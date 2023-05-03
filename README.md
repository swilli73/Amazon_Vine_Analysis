# Amazon_Vine_Analysis
pgAdmin4, SQL, Jupyter Notebook, Pandas, Python, Google Colab

![Amazon sample datasets](https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt) 

![Amazon grocery dataset used for this challenge](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Grocery_v1_00.tsv.gz)

![Resource used for groupby() and agg() function chaining](https://hendra-herviawan.github.io/pyspark-groupby-and-aggregate-functions.html)

## Overview of Amazon_Vine_Analysis
#### This analysis was performed to analyze Amazon reviews written by members of the paid Amazon Vine program. This is a program where businesses provide their products to Amazon Vine members, and for a fee to Amazon, can receive a verified sponsored review of their product. From the list of sample datasets, I chose the "Grocery" dataset. 

#### With this, I created an AWS RDS Database, connected it to a new server + database in Postgres (pgAdmin4), performed an ETL (Extract/Transform/Load) on the data in Google Colab to load the data, clean it up, and export it into four new DataFrames (essentially displaying details on reviews, products, customers, and reviews + whether or not they were Vine reviews). These DataFrames were then combined with tables created in the new Postgres database that would then be open to SQL queries, exporting, etc. 

#### The DataFrame having to do with details on vine reviews was exported (vine_table.csv) and loaded into Jupyter Notebook (Vine_Review_Analysis.ipynb). This data included review IDs and their star rating, votes that marked them as helpful reviews, total votes, whether or not they were Vine reviews, and if they were verified purchases. These were then separated into new DataFrames that displayed reviews with more than 20 votes, and then the former but with at least 50% helpful votes. From this final filtered DataFrame, two new DataFrames were created (Amazon Vine reviews, and non Amazon Vine reviews).

## Results
![Paid](https://i.gyazo.com/bfbc8d4c5d13c06491ae4238bcd75260.png)

![Unpaid](https://i.gyazo.com/ba0443af02e28555bf6ea00823f7e1d8.png)

- In total, there were 61 paid reviews, and 28,287 unpaid reviews from the Grocery dataset. A very small portion of the total reviews were from Amazon Vine members.
- 20 of the paid reviews gave five stars, and 15,689 of the unpaid reviews gave five stars.
- Rounded to two decimal points, 32.79% of the paid reviews were five stars. 55.46% of the unpaid reviews were five stars.

## Summary
#### Given that Amazon Vine verified reviews made up only about .002% of the total "helpful" reviews, it seems like more data is needed to make the conclusion that Vine reviews are generally more critical or trustworthy. With that in mind, looking at the numbers within this dataset, the unpaid reviews are generally kinder. 
#### Another analysis that could be performed to determine a positivity bias would be to eliminate filtering out reviews that were not voted at least 50% "helpful". While community voting can help get rid of outlier and unreliable reviews, it may provide a bigger picture if all the reviews were included. There is sure to be more reviews that are less than five stars if you include reviews with less votes, and/or those that can be considered "unhelpful" by the community. 
#### There are so many more reviews by unpaid users that it seems difficult to concretely compare their positivity and relevance to paid reviews, as the sample size for both are not even remotely close. As stated before, reviews from Amazon Vine users are much more rare compared to the full pool of reviews and ratings. 
