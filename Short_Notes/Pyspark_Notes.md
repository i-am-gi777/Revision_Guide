Spark : unifield computing engine. with set of liabrires for prarllel data 
processing on computer clusters

Pyspark: spark's python API, allowing to write spark applications in 
python instead of java/scala

Apachespark: distributed computing framework for big data processing.

RDD: (resilient distributed dataset) the fundamental data structure of 
spark -immutable, distributed collection.

Transformations: lazy operation that defined a new rdd/dataframe(eg:  map 
filter, select)

Actions: trigger computation and return result (eg: count,collect,show)

DataFrame: disubuted collection of data organized in a named columns

SparkSql: a spark module for running sql queries on structured data. you 
registered dataframe as temporary view and quey them with sql

Lazy evaluation: in spark transformation are not executed immediately. 
they are recorded in dag(directed acyclic graph) execution happens only 
when an action called
-optimize execution plan
-avoids unnecessary computations

caching: store dataframe /rdd in memory only.

persistence: more flexible alloew storage in memory disk or both (with 
different storage levels) use when data is reused multiple times in 
iterrative algoorithms(eg : ML)


```python
# Initialize SparkSession in Pyspark
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName().getOrCreate()
# Note: "SparkSession is the entry point for DataFrame and SQL 
functionalities in pyspark"

# Sample data
student_data = [(1, 'steve'), (2, 'david'),(3, 'aryan')]
student_data_columns =('id', 'name')

# Create DataFrame
data_df = spark.createDataFrame(student_data, student_data_columns)

#sql query/Register tamp view
df.createOrReplaceTempView("people")
spark.sql("select* from people").show()

#create RDDs from 
#list: 
rdd = spark.SparkContext.prallelize([1,2,3])
#file: 
rdd = spark.sparkContext.textFile("file.txt")

#Transformatin
df.filter(df.age>30)
#action
df.count()

#DataFrame operations in pyspark
df.show()
df.select("name").show()
df.count()
df.filter(df.age>30).show()
#Note: common ops: select,filter,groupby,age,agg,join,orderby

# read&write csv/json/perquet
#read
1. df_csv = spark.read.option("header", True).csv("filename/path")
2. df_json = spark.read.option("header", True).json("filename/path")
3. df_parquet = spark.read.option("header", True).parquet("filename/path")
#write
1. df_csv.write.mode("overwrite").option("header", True).csv("path")
2. df_json.write.mode("overwrite").option("header", True).json("path")
3. df_parquet.write.mode("overwrite").option("header", True).parquet("path")

#cache
df.cache()
#persist
df.persist(StorageLevel.MEMORY_AND_DISK)


