# superstore-data-analysis-aws
AWS data pipeline for Superstore sales analysis (S3, Glue, Athena, QuickSight). Explore data acquisition, storage, querying &amp; visualization.

This project demonstrates an end-to-end data engineering workflow for analyzing sales order data using various AWS services:

Project Objective: Build a data pipeline to analyze order data from the Kaggle Superstore dataset and create visualizations for insights.

Technologies Used:

AWS Identity and Access Management (IAM): An IAM user with administrator access was created for project management.
Amazon Simple Storage Service (S3): An S3 bucket named "bucket-superstore-project" was created to store the order data in CSV format.
AWS Glue:
A database named "db_superstore" was created in the AWS Glue Data Catalog.
A crawler was configured to automatically discover and register new data files uploaded to the S3 bucket.
Partitions were created within the S3 bucket based on date (e.g., "snapshotday=2017-01-01") for efficient data retrieval.
Amazon Athena: Used for querying the orders table stored in the Glue Data Catalog. Athena leverages partition pruning to optimize queries by only scanning relevant data based on filters (e.g., specific date).
Amazon QuickSight: Used to create visualizations (bar and pie charts) for analyzing order trends and patterns.
Project Steps:

IAM User Creation: An IAM user with administrator access was created for managing the project resources.
S3 Bucket Setup: An S3 bucket named "bucket-superstore-project" was created to store the Superstore order data in CSV format.
Data Preparation:
Downloaded Superstore data from Kaggle.
Filtered data by date (January 1st and 2nd) to create separate CSV files representing daily sales data.
AWS Glue Configuration:
Created a database named "db_superstore" in the AWS Glue Data Catalog.
Defined a new IAM role for the crawler with appropriate permissions.
Set up a crawler with on-demand frequency to automatically discover new data files in the S3 bucket.
Data Partitioning: Created two folders within the S3 bucket named "snapshotday=2017-01-01" and "snapshotday=2017-01-02" to store the filtered CSV files, enabling partitioned data access in Athena.
Crawler Execution: Ran the crawler to register the data files in the Glue Data Catalog.
Amazon Athena Queries:
Created a folder named "athena_logs" in the S3 bucket to store query logs.
Performed queries on the "orders" table within the "db_superstore" database.
Demonstrated the efficiency of partition pruning by comparing query times:
Full table scan: select * from "dbstore".orders (data scanned: 4.47 KB)
Partitioned query: select * from "dbstore" where snapshot_day='2027-01-02' (data scanned: 1.99 KB)
Amazon QuickSight Visualization: Utilized Amazon QuickSight to create interactive bar and pie charts for analyzing order trends based on the data retrieved from Athena.
Results: This project successfully built a data pipeline for storing, managing, querying, and visualizing order data using AWS services. Partition pruning in Athena significantly optimized query performance. Visualizations created with Amazon QuickSight provided valuable insights into sales patterns.

Access to Visualization:

The visualizations created with Amazon QuickSight can be accessed at the following URL (note: access may be restricted): https://us-east-1.quicksight.aws.amazon.com/sn/accounts/339712881135/dashboards/ea12a883-fd6c-4f74-b1de-8cbd4d83d9c2?directory_alias=ganeshvadlamuri
