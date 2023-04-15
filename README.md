![](food.png)

# Food Delivery App Data Analysis
Author: Volha Puzikava
***

## Overview
In this project, I worked on a real-world dataset of zomato, one of the most used food ordering platforms. This project aimed on cleaning the dataset, analyzing the given dataset, and mining informational quality insights. This project also involved visualizing the data to better understand the restaurant’s performance.

This project helped to understand how a real-world database is analyzed using SQL, how to get maximum available insights from the dataset, how to pre-process the data using Python for better upcoming performance, how a structured query language helps retrieve useful information from the database, and how to visualize the data with the power bi tool.

The project consisted of 2 modules:
* Module 1: Pre-processing, Analyzing data using Python.
* Module 2: Running SQL queries to perform Analysis.

Prerequisites for the project were the following: 
* SQL (MYSQL)
* Excel
* Python
***

## Pre-Processing the Data 
Data Pre-processing is one of the important steps in data analytics because data that is not processed can lead to different unwanted results when the data will be used for further applications. This task included sub-tasks such as handling null values, deletion or transformation of irrelevant values, datatype transformation, removing duplicates, etc.

![](guide.png)

### 1. Removing Unwanted Columns
Removing unwanted columns refers to the process of eliminating irrelevant or unnecessary columns from a dataset. This can improve data analysis and visualization by reducing clutter and focusing on the most important information. It involves identifying and selecting the columns to be removed and executing the removal process using tools like programming languages, database management systems, or spreadsheet software.

### 2. Renaming and Selecting Columns in a Dataset
Renaming columns involves changing the names of one or more columns in a dataset to make them more meaningful or consistent. Selecting columns refers to the process of choosing only specific columns to be included in a dataset, while excluding all others. These techniques are useful for improving the organization and readability of data and can help streamline data analysis. By renaming and selecting only the relevant columns, data scientists can create a more focused and manageable dataset that is better suited for their specific analysis needs.

Only these columns were allowed in the dataset:
1.    Id
2.    Name
3.    online_order
4.    book_table
5.    rating
6.    votes
7.    location
8.    rest_type
9.    dish_liked
10.    cuisines
11.    approx_cost
12.    type

### 3. Dealing with Null Values in a Dataset
Handling null values refers to the process of identifying and addressing missing or incomplete data in each column of a dataset. This involves using techniques like imputation, where missing values are replaced with estimated values based on other data, or deletion, where incomplete records are removed entirely. Proper handling of null values is critical for accurate data analysis and can help prevent bias and errors in results.

Hint:

    delete null values of name column as name is the primary identifier of the dataset
    replace null values of online order with NA
    replace null values of book_table with NA
    replace null values of rating to zero as it is a numerical datatype
    replace null values of votes to zero as it is a numerical datatype
    replace null values of location to NA
    replace null values of rest_type to NA
    replace null values of dishliked to NA
    replace null values of cuisines to NA
    replace null values of approxcost to 0 as it is a numerical value
    replace null values of type to NA
    
### 4. Identifying Duplicate Data in a Dataset
Finding duplicates in a dataset refers to the process of identifying records that are identical or nearly identical to one another. Duplicate data can skew analysis results and waste computational resources, so it is important to identify and remove duplicates before analyzing data. This can be achieved using algorithms that compare records and identify common attributes, or through manual inspection of the dataset.

Hint:

    drop all the duplicate values keeping the first value as it is
    
### 5. Text Cleaning
Text cleaning refers to the process of removing irrelevant or unnecessary text from all the columns in a dataset. This is an essential step in data preprocessing and analysis, as it ensures that the data is accurate and reliable. Text cleaning can involve tasks such as removing stopwords, punctuation, and special characters, as well as correcting spelling and grammar errors.

Hint:

    we have irrelevant reviews like string eg(RATED,Rated) in our name,online_order etc columns
    remove this irrelevant text from all the columns
    
### 6. Unique Value Check and Irrelevant Value Handling
The process of examining each column in a dataset to identify and handle any irrelevant data, while also verifying the uniqueness of values within each column. This helps ensure data accuracy and integrity in analysis and decision-making.

Hint:

    online order column should have only yes and no because it is necessary to have the online order as yes or no only for zomato to perform further analysis, remove other values
    check for rating column and remove NEW,- values to 0 and remove /5 as rating column should only contain decimal values

### 7. Cleaning and Exporting Zomato Dataset
The process of cleaning the Zomato dataset by removing any unknown or unidentifiable characters and exporting the cleaned dataset to a new file named "zomatocleaned.csv". This involves identifying and removing any symbols, special characters, or non-standard characters that may interfere with proper data analysis. By exporting the cleaned dataset to a new file, the original dataset can be preserved and the cleaned data can be easily accessed for further analysis and decision-making.

Hint:

    remove the unknown character from the dataset, we have Ã charachter in our names column
***

## Encounted Problems
It seemed that the dataframe was ready for SQL analysis. However, the project was done in Sandbox Module. The tasks were supposed to be done one after the other, and the program didn't allow to start a new task if the answers for the previous one didn't match. Even though I followed all the hints HiCounselor provided, the final results of my code didn't match the results of the Sandbox code. As a result, I had to add some modifications to the code so it matched the Sandbox results, and I could go further. 
Thus, in step "3.Dealing with Null Values in a Dataset" I replaced null values in "Rating" column with "0.0/5" value. In step "5.Text Cleaning" I added the following lines, so my data had 30340 rows to pass the Sandbox:

            hotels = hotels[hotels["rating"].str.contains("0.0/5") == False]
            hotels = hotels[(hotels['approx_cost']!='0')]
            
Even after all the performed modifications to the code and passing by the Sandbox, the code was not identical to the HiCounselor results. Since a lot of people had the same issue with Sandbox passing, the company provided the cleaned data for SQL analysis. For solving business problems, I uploaded the provided data and worked with it.
However, the cleaned data provided by the company was weird. In the beginning of the analysis, the dataset contained 56,256 rows. After following all the required steps, the data became 32,737 rows. After the modifications that were made in order to pass the Sandbox, the data was 28,818 rows. However, the provided cleaned data contained only 9,880 rows. Basically, what the company did - it removed more than 82% of the entire database, which is not the right thing to do in real live as it is not even the representative sample of the population.
***

## Running SQL Queries

#### Problem 1. 
For a high-level overview of the hotels, provide us the top 5 most voted hotels in the delivery category.

#### Problem 2. 
The rating of a hotel is a key identifier in determining a restaurant’s performance. Hence for a particular location called Banashankari find out the top 5 highly rated hotels in the delivery category.

#### Problem 3. 
Compare the ratings of the cheapest and most expensive hotels in Indiranagar.

#### Problem 4.
Online ordering of food has exponentially increased over time. Compare the total votes of restaurants that provide online ordering services and those that don’t provide online ordering service.

#### Problem 5.
Number of votes defines how much the customers are involved with the service provided by the restaurants. For each Restaurant type, find out the number of restaurants, total votes, and average rating. Display the data with the highest votes on the top (if the first row of output is NA display the remaining rows).

#### Problem 6.
What is the most liked dish of the most-voted restaurant on Zomato (as the restaurant has a tie-up with Zomato, the restaurant compulsorily provides online ordering and delivery facilities).

Again, the code was not passing, that's why I had to add the location Marathahalli to it.

#### Problem 7.
To increase the maximum profit, Zomato is in need to expand its business. For doing so Zomato wants the list of the top 15 restaurants which have min 150 votes, have a rating greater than 3, and is currently not providing online ordering. Display the restaurants with highest votes on the top.
