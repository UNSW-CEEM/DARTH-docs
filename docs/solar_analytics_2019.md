# Solar Analytics Solar Data 2019 Dataset
## Database Structure & Data 

This dataset has 5-minute energy data of 1000 sites for 1 year (2019). 

For this dataset two tables were created in the DARTH database: 

1. *solar_analytics_site_details* with the following columns: 

    - site_id (bigint) 

    - postcode (character 4) 

    - state (character varying 3) 

    - timezone_id (text) 


    The primary key is site_id. This table currently has 1000 records (40 KB). 


2. *solar_analytics_voltage_data* with these columns: 

    - datetime (timestamp with time zone) 

    - site_id (bigint) 

    - energy_wh (double precision) 

    - voltage_max_v (double precision) 

    - voltage_min_v (double precision) 

This table currently has 105,406,509 records. The volume is 6 GB (each month’s solar data around 500 MB). 

  

## Appendix A: Original Dataset 

The dataset included 12 csv files (2019-01 to 2019-12) and a site_details file. 

The site_details file included 1000 rows of site_id, postcode, state, and timezone_id. No missing data. 

Each csv file included around 9,000,000 rows of data with the following columns: t_stamp_utc, site_id, energy_(Wh), voltage_max_(V), voltage_min_(V). There was a small portion of records with missing data (Null values) for energy_(Wh), voltage_max_(V), or voltage_min_(V). No missing data for site_id. 

In total 1000 unique site_id values exist in site_details file and also 1000 unique site_id values exist in each csv file; however, some of the site_id values that have associated voltage data did not exist in the site_details file. That is, we have some voltage data for some (according to site_details file) unknown sites. The number of these unknown sites for each data file are 153 (for 10 csv files/months) and 164 (for 2 csv files/months). Additionally, some of the sites do not have any associated voltage data. 