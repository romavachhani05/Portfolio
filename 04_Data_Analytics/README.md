This project involves analyzing Yelp's open dataset (5GB JSON) to derive insights using an end-to-end data pipeline that incorporates:
	• Python for data prep and sentiment analysis
	• AWS S3 for intermediate storage
	• Snowflake for structured storage, querying, and UDF-based sentiment analysis in SQL

✅ Step-by-Step Instructions
1. Download and Explore Yelp Dataset
	• Download Yelp's open dataset from: https://www.yelp.com/dataset
	• Extract the .tar file to access:
		○ business.json
		○ review.json
	• Focus on these two files:
		○ business.json: business metadata
		○ review.json: 7M+ user reviews
2. Split Large JSON File with Python
	• Write a Python script to:
		○ Count lines in review.json
		○ Split into ~25 smaller files (each ~200MB)
		○ Save them for faster parallel upload & ingestion
3. Upload Files to AWS S3
	• Create an AWS account and an S3 bucket (e.g., namaste-sql/yelp/)
	• Upload all split JSON files into the S3 folder
	• Ensure IAM user has AmazonS3ReadOnlyAccess
4. Set Up Snowflake Environment
	• Sign up at: https://signup.snowflake.com/
	• Create:
		○ New Database (e.g., YelpDB)
		○ New Warehouse (start with XS, scale as needed)
