# BOM (Bureau of Meteorology)

This dataset consists of half-hourly weather data from the Australian Bureau of Meteorology. It starts from 1985 and continues to the present and includes around 630 weather stations nation-wide. 

## Database Structure & Data 

This dataset has two tables in the database: 

| Database Table | Columns |
|--------------|---------------------------------------------------------|
| *bom_station_details* | date_data_supplied, record_identifier, station_number, rainfall_district_code, station_name, month_year_station_opened, month_year_station_closed, latitude, longitude, method_by_which_latitude_longitude_was_derived, state, height_of_station_above_mean_sea_level_metres, height_of_barometer_above_mean_sea_level_metres, wmo_index_number, first_year_of_data_supplied, last_year_of_data_supplied, percentage_complete_between_first_and_last_records, percentage_of_values_with_quality_flag_y,  percentage_of_values_with_quality_flag_n, percentage_of_values_with_quality_flag_w, percentage_of_values_with_quality_flag_s, percentage_of_values_with_quality_flag_i, end_of_record_indicator |
| *bom_data* | hm, station_number, state, year, month, day, hour_local_std, min_local_std, datetime, precipitation_since_9am_local_time_in_mm, quality_of_precipitation_since_9am_local_time, air_temperature_in_degrees_c, quality_of_air_temperature, wet_bulb_temperature_in_degrees_c, quality_of_wet_bulb_temperature, dew_point_temperature_in_degrees_c, quality_of_dew_point_temperature, relative_humidity_in_percentage, quality_of_relative_humidity, vapour_pressure_in_hpa, quality_of_vapour_pressure, saturated_vapour_pressure_in_hpa, quality_of_saturated_vapour_pressure, wind_speed_in_km_h, wind_speed_quality, wind_direction_in_degrees_true, wind_direction_quality,  speed_of_maximum_windgust_in_last_10_minutes_in_km_h, quality_of_speed_of_maximum_windgust_in_last_10_minutes, cloud_amount_of_first_group_in_eighths, quality_of_first_group_of_cloud_amount, cloud_type_of_first_group_in_code, quality_of_first_group_of_cloud_type, cloud_height_of_first_group_in_feet, quality_of_first_group_of_cloud_height, cloud_amountof_second_group_in_eighths, quality_of_second_group_of_cloud_amount, cloud_type_of_second_group_in_code, quality_of_second_group_of_cloud_type, cloud_height_of_second_group_in_feet, quality_of_second_group_of_cloud_height, cloud_amount_of_third_group_in_eighths, quality_of_third_group_of_cloud_amount, cloud_type_of_third_group_in_code, quality_of_third_group_of_cloud_type, cloud_height_of_third_group_in_feet, quality_of_third_group_of_cloud_height, cloud_amount_of_fourth_group_in_eighths, quality_of_fourth_group_of_cloud_amount, cloud_type_of_fourth_group_in_code, quality_of_fourth_group_of_cloud_type, cloud_height_of_fourth_group_in_feet, quality_of_fourth_group_of_cloud_height, ceilometer_cloud_amount_of_first_group, quality_of_first_group_of_ceilometer_cloud_amount, ceilometer_cloud_height_of_first_group_in_feet, quality_of_first_group_of_ceilometer_cloud_height, ceilometer_cloud_amount_of_second_group, quality_of_second_group_of_ceilometer_cloud_amount, ceilometer_cloud_height_of_second_group_in_feet, quality_of_second_group_of_ceilometer_cloud_height, ceilometer_cloud_amount_of_third_group, quality_of_third_group_of_ceilometer_cloud_amount, ceilometer_cloud_height_of_third_group_in_feet, quality_of_third_group_of_ceilometer_cloud_height, ceilometer_sky_clear_flag, mean_sea_level_pressure_in_hpa, quality_of_mean_sea_level_pressure, station_level_pressure_in_hpa, quality_of_station_level_pressure, aws_flag, end_of_record_indicator |

The station details are usually the same from month to month for each station, occasionally change for example a station is closed. Therefore, we keep all records of these details to have the details corresponding to the data in any specific date. However, it also means that the details are repeated in the table. 

An example of the *bom_station_details* for one month can be found here. 

Due to the high volume of the data, the *bom_data* table has been partitioned by zones (states): 

- bom_data_ant 

- bom_data_nsw 

- bom_data_nt 

- bom_data_qld 

- bom_data_sa 

- bom_data_tas 

- bom_data_vic 

- bom_data_wa 

Each of the above partitions are accessible via the web downloader by selecting the name in the *Data Type* input field. It is recommended to use the *Time From* and *Time To* filters in the web interface to limit the data download volume to the necessary amount. Currently the size of this dataset is around 35 GB, each zone around 5 GB (on average). 

## Appendix A: Original Dataset  

At the beginning of the project, we received the historical data up to May 2022 in a batch. It consisted of two metadata files (station details and station notes) for all the stations, plus one file of historical weather data for each station. Afterwards, we have been receiving monthly data updates including one monthly data file for each weather station, and two metadata files for all the stations.  

### 1. Notes 

With each data round one Notes metadata file is provided which explains the period of observation, byte location, byte size, and explanation of the fields in the data files, parameter notes, code meanings, and finally byte location, byte size, and explanation of the fields in the station details file. An example of the Notes file can be found here. 

### 2. Station Details 

With each data round one Station Details metadata file is provided as a text file. The file starts with the following explanation/disclaimer: 

    “Percentage complete between first and last records assumes 48 observation per day. 

    Some days there may be more than 48 reports if there have been significant changes in  

    the weather, so the percentage completeness is an estimate.” 

Then it has around 630 rows of details, one row for each weather station, including the following fields: 

- Record identifier - st 

- Bureau of Meteorology Station Number 

- Rainfall district code 

- Station Name 

- Month/Year station opened (MM/YYYY) 

- Month/Year station closed if applicable (MM/YYYY) 

- Latitude to 4 decimal places, in decimal degrees 

- Longitude to 4 decimal places, in decimal degrees 

- Method by which latitude/longitude was derived 

- State 

- Height of station above mean sea level in metres 

- Height of barometer above mean sea level in metres 

- WMO (World Meteorological Organisation) Index Number 

- First year of data supplied in data file 

- Last year of data supplied in data file 

- Percentage complete between first and last records 

- Percentage of values with quality flag 'Y' 

- Percentage of values with quality flag 'N' 

- Percentage of values with quality flag 'W' 

- Percentage of values with quality flag 'S' 

- Percentage of values with quality flag 'I' 

- \# symbol, end of record indicator 

### 3. Data Files 

In each round we receive a text data file for each weather station (around 630 data files). Each file has a header of the column names: 

    hm, Station Number, Year Month Day Hour Minutes in YYYY, MM, DD, HH24, MI format in Local standard time, Precipitation since 9am local time in mm, Quality of precipitation since 9am local time, Air Temperature in degrees C, Quality of air temperature, Wet bulb temperature in degrees C, Quality of Wet bulb temperature, Dew point temperature in degrees C, Quality of dew point temperature, Relative humidity in percentage %, Quality of relative humidity, Vapour pressure in hPa, Quality of vapour pressure, Saturated vapour pressure in hPa, Quality of saturated vapour pressure, Wind speed in km/h, Wind speed quality, Wind direction in degrees true, Wind direction quality, Speed of maximum windgust in last 10 minutes in  km/h, Quality of speed of maximum windgust in last 10 minutes, Cloud amount (of first group) in eighths, Quality of first group of cloud amount, Cloud type (of first group) in code, Quality of first group of cloud type, Cloud height (of first group) in feet, Quality of first group of cloud height, Cloud amount(of second group) in eighths, Quality of second group of cloud amount, Cloud type (of second group) in code, Quality of second group of cloud type, Cloud height (of second group) in feet, Quality of second group of cloud height, Cloud amount (of third group) in eighths, Quality of third group of cloud amount, Cloud type (of third group) in code, Quality of third group of cloud type, Cloud height (of third group) in feet, Quality of third group of cloud height, Cloud amount (of fourth group) in eighths, Quality of fourth group of cloud amount, Cloud type (of fourth group) in code, Quality of fourth group of cloud type, Cloud height (of fourth group) in feet, Quality of fourth group of cloud height, Ceilometer cloud amount (of first group), Quality of first group of ceilometer cloud amount, Ceilometer cloud height (of first group) in feet, Quality of first group of ceilometer cloud height, Ceilometer cloud amount (of second group), Quality of second group of ceilometer cloud amount, Ceilometer cloud height (of second group) in feet, Quality of second group of ceilometer cloud height, Ceilometer cloud amount (of third group), Quality of third group of ceilometer cloud amount, Ceilometer cloud height (of third group) in feet, Quality of third group of ceilometer cloud height, Ceilometer sky clear flag, Mean sea level pressure in hPa, Quality of mean sea level pressure, Station level pressure in hPa, Quality of station level pressure, AWS Flag, # 

And then the data for each 30-minute interval. 

## Appendix B: Data Processing 

### 1. Station Details 

We rename the fields to the following: 

- record_identifier 

- station_number 

- rainfall_district_code 

- station_name 

- month_year_station_opened 

- month_year_station_closed 

- latitude 

- longitude 

- method_by_which_latitude_longitude_was_derived 

- state 

- height_of_station_above_mean_sea_level_metres 

- height_of_barometer_above_mean_sea_level_metres 

- wmo_index_number, first_year_of_data_supplied 

- last_year_of_data_supplied 

- percentage_complete_between_first_and_last_records 

- percentage_of_values_with_quality_flag_y 

- percentage_of_values_with_quality_flag_n 

- percentage_of_values_with_quality_flag_w 

- percentage_of_values_with_quality_flag_s 

- percentage_of_values_with_quality_flag_i 

- end_of_record_indicator 

Then we add a *date_data_supplied* column with value being the last day of the month for which the data is provided. Occasionally the data needs correction, for example state is missing we find and fill it in. 

### 2. Weather Data 

We rename columns as follows: 

- "Year Month Day Hour Minutes in YYYY": "Year" 

- "MM": "Month" 

- "DD": "Day" 

- "HH24": "Hour Local STD" 

- "MI format in Local standard time": "Min Local STD" 

- "Relative humidity in percentage %": "Relative humidity in percentage" 

- "#": "end of record indicator" 

and rename all the fields by replacing each white space with an underscore. 

Then change the data types (from string to integer or float) and treat the white spaces as Null according to the data type they should be. 

Integer columns: 

- station_number 

- year 

- month 

- day 

- hour_local_std 

- min_local_std 

- relative_humidity_in_percentage 

- wind_direction_in_degrees_true 

- cloud_height_of_first_group_in_feet 

- cloud_height_of_second_group_in_feet 

- cloud_height_of_third_group_in_feet 

- cloud_height_of_fourth_group_in_feet 

- ceilometer_cloud_height_of_first_group_in_feet 

- ceilometer_cloud_height_of_second_group_in_feet 

- ceilometer_cloud_height_of_third_group_in_feet 

- ceilometer_sky_clear_flag, aws_flag 

Float columns: 

- precipitation_since_9am_local_time_in_mm 

- air_temperature_in_degrees_c 

- wet_bulb_temperature_in_degrees_c 

- dew_point_temperature_in_degrees_c 

- vapour_pressure_in_hpa 

- saturated_vapour_pressure_in_hpa 

- wind_speed_in_km_h 

- speed_of_maximum_windgust_in_last_10_minutes_in_km_h 

- mean_sea_level_pressure_in_hpa 

- station_level_pressure_in_hpa 

Then we create *datetime* from the year, month, day, hour, minute values (local time) and add it as a new column. We find the state by looking up the station number in the station details and add *state* as a new column to the data.  

 