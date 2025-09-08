# Short Note on AWS Glue Job (with PySpark)
# 1.What is AWS Glue?
-AWS Glue is a serverless ETL (Extract, Transform, Load) service that lets you process and move data easily between different data sources.
-Glue uses Apache Spark under the hood for large-scale data processing.
# 2. What is a Glue Job?
-A Glue Job is the main unit of work in AWS Glue. It runs your code (e.g., PySpark scripts) to perform tasks like:
-Reading data from S3 or a database
-Transforming data (e.g., filtering, joining)
-Writing results to another location
# 3.Why PySpark?
-PySpark allows you to write Spark jobs using Python, which is more accessible and readable than Scala/Java.
# Step-by-Step Guide: Create a Sample Glue Job (PySpark) in AWS 
Console
# Prerequisites
-AWS account
-Data file in S3 (e.g., CSV or JSON)
-AWS Glue role with proper S3 access permissions
# Steps to Create Glue Job in PySpark
1. Open AWS Glue Console
-Go to: https://console.aws.amazon.com/glue/
-In the left menu, click Jobs.
2. Click “Create job”
-Click “Create job” button.
3. Configure Job Basics
-Name: e.g., sample-glue-job
-IAM Role: Select or create a role with access to S3 (e.g., 
AWSGlueServiceRole)
-Type: Spark
-Glue version: Choose latest (e.g., Glue 4.0)
-Language: Python
-Job Type: Script
-Script file name: e.g., sample_script.py
-S3 path where the script is stored: You can leave it as default or choose a folder in S3
4. Script Options
Select “Create an empty script”
Or “Start from a template” to get basic code (like S3 to S3 copy)
5. Script Example (PySpark)
```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col

# Step 1: Create Spark session
spark = SparkSession.builder \
    .appName("FlattenEmployeeJSON") \
    .getOrCreate()

# Step 2: Read the JSON files
df = spark.read.json(["employee1.json", "employee2.json"], multiLine=True)

# Step 3: Flatten the address field
flattened_df = df.select(
    col("employee_id"),
    col("first_name"),
    col("last_name"),
    col("address.street").alias("street"),
    col("address.city").alias("city"),
    col("address.state").alias("state"),
    col("address.zip").alias("zip")
)

# Step 4: Show the data (for verification)
flattened_df.show()

# Step 5: Write to CSV
flattened_df.write.csv("output/employees_csv", header=True, 
mode="overwrite")

# Stop the Spark session
spark.stop()

# 6. Save and Run the Job
#Click “Save”
#Click “Run”
#You can monitor the job from the Runs tab.
# 3. How to Use Jupyter Notebook in AWS (Glue Notebooks)
# Option 1: AWS Glue Studio Notebooks (Recommended)
#Step-by-Step:
# -Go to AWS Glue Console
# -Click "Notebooks" or "Jupyter Notebooks"
# -Click "Create notebook"
#Choose:
# -IAM Role with access to S3
# -Glue version (e.g., 4.0)
# -S3 location for notebook storage
#Once created, click “Open notebook” — a Jupyter notebook opens in your browser
##You can write PySpark code using GlueContext like this:
from pyspark.sql import SparkSession
from pyspark.sql.functions import col

# Step 1: Create Spark session
spark = SparkSession.builder \
    .appName("FlattenEmployeeJSON") \
    .getOrCreate()

# Step 2: Read the JSON files
df = spark.read.json(["employee1.json", "employee2.json"], multiLine=True)

# Step 3: Flatten the address field
flattened_df = df.select(
    col("employee_id"),
    col("first_name"),
    col("last_name"),
    col("address.street").alias("street"),
    col("address.city").alias("city"),
    col("address.state").alias("state"),
    col("address.zip").alias("zip")
)

# Step 4: Show the data (for verification)
flattened_df.show()


