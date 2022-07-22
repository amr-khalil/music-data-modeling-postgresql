# Project: Music Data Modeling with PostgreSQL

ETL pipeline for music data using Python and PostgreSQL.


## Introduction
A startup called **Sparkify** wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a **Postgres database** with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and **ETL pipeline** by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.


## Song Dataset
The first dataset is a subset of real data from the [Million Song Dataset](http://millionsongdataset.com/). Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are file paths to two files in this dataset.

```
song_data/A/B/C/TRABCEI128F424C983.json
song_data/A/A/B/TRAABJL12903CDCF1A.json
```

## Log Dataset
The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate activity logs from a music streaming app based on specified configurations.

The log files in the dataset you'll be working with are partitioned by year and month. For example, here are filepaths to two files in this dataset.

```
log_data/2018/11/2018-11-12-events.json
log_data/2018/11/2018-11-13-events.json
```

## Schema for Song Play Analysis
Using the song and log datasets, you'll need to create a star schema optimized for queries on song play analysis. This includes the following tables.

### Fact Table
#### songplays
Description: records in log data associated with song plays i.e. records with page NextSong.
- `songplay_id`
- `start_time`
- `user_id`
- `level`
- `song_id`
- `artist_id`
- `session_id`
- `location`
- `user_agent`
 
### Dimension Tables
#### users
Description: users in the app.
- `user_id`
- `first_name`
- `last_name`
- `gender`
- `level`

#### songs
Description: songs in music database.
- `song_id`
- `title`
- `artist_id`
- `year`
- `duration`

#### artists
Description: artists in music database.
- `artist_id`
- `name`
- `location`
- `latitude`
- `longitude`

#### time 
Description: timestamps of records in songplays broken down into specific units.
- `start_time`
- `hour`
- `day`
- `week`
- `month`
- `year`
- `weekday`

## Project Structure
The project includes six files:

- **test.ipynb**:  displays the first few rows of each table to let you check your database.
- **create_tables.py**: drops and creates your tables. You run this file to reset your tables before each time you run your ETL scripts.
- **etl.ipynb**: reads and processes a single file from song_data and log_data and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.
- **etl.py**: reads and processes files from song_data and log_data and loads them into your tables. You can fill this out based on your work in the ETL notebook.
- **sql_queries.py**: contains all your sql queries, and is imported into the last three files above.

## Project Steps
**NOTE**: You will not be able to run test.ipynb, etl.ipynb, or etl.py until you have run create_tables.py at least once to create the sparkifydb database, which these other files connect to.

- Create Tables: `python create_tables.py`
- Build ETL Pipeline: `python etl.py`
- Run Sanity Tests: open and run test.ipynb using jupyter notebook
