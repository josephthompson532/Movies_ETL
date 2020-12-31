# Movies_ETL
* NOTE: The finished product of this repository is under "ETL_create_database.ipynb"

## Purpose
The purpose of this repository was to perform ETL on near unsalvageablely dirty data scraped from wikipedia, join it with several kaggle datasets, and then import it into a Postgres database using Sqlalchemy. This project was mean in particular to showcase various methods of transform data into an ingestible and clean form. 

### Overview
I started with 3 different data sources: a Kaggle csv file, a json file, and a ratings csv file containing ratings information for a variety of movies. The files were too large to upload to Github themselves, so I have not uploaded them here. 

The json file was in particularly unusable condition. It started out with 192 columns. Through the use of list-comprehensions and functions, I was able to cut the columns down to a reasonable number of only those columns with useful information. I then got rid of rows with null values or values without an "imdb_rating" column or with a "No. of Episodes" column since we were only looking for movies. Any column that did not meet a certain threshold of non-null values was similarly dropped. It was an iterative process but eventually I was able to get the data down to a form that was clean and had only the columns I needed. I then streamlined this process by reformatting all of my code into a set of functions.

***To see this process, please reference the "ETL_clean_kaggle_data.ipynb" file.***


Next, I performed a similar iterative process for the two csv files. Once finished, the task of joining these three datasets into one was the next goal. To do these I combined them all into a single dataframe using the "pd.merge()" function. Afterwards, I used matplotlib to visualize the difference between similarly named columns and decided which versions of the columns to drop and which versions to keep. 

Once I had one clean dataset resulting from the combination of the original three, I imported the data into a PostgreSQL relational database and performed queries on it:

<img width="510" alt="Screen Shot 2020-10-02 at 3 21 02 PM" src="https://user-images.githubusercontent.com/66881241/94974288-ecec2e80-04c2-11eb-932e-4e5bb0e74128.png"> 

<img width="546" alt="Screen Shot 2020-10-02 at 3 20 53 PM" src="https://user-images.githubusercontent.com/66881241/94974290-ef4e8880-04c2-11eb-9ab7-aa3b37f2c606.png">


## Result
The result was a single-table, fully functional database in Postgres that I could perform queries on using SQL.
