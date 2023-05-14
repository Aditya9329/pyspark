# Pyspark data sources


### how to read csv file in pyspark
```bash
if __name__ == "__main__":
    spark = SparkSession.builder.master("spark://localhost:7077").appName("demo2").getOrCreate()
    print(spark)

    # read the csv file from local 
    df = spark.read.csv('/data/')
 ```
 
 ### how to connect pyspark with aws-rds
 ```bash
 #importing the requiredlibraries and classes
from pyspark.sql import SparkSession
from pyspark.sql.types import StructType,StructField, StringType, IntegerType


if __name__ == "__main__":
    spark = SparkSession.builder.master("spark://localhost:7077").appName("demo2").config('spark.jars','mysql-connector-j-8.0.32.jar').getOrCreate()
    print(spark)

    # read the csv file from local 
    # df = spark.read.csv('/data/')
    # df.printSchema()
    # df.show()

    # df = spark.read \
    # .jdbc("testdb.codhbrttu8gn.us-east-1.rds.amazonaws.com", "employees", \
    #       properties={"user": "admin", "password": "aditya123", "driver":"com.mysql.cj.jdbc.Driver"})

    # df.show()


    df = spark.read \
    .format("jdbc") \
    .option("driver","com.mysql.cj.jdbc.Driver") \
    .option("url", "jdbc:mysql://testdb.codhbrttu8gn.us-east-1.rds.amazonaws.com/company") \
    .option("dbtable", "employees") \
    .option("user", "admin") \
    .option("password", "aditya123") \
    .load()

    df.show()
    ```
 
