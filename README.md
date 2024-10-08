# SPOTIFY ETL PIPELINE PROJECT
## OVERVIEW OF PROJECT
### This project builds an ETL (Extract, Transform, Load) pipeline to extract Spotify data using Python, transform it with AWS Lambda, and load it onto AWS Athena for analysis.

## ARCHITECTURE
### 1. Extraction:
    - Python script using Spotify API to extract data 
    - Data stored in AWS S3 bucket
### 2. Transformation:
    - AWS Lambda function to transform extracted data (e.g., data cleaning, formatting)
    - Lambda function triggered by S3 bucket updates
### 3. Loading:
    - Transformed data loaded into AWS Athena for querying and analysis

## Components

### 1. Extraction (Python Script)

- (spotify_etl.ipynb): Python script using Spotify API to extract data
- Requirements:
    - spotipy library
    - Spotify API credentials (Client ID, Client Secret)
- Output: JSON files stored in S3 bucket (s3://spotify-etl-new/)

### 2. Transformation (AWS Lambda)

- (arn:aws:lambda:ap-south-1:654654433023:function:spotify_etl_extract): Lambda function to transform extracted data
- Requirements:
   ### - boto3 library
   ### - AWS credentials (Access Key ID, Secret Access Key)
- Input: JSON files from S3 bucket (s3://spotify-data-extraction/)
- Output: Transformed JSON files stored in S3 bucket (s3://spotify-etl-new/raw_data/processed/)

### 3. Loading (AWS Athena)

- spotify_athena_table.sql: SQL script to create Athena table
- Requirements:
    - AWS Athena configured with S3 bucket (s3://spotify-etl-new/transform-data/)
- Output: Queryable table in Athena (spotify_db)
