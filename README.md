# pyspark
### read data from hdfs
```bash
empdf = spark.read.option("header",True).option("inferSchema",True).csv("/input_data/employees.csv")
empdf.printSchema() 
```
### read few columns only from the dataframe
```bash
empdf.select("FIRST_NAME","LAST_NAME").show()
```
### prefer syntax for alias
```bash
from pyspark.sql.functions import col
empdf.select(col("FIRST_NAME"),col("LAST_NAME")).show()
```
### column name alias
```bash
empdf.select(col("FIRST_NAME").alias("F_NAME"),col("LAST_NAME").alias("L_NAME")).show()
```
### how to derive a new column
```
withColumn
```
### chaining operation with new derive column
```
empdf.select("EMPLOYEE_ID","FIRST_NAME","SALARY").withColumn("NEW_SALARY",col("SALARY")+1000).show()
```
### how to update the existing column
```bash
empdf.withColumn("SALARY",col("SALARY")+1000).select("EMPLOYEE_ID","FIRST_NAME","SALARY").show()
```
### change the column name
```bash
empdf.withColumnRenamed("SALARY","EMP_SALARY").show()
```
### drop column name
``bash
 empdf.drop("COMMISSION_PCT").show()
 ```
