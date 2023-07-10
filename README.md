# Impact of Amazon Fulfillment Centers on PM2.5 Levels in Surrounding Areas

This study investigates the impact of Amazon's fulfillment centers on surrounding areas' fine particulate matter (PM2.5) levels. We used the synthetic controls with staggered adoption method and included the Rural-Urban Commuting Area Codes (RUCC) score as an auxiliary covariate. Our analysis indicates that Amazon's fulfillment centers have a positive effect on PM2.5 levels in surrounding areas, with an average estimated ATT of 0.098. The effect varies across years, with most years showing a positive effect. Furthermore, we found that the effect is concentrated in areas with a lower RUCC score. Our results have implications for policymakers and companies alike, highlighting the importance of considering the environmental impact of industrial activities in surrounding communities.


On this page, I will introduce the coding steps of this project and list all the output files.

### Step 1
Generate the latitude and longitude coordinates of the original Amazon fulfillment center address data (amazon-fulfillment-fips.csv) by using the r package # opencage # (https://opencagedata.com/)
#### Code: 
Amazon fulfillment center coordinates
#### Output:
 amazon_fulfillment_coordinates.csv

### Step 2
Build the PM2.5 data frame from the .nc files downloaded from the Atmospheric Composition Analysis Group at Washington University in St. Louis website (https://sites.wustl.edu/acag/datasets/surface-pm2-5/#V4.NA.03).
#### Code: 
Create the PM2.5 data frame from 2000 to 2018

### Step 3
To merge the Amazon fulfillment center coordinates data with our PM2.5 data, we rounded the latitude and longitude coordinates of the Amazon fulfillment centers and RUCC Score table to 3 decimals.
#### Code: 
Amazon fulfillment center rounded coordinates

County RUCC coordinates
#### Output: 
amazon_fulfillment_coordinates_rounded.csv

us_county_fips_coordinates_rounded.csv

### Step 4
Merge the Amazon FC and RUCC score table based on FIPS code into one table. 
Amazon fulfillment centers are in the areas where the RUCC score equals 1 – 4.
Subset to fulfillment centers that opened 2005-2017.
#### Code: 
Create the treatment and control group table
#### Output: 
fc_rucc_combined.csv (RUCC score equals 1 – 4)

fc_rucc_combined_full.csv (full version)

### Step 5
Combine the PM2.5 table and the RUCC-Amazon FC table.
#### Code: 
Preparation for Synthetic controls with staggered adoption
#### Output: 
fc_rucc_pm25_merge.csv

fc_rucc_pm25_left.csv (left-join version)

### Step 6
Using Synthetic controls with staggered adoption (r package # augsynth #) to estimate the impact of Amazon Fulfillment Centers on PM2.5 Levels in Surrounding Areas
#### Code: 
Synthetic controls with staggered adoption
#### Output: 
Synthetic-controls-with-staggered-adoption.docx
