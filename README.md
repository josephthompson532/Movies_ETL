# Movies_ETL

## Purpose
The purpose of this repository was to demonstrate my ability to take exceptionally dirty data and clean data from multiple sources, transform the data, combine the sources into a single dataset, and then export the data to a relational database such as PostgreSQL.

### Overview
I started with 3 different data sources: a Kaggle csv file, a json file, and a ratings csv file containing rating information for movies. The files were too large to upload to Github themselves, so I have not uploaded them here. The json files was in particularly unusable condition. It started out with 192 columns. Through the use of list-comprehensions and functions, I was able to cut the columns down to a reasonable number of only those columns with useful information. Then I got rid of rows with null values or values without an "imdb_rating" or with a "No. of Episodes" since we were only looking for movies. Any column that did not meet a certain threshold non-null values was also drop. It was an iterative process but eventually I was able to get the data down to a form that was clean and had only the columns we needed. 

***To see this process, please reference the "ETL_clean_kaggle_data.ipynb" file.***


Next, I performed a similar iterative process for the two csv files. Once finished, the task of combining these datasets into one was the next goal. To do these I combined them all into a single dataframe using the "pd.merge()" function. After I used matplotlib to visualize the difference between similarly named columns and decide which versions of the columns to drop and which versions to keep. 

Once I had one clean dataset resulting from the combination of the original three, I imported the data into a PostgreSQL relational database and performed queries on it:

<img width="510" alt="Screen Shot 2020-10-02 at 3 21 02 PM" src="https://user-images.githubusercontent.com/66881241/94974288-ecec2e80-04c2-11eb-932e-4e5bb0e74128.png"> <img width="546" alt="Screen Shot 2020-10-02 at 3 20 53 PM" src="https://user-images.githubusercontent.com/66881241/94974290-ef4e8880-04c2-11eb-9ab7-aa3b37f2c606.png">


## Result
The result was a single-table, fully functional database in PostgreSQL that I could perform queries using SQL.
