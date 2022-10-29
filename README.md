# amazon_vine_analysis
______________________

## Amazon Vine Analysis Overview
The vine program is a paid review program where amazon chooses certain insightful reviewers to request and review certain products. The reviewers receive the product free of charge. The question and ultimate purpose of our analysis was this, "Do vine reviews tend towards a higher positive bias in their reviews".

How we set out to achieve this result was to look at datasets provided by amazon in their S3 storage site and pick a set to work with. 
To complete this we first needed to bring the dataset in and begin creating tables in a database. We chose google colab notebooks to work with pyspark on the big data manipulation into PG admin. 

![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/pyspark_init.png)

as seen above here we are loading in our pyspark tools.
========================================================================================================================================================================

![this is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/postgres_pyspark_init.png)

In the image above you can see that we loaded our postgres drivers and then initialized our spark session.

As mentioned earlier we would need to pick a dataset to work with to analyze reviews. We chose the video games dataset and loaded that into a dataframe

![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/amazon_vg_dataset.png)

From here we needed to filter and create new dataframes that could be used to upload our data into the postgress database we had already created tables for. 

![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/customers_table.png)
First we created a customers table, which was subsequently uploaded to Postgres. As you will see we chose to make sure the count of values was verified after each upload to make sure that the dataframe came over to the tables correctly.

![This is an image](https://github.com/Bren42/amazon_vine_analysis/blob/main/images/customers_table_pg.png)
