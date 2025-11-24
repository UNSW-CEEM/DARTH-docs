# PV Bushfire Data

This data set ranges from 2017-11 to 2020-09 in 30-minute sampling rate. The data set includes 710 residential sites across Australia. 

## Database Stricture & Data 

Two tables were created for this dataset: 

1. *pv_bushfire_site_details:* contains the site details similar to the csv file, hence the following columns: 

    - site_id (big integer) 

    - postcode (character (4)) 

    - state (character varying (3)) 

    - timezone_id (character varying) 

2. *pv_bushfire_data:* contains all the PV energy data from all sites and times. The original data was in UTC; we localized timestamps using the time zone of each site and added a new column, datetime, to store the local time. It is referred to when accessing and filtering data via the webserver. The table has the following columns: 

    - utc_timestamp (timestamp with time zone) 

    - datetime (timestamp without time zone) 

    - site_id (big integer) 

    - monitoring_data_type (character varying) 

    - value (real) 

The volume of this dataset is 2.7 GB (one month energy around 100 MB). 

## Appendix A: Original Dataset 

This data set ranges from 2017-11 to 2020-09 in 30-minute sampling rate.  

The data set includes 710 residential sites across Australia from the Solar Analytics data set. 

Each month's data was provided in a separate csv file. There were 35 data files in total. In the data csv files, each column represents: 

- utc_timestamp: the time stamp in UTC 

- site_id: the ID of this site 

- monitoring_data_type: the data type of this monitoring 

- values: the PV energy produced during the 30 minutes in w- att-hour 

There was a site_details csv file as well, each row representing the details of one site as follows: 

- site_id: the ID of this site 

- postcode: the postcode of this site 

- state: the state of this site 

- timezone_id: the local time zone of this site. This information will be useful when converting the UTC time stamp to local time stamp. 