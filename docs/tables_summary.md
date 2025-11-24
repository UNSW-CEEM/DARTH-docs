# Summary of Data Tables Accessible from the Web Downloader

## Datasets Accessible via the SPREE Web Downloader

The following datasets are accessible via the SPREE web downloader. Please note that the volumes are as of September 2025; the data upload to the BOM and EDP datasets and photovoltaics and weather tables is continuous, so the dataset volumes constantly increase.

---

## photovoltaics

| Tables (Data Type in Web Interface) | Data | Data Source | Filters in Web Interface | Volume |
|------------------------------------|------|-------------|------------------------|--------|
| photovoltaics, metadatapv | 5-min PV data from 2018 to present | UNSW buildings: PV-TETB, PV-MB, PV-UNIGYM, PV-TETB-ISLAND | From Time Stamp, To Time Stamp, Building, Serial Number | 1 GB |

---

## weather

| Tables (Data Type in Web Interface) | Data | Data Source | Filters in Web Interface | Volume |
|------------------------------------|------|-------------|------------------------|--------|
| weather, metadataunitsweather | Hourly weather data from 2020 to present | UNSW buildings: TETB, Room401, TETB_SDEC | From Time Stamp, To Time Stamp, Building | 1.8 GB |

---

## Ausgrid 300 Homes Solar Data

| Tables (Data Type in Web Interface) | Data | Data Source | Filters in Web Interface | Volume |
|------------------------------------|------|-------------|------------------------|--------|
| ausgrid_solar_homes_customers, ausgrid_solar_homes_electricity | 30-min solar generation data 2010-2013 | 300 sites | From Time Stamp, To Time Stamp | 800 MB |

---

## Solar Analytics Solar Data

| Tables (Data Type in Web Interface) | Data | Data Source | Filters in Web Interface | Volume |
|------------------------------------|------|-------------|------------------------|--------|
| solar_analytics_voltage_data, solar_analytics_site_details | 5-min solar data (energy, voltage) from 2019-01 to 2019-12 | 1000 sites | From Time Stamp, To Time Stamp | 6 GB (site details 40 KB, one month’s solar data ~500 MB) |

---

## Victorian Consumers Data

| Tables (Data Type in Web Interface) | Data | Data Source | Filters in Web Interface | Volume |
|------------------------------------|------|-------------|------------------------|--------|
| victorian_consumers_site_details, victorian_consumers_electricity_data, victorian_consumers_subload_data | 30-min consumption, generation, voltage data; 30-min subload data from 2016-12 to 2022-05 | 1146 sites | From Time Stamp, To Time Stamp | 4 GB (electricity 2 GB, subload 2 GB) |

---

## PV Bushfire Data

| Tables (Data Type in Web Interface) | Data | Data Source | Filters in Web Interface | Volume |
|------------------------------------|------|-------------|------------------------|--------|
| pv_bushfire_data | 30-min PV energy data from 2017-11 to 2020-09 | 710 residential sites | From Time Stamp, To Time Stamp | 2.7 GB (one month ~100 MB) |

---

## BOM (Australian Bureau of Meteorology)

| Tables (Data Type in Web Interface) | Data | Data Source | Filters in Web Interface | Volume |
|------------------------------------|------|-------------|------------------------|--------|
| bom_data_nsw, bom_data_qld, … | 30-min weather data from 1985 to present | 718 stations | From Time Stamp, To Time Stamp | 35 GB (one zone ~5 GB on average) |

---

## EDP (Energy Data Platform)

| Tables (Data Type in Web Interface) | Data | Data Source | Filters in Web Interface | Volume |
|------------------------------------|------|-------------|------------------------|--------|
| edp_data (partitioned by year/month), edp_survey_answers, edp_sites_metadata | 5-min energy data from 2018 to present | ~1000 sites | From Time Stamp, To Time Stamp | 124 GB (one month ~1.5 GB) |
