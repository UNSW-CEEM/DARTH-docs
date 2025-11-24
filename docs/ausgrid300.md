# Ausgrid 300 Homes Solar Data

This dataset consists of half-hourly solar generation data of 300 customers for 3 years (2010-2011, 2011-2012, 2012-2013). Two tables were created for this dataset: 

1. *ausgrid_solar_homes_customers:*
    
    <u>columns:</u>

    - customer_id (integer; Not Null) 

    - postcode (character 4; Not Null) 

    - generator_capacity (double precision; Not Null) 

    <u>Primary Key:</u>

    1. *ausgrid_solar_homes_elecrticity*

    <u>columns:</u>

    - customer_id (integer; Not Null) 

    - datetime (timestamp without time zone; Not Null) 

    - date (date; Not Null) 

    - time (character varying 5; Not Null) 

    - gross_generation (real) 

    - general_consumption (real) 

    - controlled_load (real) 

        <u>Primary key:</u> combination of customer_id and datetime 

        <u>Foreign key:</u> customer_id referencing ausgrid_solar_homes_customers.customer_id

        The timestamp column of the processed dataset was renamed to datetime in the database table to activate the time filters of the webdownloader on this dataset. 

The total volume of this dataset is around 800 MB. 

# Appendix A: Original Dataset 

The original dataset consisted of three csv files, each containing half-hourly solar generation data of 300 customers for one year (2010-2011, 2011-2012, 2012-2013). Each data row included customer id, generator capacity, postcode, consumption category, date, and 48 values. The csv files for the second and third year also included a column named Row Quality, but there were no data in it. The consumption category column could include three values: “CL” for controlled load, “GC” for general consumption, and “GG” for gross generation. Thus, in a complete dataset there would have been three data rows for each customer/date combination. However, in many cases there was no data for controlled load, that is only two rows existed for a specific customer/date combination. Therefore, each file had around 270,000 rows and 53 or 54 columns. Please refer to the [Ausgrid solar home electricity data notes (Aug 2014).pdf](https://unsw.sharepoint.com/sites/DARTHUsers/Shared%20Documents/Forms/AllItems.aspx?id=%2Fsites%2FDARTHUsers%2FShared%20Documents%2FGeneral%2FAusgrid%20solar%20home%20electricity%20data%20notes%20%28Aug%202014%29%2Epdf&parent=%2Fsites%2FDARTHUsers%2FShared%20Documents%2FGeneral) for more details about the original dataset. 