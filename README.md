# Technical Assessment
## `Data Analyst`
## Overview

We are currently developing tools based on AI models to assess the cognitive impact of videos and images. Our main product is offered through a dashboard where users can upload their assets and analyze memorability and saliency metrics. This simple technical assessment is meant to measure your data analytical abilities.

### Delivery
Once you have cloned this repository, close it and create a new one from your own Github user. This will ensure that your deliverable will not be visible to other candidates. Failing to close the repository and/or overwriting any content in the `master` branch of this repository will result in immediate disqualification.

Once the task is completed, please ensure to add the following users as collaborators:
- [JHevia23](https://github.com/JHevia23)
- [ppfreitas](https://github.com/ppfreitas)
    
 and notify by email to your recruiting contact.

### The Problem
We need to analyze all the data we have from our client's assets to extract meaningful conclusions. We are looking for an awesome Data Analyst capable of implementing analytics solutions, such as data analysis and visualization tools to understand our client's data, extract it from SQL tables and leverage it to generate marketing insights. 

### The Task
Using the resources attached to the email, we want to test your ability to analyze a specific data set and answer the following items: 
- Average Social Media score (smScore) by the publishing year? 
- What are the most present colors in assets by publishing year? 
- What are the most present colors in assets by asset type?

### Requirements 
You are allowed to work either with a `.csv` or with a single local database.  

### Resources
To successfully accomplish this task, you'll need to use the following files under the `data/` durectory. You find a SQLite database (`mock_db.db`) with all the tables loaded. Alternatively you can use the .csv in case you are better used to it.
- asset.csv 
- asset_type.csv
- asset_color.csv
- asset_assets_types.csv

(You are receiving one csv for each table)
*We will have special consideration for those candidates who use the db file to complete the task.*

In the `Index` section you'll find a data dictionary with a description of the main tables and their attributes. 

**`GOOD LUCK!`**

## Index
Description of main tables and attributes
**Table:** asset
**Description:** Main info about the assets (videos and images) in our database
**Attributes:**
- *id*: unique identifier of that asset (this field can be matched with assetId present in other tables)
- *name*: filename
- *campaignId*: marketing campaign identifier for that asset
- *sectorId*: economic activity sector id for that asset
- *brandId*: brand identifier for that asset
- *publishedAt*: when the asset was published
- *smScore*: social media memorability score for the asset


**Table:** asset_color
**Description:** States what colors are present in an asset
**Attributes:**
- *assetId*: asset identifier
- *color*: a color name present in the asset
- *coverage*: percentage of the pixels in an asset that are of that color


**Table:** asset_type
**Description:** Information about asset types
**Attributes:**
- *id*: unique identifier of an asset type (this field can be matched with assetTypeId present in other tables)
- *name*: its name


**Table:** asset_asset_types
**Description:** Links one asset with one asset type
**Attributes:**
- *assetId*: asset identifier
- *assetTypeId*: the corresponding asset type identifier for an asset

To read from the SQLite DB you can run the following snippet in Python:

```
import pandas as pd
import sqlite3 as db

conn = db.connect("data/mock_db.db")
pd.read_sql("describe asset", con=conn)
```