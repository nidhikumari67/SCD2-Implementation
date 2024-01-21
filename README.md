# SCD2-Implementation

## Overview
This Python-based project illustrates the implementation of Slowly Changing Dimension 2 (SCD2) using Pandas and SQLAlchemy, specifically designed for maintaining historical changes in a product dimension table within a Microsoft SQL Server database. SCD2 is employed to track changes over time, allowing historical versions of records to be preserved.

### Key Components
* Data Extraction: Utilizes Pandas to read data from a CSV file ('products.txt') and SQLAlchemy to query an existing SQL Server table ('product_dim'). The SQL query 
  retrieves the current active records with an 'end_date' set to '9999-12-31'.

* Data Transformation: Merges the extracted product data with the current database records based on the 'product_id'. The result is a DataFrame containing keys of records 
  that need to be updated in the SCD2 process.

* Insert Operation: Adds new records to the 'product_dim' table with a 'start_date' set to the current date and 'end_date' set to '9999-12-31'.

* Update Operation: Executes SQL update statements to set the 'end_date' of the existing records identified in the transformation step to yesterday's date, effectively
  ending their validity.

#### Usage
* Extract Data: Run the extract() function to read data from the CSV file and SQL database using Pandas and SQLAlchemy.

* Transform Data: Execute the transform() function to identify records that need to be updated in the SCD2 process.

* Insert New Records: Apply new records to the 'product_dim' table using the inserts() function with Pandas and SQLAlchemy.

* Update Existing Records: Run the updates() function to update the 'end_date' of existing records identified in the transformation step using SQLAlchemy.

