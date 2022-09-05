## ETL Overview

The purpose of this weeks analytics lesson was the Extract Transform and Load methodology. In this we worked towards cleaning up and refactoring multiple .csv and JSON files into a format that could be used by others. The movie data had to be cleaned up and merged so that we could read cleanly the title, budget, revenue, and ratings data.


## Clean Function
We started by creating a block of code that would allow us to define a function we would be using throughout the rest of the work. The ETL function I wrote would take in the Ratings CSV, Kaggle Movies Meta Data CSV, and would read and format the Wikipedia JSON file. The function would then help in creating three data frames

![This is an image](https://github.com/Bren42/movies_etl/blob/main/resources/clean_functions_kagglw.png)

as we can see above this is the kaggle metadata in its dataframe view.

![This is an image](https://github.com/Bren42/movies_etl/blob/main/resources/clean_functions_ratingspng.png)

and a quick view of the ratings dataframe with the ratings bins.


## Clean up Kaggle Data
In our second section of our work we ran through the kaggle data to clean up the budget, box office, and ratings data so that we could prepare the dataframes to be eventually merged with the wiki dataframe. This required us to remove extra and unneeded characters in our financial data as well as make sure any of the data objects were set to the right format. We also merged and created new dataframes, such as movies with ratings, tying a couple of the datapoints into a more useable format. When completed we also renamed, reordered and removed columns so that our dataframe had only useable clean data.

![This is an image](https://github.com/Bren42/movies_etl/blob/main/resources/clean_kaggle_moviesdf.png)

![This is an image](https://github.com/Bren42/movies_etl/blob/main/resources/clean_kaggle_movies_ratings.png)

as you can see from the images above we now have a clean movies with ratings dataframe to work with. 


## Clean the wikipedia data

We were now ready to work on the data in the wikipedia dataframe that we created from the JSON file. At this point in the work we had begun re-using several of the functions we had created earlier, we were cleaning the data in much the same way that we had been cleaning the kaggle data as many of the data issues were similar and we needed the data to look the same as the kaggle data so that we had a consistent point to work with once we moved this over to a SQL database.

![This is an image](https://github.com/Bren42/movies_etl/blob/main/resources/wiki_movies_df.png)

As seen above the dataframe is looking very similar to the work that we had done with the Kaggle data, and this is to be expected.

the final part that we wanted to verify was that we had the columns that were requested as being the most useful data points to keep.

![This is an image](https://github.com/Bren42/movies_etl/blob/main/resources/wiki_movies_columns.png)

## Creating a Database

Now that our data was finally in a format we felt was clean enough to work with it is time to store our completed work into a database for the users to pull from. 

This database would include two tables, one for all the movie data, appropriately named movies, and a table for ratings. We needed to make sure all of our data came over in the creation of the tables so we would right some queries to check this. 

We expected 6058 rows of data for the movies database table, so we wrote a query to check this:

![This is an image](https://github.com/Bren42/movies_etl/blob/main/resources/psg_count_movies.png)

Everything checks out on the movies table however we needed to check the data in the ratings table, this had to be uploaded to the database in chunks as the size was way to large to upload in one chunk. This makes vetting the total data count even more imperative.

We wrote a query to check the ratings data which we expected to have 26 million rows.

![This is an image](https://github.com/Bren42/movies_etl/blob/main/resources/psg_ratings_count.png)


## Conclusion
In conclusion the ETL process is a very time intensive and focus intensive project, however without creating and running these functions the time needed to clean the data would have been much more than what we needed to code the solution. It also shows how functions can be re-used across more than one piece of code making the code simpler to write and use as we moved through the process.
