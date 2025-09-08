
# 1.What is pyspark?
 Python interface /python API for Apache Spark , a powerful engine for big data processing       
 PySpark = Apache Spark + Python
# 2.Why use pyspark? 
 Fast, scalable, handles big data         
# 3.Core tool?  
`SparkSession`, DataFrames               
# 4.Use cases - Data analysis, streaming, ML on big data 
# 5.How Does PySpark Work?
You write code using PySpark (in Python)
Behind the scenes, PySpark talks to the Spark engine (written in Scala/Java)
Spark distributes the data and computation across many computers
The result comes back to you in a DataFrame, like a big table
# 6. what is PySpark Architecture?
            +----------------------+
            |     Driver Program   |
            | (your PySpark code)  |
            +----------+-----------+
                       |
                       v
           +-----------+-----------+
           |    Cluster Manager     |
           | (YARN / Standalone / K8s) |
           +-----------+-----------+
                       |
           +-----------+-----------+
           |      Executors (Workers)  |
           |   - Run tasks             |
           |   - Cache data            |
           +---------------------------+

# Broadcast in PySpark
1.What
When you have a small dataset (like a lookup table), you can use broadcast to send it to all worker nodes in the cluster once, instead of sending it over and over again.

2.Why
Avoids sending the small data repeatedly over the network
Makes joins faster

# Cache in PySpark
1.What
cache() stores the DataFrame in memory (RAM) after the first action so that future actions are faster.

2.Why
Speeds up repeated operations on the same data

# Persist in PySpark
1.What
persist() is more flexible than cache() – you can choose where and how to store the data: memory, disk, or both.

2.Why
Use when your data can’t fit fully in memory

# Repartition 
Can increase or decrease partitions
Performs a full shuffle
Balances data evenly across partitions
--USE:
Preparing for joins, groupBy, etc.
Need more parallelism
Want even data distribution

Example:
df = df.repartition(10)
df = df.repartition("country")  # by column

# Coalesce
Can only decrease number of partitions
No full shuffle – faster
May result in uneven partition sizes
--USE:
Reducing output files (e.g. before write)
Want a quick partition reduction

Example:
df = df.coalesce(1)

NOTE:
broadcast() - Joining large and small DataFrame	
cache() - Using same DataFrame multiple times (enough RAM)	
persist() - Data too big for memory, still want reuse	
repartition() – Redistribute with shuffle
coalesce() – Reduce without shuffle

TOPICS I COVER BELOW:
1.Reading & Writing CSV
2.Reading & Writing Parquet
3.Reading & writing Json
4.Create & Reading CSV file


```python
from pyspark.sql import SparkSession
# Initialize SparkSession
spark = SparkSession.builder.getOrCreate()
# Sample data
student_data = [(1, 'steve'), (2, 'david'),(3, 'aryan')]
student_data_columns =('id', 'name')
student_marks = [(1, 'pyspark', 90), (1, 'sql', 100), (2, 'sql', 70), (2, 
'pyspark',60), (3, 'sql',30), (3, 'pyspark', 20)]
student_marks_columns = ['id', 'subject', 'marks']
# Create DataFrame
data_df = spark.createDataFrame(student_data, student_data_columns)
marks_df = spark.createDataFrame(student_marks, student_marks_columns)
#Show data
data_df.show()
marks_df.show()
#Load
# write data in json file #
data_df.write.option("overwrite").option("header", 
True).json("/Users/prasannahi/PycharmProjects/Pyspark/student_data")
# write data in csv file #
marks_df.write.mode("overwrite").option("header", 
True).csv("/Users/prasannahi/PycharmProjects/Pyspark/student_marks")
# Extract
# read  file from datasource#
s_data_df = spark.read.option("header",True).json("student_data")
s_marks_df = spark.read.option("header",True).csv("student_data")
#Transform
# Register tamp view
s_data_df.createOrReplaceTempView('student_data')
s_marks_df.createOrReplaceTempView('student_marks')
# Sql query
df1 = spark.sql('''select 
          student_data.id,
          student_data.name,
          student_marks.subject,
          student_marks.marks from student_data
          join student_marks
          on student_data.id = student_marks.id''')
#Load
# write data in parquet file #
df1.write.mode("overwrite").option("header", 
True).parquet("/Users/prasannahi/PycharmProjects/Pyspark/student_details")
# Extract
# read  file from datasource#
df2 = spark.read.option("header",True).parquet("student_details")
#-----------------------------------------#

# create/write CSV file 

```python
import csv 
data =[["Name", "Age", "City"],
    ["Alice", "30", "New York"],
    ["Bob", "25", "San Francisco"],
    ["Charlie", "35", "London"]]
with open ("people.csv", mode='w', newline="") as file:
    writer = csv.writer(file)
    writer.writerows(data)

# Read CSV file

```python
import csv

with open ("people.csv ", mode = 'r',newline = " ") as file:
    reader =csv.reader(file)
    for row in reader:
        print(row)


----

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


