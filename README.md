# big-data-challenge

# Unit 22 Homework: “Alexa, Can You Handle Big Data?”

# Before You Begin


- Create a new repository for this project called big-data-challenge. Do not add this homework to an existing repository.


- Clone the new repository to your computer.


- Inside your local git repository, create a directory for the level of challenge that you choose. Use folder names corresponding to the challenges: level-1 or level-2.


- Download a Google Colab Notebook as a ipynb file and add it to this folder. This will be the main script to run for analysis. Be sure to also add any SQL queries that you used to a .sql file and then add it to your repo.


- Push the above changes to GitHub or GitLab.



# Background
In this assignment, you will put your ETL skills to the test. Many of Amazon's shoppers depend on product reviews to make a purchase. Amazon makes these datasets publicly available. They are quite large and can exceed the capacity of local machines. One dataset alone contains over 1.5 million rows; with over 40 datasets, data analysis can be very demanding on the average local computer. Your first goal for this assignment will be to perform the ETL process completely in the cloud and upload a DataFrame to an RDS instance. The second goal will be to use PySpark or SQL to perform a statistical analysis of selected data.
This homework assignment contains two levels. The second level is optional but highly recommended.


- Create DataFrames to match production-ready tables from two big Amazon customer review datasets.


- Analyze whether reviews from Amazon's Vine program are trustworthy.




# Instructions

## Level 1


1.) Use the provided schema to create tables in your RDS database.


2.) Create two separate Google Colab notebooks and extract any two datasets from the list at review dataset. Put each dataset into its own notebook.
- Note: You could ETL both data sources in a single Colab notebook, but it will be easier to work with these large S3 data sources in separate notebooks.


3.) Be sure to handle the header correctly. If you read the file without the header parameter, you may find that the column headers are included in the table rows.


4.) Complete the following steps for each notebook (one dataset per notebook).


- Count the number of records (rows) in the dataset.


- Transform the dataset to fit the tables in the schema file. Be sure that the DataFrames match in data type and in column name.


- Load the DataFrames that correspond to tables into an RDS instance. Note: This process can take up to 10 minutes for each. Ensure that everything is correct before uploading.





## Level 2
In Amazon's Vine program, reviewers receive free products in exchange for reviews.

![](https://github.com/evz5050/big-data-challenge/blob/main/vine01.png)

Amazon has several policies to reduce the bias of its Vine reviews: https://www.amazon.com/gp/vine/help?ie=UTF8.
But are Vine reviews truly trustworthy? Your task is to investigate whether Vine reviews are free of bias. Use either PySpark or, for an extra challenge, SQL to analyze the data.


- If you choose SQL, first use Spark on Colab to extract and transform the data and then load it into a SQL table on your RDS account. Perform your analysis with SQL queries on RDS.


- While there are no strict requirements for the analysis, consider steps you can take to reduce noisy data, such as filtering for reviews that meet a certain number of helpful votes, total votes, or both.


- Submit a summary of your findings and analysis.




# Hints and Considerations

Start each notebook with the following code in the first cell, and be sure to update the Spark version.

## code
- import os
(Find the latest version of spark 3.2  from http://www.apache.org/dist/spark/ and enter as the spark version
For example:
spark_version = 'spark-3.2.2')
- spark_version = 'spark-3.<spark version>'
- os.environ['SPARK_VERSION']=spark_version

(Install Spark and Java)
- !apt-get update
- !apt-get install openjdk-11-jdk-headless -qq > /dev/null
- !wget -q http://www.apache.org/dist/spark/$SPARK_VERSION/$SPARK_VERSION-bin-hadoop2.7.tgz
- !tar xf $SPARK_VERSION-bin-hadoop2.7.tgz
- !pip install -q findspark

(set Environment Variables)
- import os
- os.environ["JAVA_HOME"] = "/usr/lib/jvm/java-11-openjdk-amd64"
- os.environ["SPARK_HOME"] = f"/content/{spark_version}-bin-hadoop2.7"

(Start a SparkSession)
- import findspark
- findspark.init()



## For connection to Postgres, run the following code in the next cell:


- !wget https://jdbc.postgresql.org/download/postgresql-42.2.9.jar




# Submission


- Important: You must clean up all your AWS resources. Consult the AWS cleanup guide and AWS check billing guide as reference.


- Download your Google Colab notebooks as .ipynb files and upload those to GitHub.


- Copy your SQL queries into .sql files and upload them to GitHub.


- Important: Do not upload notebooks that contain your RDS password and endpoint. Delete these two items before making your notebook public!


- Ensure your repository has regular commits and a thorough README.md file




