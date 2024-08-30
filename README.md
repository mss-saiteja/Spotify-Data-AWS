# Spotify-End-To-End-Data-Engineering-Project-Using-AWS

Project Architecture:

Staging Layer:
Data is initially stored in a staging layer.

ETL Pipeline (AWS Glue):

AWS Glue is used to build an ETL pipeline that extracts data from the staging layer, transforms it, and loads it into a data warehouse.

Data Warehouse:

Data is stored in the data warehouse after processing.

AWS Glue Crawler:

A Glue Crawler is used to create a database and populate tables in the data warehouse.

Data Querying (AWS Athena):

AWS Athena is used to query data from the tables.

Dataset Description: Spotify 2023 Dataset

Files:
Albums: Contains details of albums, tracks, artists, and release dates.
Artists: Includes artist names, number of followers, and genres.
Spotify Data: Contains album ID, name, and popularity.
Spotify Features: Includes features like danceability, energy, loudness, mode, and more.
Tracks: Contains track ID, popularity, and explicitness.

Step-by-step-process:
1) A new IAM user is created for project-specific tasks.This user is given a custom username, password, and is required to change the password upon first login.
2) The newly created IAM user is used to log in, confirming that the permissions are set correctly. The user is able to access services like S3 but is denied access to services not included in the assigned permissions, such as CloudWatch.
3) Set up S3 buckets to store and organize data for the project, specifically creating a staging area and a data warehouse.
4) Create a data pipeline using AWS Glue to transfer and transform data from the staging layer to the data warehouse.
5) Setting Up the ETL Pipeline:
Data Source: The data in the staging layer, which originates from various transactional databases or has been manually uploaded, serves as the input.
Visual ETL Creation: AWS Glue provides a visual interface for creating the ETL pipeline, allowing users to drag and drop components like source and destination buckets

6) Configuring Data Sources:

Three source datasets (tracks, albums, artists) are connected from the S3 staging layer.
The correct file paths and formats (CSV) are provided for these sources.

Data Transformation:

Join Operations:
The albums and artists datasets are joined using artist ID.
The result is further joined with the tracks dataset using track ID.
Dropping Unnecessary Columns: Columns that are redundant or not needed (e.g., duplicate ID fields) are removed.

Setting the Destination:

The transformed data is then saved in the S3 data warehouse folder.
The output format is set to Parquet, and Snappy compression is used for faster queries and efficient storage.

Review and Execution:

The generated ETL script is reviewed, showing the steps performed (fetching data, joining, dropping fields, and saving to the destination).



