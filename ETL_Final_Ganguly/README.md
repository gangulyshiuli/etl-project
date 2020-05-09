# ETL Process

The COVID-19 pandemic has changed how people around the world live their daily lives. One major area of change is education. In this project we were interested in learning more about the content of online learning platforms. We gathered data from one of the most popular MOOCs (Massive Open Online Courses), edX. We also used data from YouTube use from 10 countries/regions. Finally, we used a dataset containing information about filmed Ted Talks. These three sources of online content provide people across the world with a way to connect to many types of instructional and entertainment content.

## Step 1 - Extract

#### Data Sources: 
* Harvard and MIT courses offered by EdX (one .csv from Kaggle): https://www.kaggle.com/edx/course-study
* List of MOOCs: https://en.wikipedia.org/wiki/List_of_MOOC_providers
* Attributes of Common MOOCs: https://en.wikipedia.org/wiki/Massive_open_online_course
* YouTube Video Statistics for 10 Countries (.csv from Kaggle): https://www.kaggle.com/datasnaek/youtube-new
* YouTube Video Category IDs for 10 Countries (.json from Kaggle): https://www.kaggle.com/datasnaek/youtube-new
* Ted Talks: TED Talks- Complete List Data.World https://data.world/owentemple/ted-talks-complete-list

1. Read the .csv files with Pandas read_csv()
2. Read the .json files with Pandas read_json()
3. Extract the Wikipedia tables using Pandas read_html()

## Step 2 - Transform

#### Use the data to create the following tables:
* EdX Courses Offered (FKs: MOOC)
    -List of edX courses
    -Selected columns with information of interest, renamed columns in a concise manner with spaces omitted
* List of MOOCs (FK: MOOC)
    -List of common MOOCs with basic information about each, extracted from Wikipedia
    -Selected columns with information of interest, renamed columns in a concise manner with spaces omitted, removed Wikipedia's citation labels
* MOOC Attributes (FK: MOOC)
    -Attributes of common MOOCs, extracted from Wikipedia
    -Selected columns with information of interest, renamed columns in a concise manner with spaces omitted
* YouTube Video Categories (PK & FK: CategoryID)
    -Created unique list of categories and category codes from YouTube Video Category IDs dataset
    -Loaded into new dataframe
* YouTube Countries (PK & FK: CountryCode)
    -Created unique list of countries and country codes from YouTube Video Category IDs dataset
    -Loaded into new dataframe
* YouTube Video Data (FKs: CategoryID, CountryCode, & searchword)
    -Cleaned date columns from YouTube Video Statistics dataset
    -Loaded into new dataframe
* Master Searchwords Table (PK & FK: searchword)
    -Created unique list of categories (Youtube Video Category IDs dataset) and tags (TEDtalk dataset)
    -Loaded into new dataframe
* Ted Talk Data (FKs: Searchwords)

## Step 3 - Load

1. Create database structure: quickdatabasediagrams.com
2. Create the "online_ed" using PostgreSQL
3. Use the table structures extracted from quickdatabasediagrams.com to define the structure of the database

![DBD](Final/Images/ETL_DBD.png)
