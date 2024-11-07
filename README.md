# Layoff-Data-Cleaning-Project

Objective: The goal of this project is to clean and standardize layoff data, removing duplicates, handling null values, and formatting data for consistency.

Step 1: Data Preparation and Initial Inspection
Actions Taken:

Dropped unnecessary tables, re-created a clean staging table (Layoffs_Staging).
Inserted data from the main Layoffs table into Layoffs_Staging.
Reasoning: Creating a staging table allows for testing cleaning processes without impacting the original data.

Step 2: Identifying and Removing Duplicates
Actions Taken:

Used row_number() with a PARTITION BY clause to detect duplicate entries based on key columns (e.g., Company, Location, Industry).
Deleted rows with row_num > 1 to retain unique records.
Reasoning: Ensures that data is unique, reducing redundancy for more accurate analysis.

Step 3: Standardizing Text Fields
Actions Taken:

Trimmed whitespace in key columns like Company and Country.
Used LIKE and UPDATE statements to unify variations of industries (e.g., changing Crypto% entries to Crypto).
Reasoning: Consistent text data avoids mismatches during analysis, especially when aggregating or filtering data.

Step 4: Formatting Dates
Actions Taken:

Standardized the date column format from mm/dd/yyyy to SQL date format using STR_TO_DATE.
Altered the column to store dates as DATE instead of TEXT.
Reasoning: Date standardization allows for chronological sorting and precise date-based filtering.

Step 5: Handling Null Values and Missing Data
Actions Taken:

Set fields with unpopulated industry information to NULL.
Used JOIN statements to update missing industry data where possible based on other table rows.
Deleted rows where both Total_Laid_off and Percentage_laid_off were NULL, indicating incomplete records.
Reasoning: Ensuring the absence of empty rows or columns enhances data integrity and prevents skewed results during analysis.

Final Data Set and Verification
After completing each step, run final SELECT statements to verify that all cleaning steps have been applied correctly. The cleaned data in Layoffs_Staging2 is now ready for analysis.

Key Takeaways
This project demonstrates proficiency in:

SQL-based data cleaning techniques.
Handling duplicates, null values, and inconsistent data.
Preparing data for analysis by ensuring its accuracy and uniformity.
This structured approach to data cleaning, coupled with SQL techniques, showcases the ability to transform raw data into a reliable and analysis-ready dataset.
