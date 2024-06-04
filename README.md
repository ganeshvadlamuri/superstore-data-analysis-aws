# Superstore-Data-Analysis-AWS
AWS data pipeline for Superstore sales analysis (S3, Glue, Athena, QuickSight). Explore data acquisition, storage, querying &amp; visualization.

This project demonstrates an end-to-end data engineering workflow for analyzing sales order data using various AWS services:

### Project Objective: 
Build a data pipeline to analyze order data from the Kaggle Superstore dataset and create visualizations for insights.

### Technologies Used:

* AWS Identity and Access Management (IAM): 
An IAM user with administrator access was created for project management.
* Amazon Simple Storage Service (S3): An S3 bucket named "bucket-superstore-project" was created to store the order data in CSV format.
* AWS Glue:
A database named "db_superstore" was created in the AWS Glue Data Catalog.
A crawler was configured to automatically discover and register new data files uploaded to the S3 bucket.
Partitions were created within the S3 bucket based on date (e.g., "snapshotday=2017-01-01") for efficient data retrieval.
* Amazon Athena: Used for querying the orders table stored in the Glue Data Catalog. Athena leverages partition pruning to optimize queries by only scanning relevant data based on filters (e.g., specific date).
* Amazon QuickSight: Used to create visualizations (bar and pie charts) for analyzing order trends and patterns.

### Project Steps:
1. IAM User Creation: An IAM user with administrator access was created for managing the project resources.
2. S3 Bucket Setup: An S3 bucket named "bucket-superstore-project" was created to store the Superstore order data in CSV format.

#### 3. Data Preparation:
* Downloaded Superstore data from Kaggle.
* Filtered data by date (January 1st and 2nd) to create separate CSV files representing daily sales data.
4. AWS Glue Configuration:
Created a database named "db_superstore" in the AWS Glue Data Catalog.
Defined a new IAM role for the crawler with appropriate permissions.
Set up a crawler with on-demand frequency to automatically discover new data files in the S3 bucket.
5. Data Partitioning: Created two folders within the S3 bucket named "snapshotday=2017-01-01" and "snapshotday=2017-01-02" to store the filtered CSV files, enabling partitioned data access in Athena.
6. Crawler Execution: Ran the crawler to register the data files in the Glue Data Catalog.
7. Amazon Athena Queries:
* Created a folder named "athena_logs" in the S3 bucket to store query logs.
* Performed queries on the "orders" table within the "db_superstore" database.
* Demonstrated the efficiency of partition pruning by comparing query times:
Full table scan: select * from "dbstore".orders (data scanned: 4.47 KB)
Partitioned query: select * from "dbstore" where snapshot_day='2027-01-02' (data scanned: 1.99 KB)
8. Amazon QuickSight Visualization: Utilized Amazon QuickSight to create interactive bar and pie charts for analyzing order trends based on the data retrieved from Athena.

### Results: 
This project successfully built a data pipeline for storing, managing, querying, and visualizing order data using AWS services. Partition pruning in Athena significantly optimized query performance. Visualizations created with Amazon QuickSight provided valuable insights into sales patterns.

### Access to Visualization:
* The visualizations created with Amazon QuickSight can be accessed at the following URL (note: access may be restricted): https://us-east-1.quicksight.aws.amazon.com/sn/accounts/339712881135/dashboards/ea12a883-fd6c-4f74-b1de-8cbd4d83d9c2?directory_alias=ganeshvadlamuri


------------------------
![iam_admin_access](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/4155a430-75d3-4b76-b169-a5c7a7042ad1)
![s3_bucket_creation](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/e4423b96-8039-4fdf-82ef-be50dd20cd51)
![s3_bucket_creation_1](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/55e236a5-5367-4f3c-866d-d1eeae3f5364)
![aws_glue_db](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/bff1dc07-55bf-43eb-b47d-86307281a543)
![aws_crawler](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/3b88923d-8931-43b4-a1f4-2051db2217b0)
![permission_policies](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/94567579-08e1-4333-8e13-27e752d70bcc)
![running_crawler](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/c5ead0ca-9c65-4e23-a008-806b80950d1b)
![schema](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/33005cec-98db-48ba-87eb-ce0fc75d527c)
![crawler](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/09dc8c9a-16b1-47b0-9057-d29980c37507)
![query_1](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/4d877cf9-97f9-49eb-80f9-e5dc4c1fc618)
![filtered_data](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/3847783e-7f88-498c-a6f1-17a783d5d5c7)
![quicksight_barchart](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/39f36cc8-bc2c-42f8-bdb9-3010bbe7a069)
![quicksight_piechart](https://github.com/ganeshvadlamuri/superstore-data-analysis-aws/assets/85800035/5790d1e2-ad50-48a1-9bc6-bedb92543d07)











