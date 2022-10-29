# amazon_vine_analysis
______________________

## Amazon Vine Analysis Overview
The vine program is a paid review program where amazon chooses certain insightful reviewers to request and review certain products. The reviewers receive the product free of charge. The question and ultimate purpose of our analysis was this, "Do vine reviews tend towards a higher positive bias in their reviews".

How we set out to achieve this result was to look at datasets provided by amazon in their S3 storage site and pick a set to work with. 
To complete this we first needed to bring the dataset in and begin creating tables in a database. We chose google colab notebooks to work with pyspark on the big data manipulation into PG admin. 

### Configuring our Tools
__________________________
![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/pyspark_init.png)

as seen above here we are loading in our pyspark tools.

![this is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/postgres_pyspark_init.png)

In the image above you can see that we loaded our postgres drivers and then initialized our spark session.

## Loading datasets and dataframe creation
___________________________________________

As mentioned earlier we would need to pick a dataset to work with to analyze reviews. We chose the video games dataset and loaded that into a dataframe

![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/amazon_vg_dataset.png)

From here we needed to filter and create new dataframes that could be used to upload our data into the postgress database we had already created tables for. 

### Customers DataFrame and SQL Table
_____________________________________
![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/customers_table.png) ![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/customers_table_pg.png)

First we created a customers table, which was subsequently uploaded to Postgres. As you will see we chose to make sure the count of values was verified after each upload to make sure that the dataframe came over to the tables correctly. in both cases we see 1045733 values

### Products DataFrame and SQL Table
____________________________________

![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/products_df.png) ![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/products_table.png)

The products dataframe and the completed table

### Review ID DataFrame and SQL Table
_____________________________________

![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/review_id_df.png) ![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/review_id_table.png)

The review ID dataframe and completed table

### Vine Dataframe and Table
____________________________

![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/vine_df.png) ![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/vine_table.png)

The vine dataframe and completed table

## Review Data
______________

Now that we had completed creating and importing the dataframes over to our postrgress database it was time to pull the data we needed for analysis into a pandas dataframe. To do this we would export the Vine table into a CSV file and work with it in pandas.

### Vine DF
__________
![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/vine_df_count.png)

As seen here we pulled in the data and created a dataframe. For each filter or change made to the dataframe I made sure to do a count of each value so that we could confirm the data filters were working. 

We needed to figure out what the percentage of 5 star reviews was for vine paid reviews, and unpaid reviews. To create a better review data set the first thing we did was create a new filtered dataframe that would only show reviews where the percentage of helpful votes were equal to or greater than 50%. 

From there we needed to split the new dataframe even further so that there was one dataframe showing only the reviews from vine, and another dataframe that would show only unpaid reviewers.

![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/greater_50_vinesplit.png)

As you can see after performing those three operations we ended with two dataframes, one for paid vine reviews, 94 in total, and on for unpaid 40,471 in total.

From these two dataframes we could explore further the percentages and determine if there was any bias in the reviews from the vine program.

### Vine Reviews Complete
First we would look at the vine reviewers data frame. We would want to understand the percentage of 5 star reviews to the whole. So we built two variables to create our comparison. A total reviews variable and a 5 stars review variable. Once we had those we could create a third variable to compare and grab a percentage.

![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/vine_complete.png)

As seen in the image above there were 94 total vine reviews and 48 of those were 5-Star reviews. This means that we had a total 5 star review percentage of 51%.



### Unpaid DF
_____________

To get an understanding of whether or not there was any postive bias towards vine reviews we would now need to calculate for the unpaid reviews. We could utilize our prior code and just create new variables.

![This is an image]



