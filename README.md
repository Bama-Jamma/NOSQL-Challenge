# NOSQL-Challenge

# Eat Safe, Love

This repository contains code for importing, updating, and analyzing data related to food establishments in the UK. The data is stored in a MongoDB database named `uk_food` with the collection `establishments`.

## Table of Contents
- [Part 1: Database and Jupyter Notebook Set Up](#part-1-database-and-jupyter-notebook-set-up)
- [Part 2: Update the Database](#part-2-update-the-database)
- [Part 3: Exploratory Analysis](#part-3-exploratory-analysis)

## Part 1: Database and Jupyter Notebook Set Up

To set up the database and Jupyter Notebook for the project, follow the instructions below:

### Importing the Data

Import the data provided in the `establishments.json` file into the MongoDB database named `uk_food` and the collection named `establishments`. The exact command used for the import can be found in the code.

### Database and Collection Set Up

Connect to the MongoDB database using the `pymongo` library. Create an instance of `MongoClient` and assign it to the `mongo` variable. Confirm the creation of the new database and review the collections within it. The code snippet provided in the code can be executed to achieve this.

### Reviewing a Document

Use the `pprint` function to review a document within the `establishments` collection. This allows you to verify the imported data and get a sense of its structure.

### Assigning the Collection

Assign the `establishments` collection to a variable named `establishments`. This allows you to perform various operations on the collection in the subsequent parts of the code.

## Part 2: Update the Database

This part focuses on updating the database with new data and modifying existing records. Follow the instructions provided below:

### Adding a New Restaurant

To add a new restaurant named "Penang Flavours" to the database, create a dictionary `penang_flavors` with the restaurant's information. Use the `insert_one` method on the `establishments` collection to insert the new restaurant. Verify that the restaurant was inserted by using the `find_one` method.

### Finding BusinessTypeID

To find the BusinessTypeID for "Restaurant/Cafe/Canteen", use the `find_one` method on the `establishments` collection with the query `{"BusinessType": "Restaurant/Cafe/Canteen"}`. Return only the `BusinessTypeID` and `BusinessType` fields by specifying them in the fields dictionary. This query helps you retrieve the necessary information.

### Updating the New Restaurant

Update the new restaurant "Penang Flavours" with the correct `BusinessTypeID` obtained from the previous step. Use the `update_one` method on the `establishments` collection with the filter `{"BusinessName": "Penang Flavours"}` and the update operation `{"$set": {"BusinessTypeID": business_query["BusinessTypeID"]}}`. Confirm that the update was successful by using the `find_one` method again.

### Removing Establishments in Dover

Check the number of documents that contain the Dover Local Authority by using the `count_documents` method with the query `{"LocalAuthorityName": "Dover"}`. Delete all establishments with the Dover Local Authority by using the `delete_many` method with the query `{"LocalAuthorityName": "Dover"}`. Verify that the documents were deleted by checking the count again and using the `find_one` method to see if any remaining documents include Dover.

### Updating Data Types

Convert the latitude and longitude fields from strings to decimal numbers by using the `update_many` method with the `$toDouble` operator. Similarly, convert the RatingValue field from a string to an integer using the `$toInt` operator. Verify that the changes were applied by using the `find_one` method.

## Part 3: Exploratory Analysis

This part focuses on performing exploratory analysis on the data. Several questions are answered, and the results are displayed as follows:

### Establishments with Hygiene Score of 20

Find establishments with a hygiene score of 20 using the `find` method with the query `{"scores.Hygiene": 20}`. Use the `count_documents` method to display the number of documents in the result. Print the first document using `pprint`. Convert the result to a Pandas DataFrame, print the number of rows, and display the first 10 rows.

### Establishments in London with RatingValue >= 4

Find establishments in London with a RatingValue greater than or equal to 4. Use the `find` method with the query `{"LocalAuthorityName": {"$regex": "London"}, "RatingValue": {"$gte": 4}}`. Use the `count_documents` method to display the number of documents in the result. Print the first document using `pprint`. Convert the result to a Pandas DataFrame, print the number of rows, and display the first 10 rows.

### Top 5 Establishments with RatingValue = 5

Find the top 5 establishments with a RatingValue of 5, sorted by the lowest hygiene score and nearest to the new restaurant "Penang Flavours". Use the `find` method with the appropriate query and sorting criteria. Iterate over the results and print each establishment using `pprint`. Convert the result to a Pandas DataFrame and display the top 5 rows.

### Establishments with Hygiene Score of 0 by Local Authority

Create a pipeline to find the number of establishments with a hygiene score of 0 for each Local Authority. Use the `$match`, `$group`, and `$sort` pipeline stages to perform the aggregation. Print the number of documents in the result and the first 10 results. Convert the result to a Pandas DataFrame and display the first 10 rows.

## Dependencies

The code provided requires the following dependencies:

- `pymongo`: A Python library for interacting with MongoDB.
- `pprint`: A module for pretty-printing data structures.
- `pandas`: A data manipulation and analysis library.

Ensure these dependencies are installed using the appropriate package manager before running the code.

## Usage

1. Import the necessary modules and libraries.
2. Set up the database and connect to it.
3. Execute the code snippets provided in the respective parts.
4. Customize the code as needed for your specific requirements.