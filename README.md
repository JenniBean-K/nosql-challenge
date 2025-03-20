
Module 12 Challenge

# UK Food Hygiene Rating Analysis

## Project Overview

The UK Food Standards Agency evaluates establishments across the Uniter Kingdom and assigns them hygiene ratings to ensure public safety. As part of this project, commissioned by the food magazine Eat, Safe, Love, the analysis aims to assist journalists and food critics in identifying noteworthy establishments for future articels. This includes setting up the database, modifying the dataset, and conducting exploratory analysis.

## Objectives

### 1. Database Setup
* Import and configure data in MongoDB.
* Verify the database setup with PyMongo and Pretty Print (pprint).
* Assign the establishments collection for further analysis.

### 2. Database Updates 
* Add a new establishments collection for further analysis.
* Delete specific records.
* Correct data inconsistencies by updating field types.

### 3. Data Analysis
* Identify establishments with specific hygiene scores.
* Focus on well_rated establishments in London.
* Locate top establishments near a specific location.
* Aggregate data for Local Authorities with poor hygiene.

## File Structure

### 1. NoSQL_setup_starter.ipynb
* Sets up the MongoDB database and verifies the data.
* Imports the required libraries (PyMongo, pprint).
* Confirms the presence of uk_foods and establishments collections.
* Prepares the database for use.

### NoSQL_analysis_starter.ipynb
* Conducts queries to answer Eat Safe, Love's specific questios.
* Utilizes Pandas for data presentaion.

## Instructions

### Part 1: Database and Jupyter Notebook Setup
* Import the data using:
```
mongoimport --db uk_food --collection establishments --file /Users/jennikim/Repos/nosql-challenge/Resources/establishments.json --jsonArray
```
* Verify database setup:
    
    * Use `list_database_names` to ensure `uk_foods` is created.
    * List collections to confirm `establishments`.
    * Validate data with `find_one` and display it using `pprint`.

### Part 2: Update the Database
1. Insert new establishment:
```
{
    "BusinessName": "Penang Flavours",
    "BusinessType": "Restaurant/Cafe/Canteen",
    "AddressLine1": "Penang Flavours",
    "PostCode": "SE18 7DY",
    "LocalAuthorityName": "Greenwich",
    "scores": {"Hygiene": "", "Structural": "", "ConfidenceInManagement": ""},
    "geocode": {"longitude": "0.08384000", "latitude": "51.49014200"},
    "NewRatingPending": true
}
```
2. Update `BusinessTypeID` for `"PenangFlavours"` using query.
3. Remove all establishments under `"Dover Local Authority"` and confirm with `count_documents`.
4. Convert:
    * `goecode.longitude` and `geocode.latitude` to decimals.
    * `RatingVlaue` to integers.

### Part 3: Exploratory Analysis
1. Hygiene Score = 20
    * Query for establishments with hygiene score of 20.
    * Display results in Pandas DataFrame.
2. London establishments with RatingValue >= 4 
    * Use `$regex` to find London-based establishments.
    * Filter for `RatingValue >= 4.
3. Top 5 Near "Penang Flavours"
    * Search for eastablishments with `RatingValue = 5` within 0.01 degrees of "Penang Flavours". 
    * Sort by lowest hygiene score and limit results to 5.
4. Hygiene Score = 0 (Top Authorities)
    * Aggregrate and count establishments with hygiene score of 0 for each Local Authority.
    * Sort by count decending order and display the top 10.

## Results
1. Hygiene Score 20: Identified 41 establishments.
2. Top-Rated in London: Found 33 establishments meeting criteria.
3. Top 5 Near Penang Flavours: Establishments sorted by display.
4. Local Authorities with Hygiene Score 0: Leading authorities include Thanet, Greenwich, and others.

## Requirements:

* Python Laibraies: PyMongo, pprint, Pandas.
* Tools: Jupyter Notebook, MongoDB.
    