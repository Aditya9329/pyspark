# pyspark
### read data from hdfs
```bash
empdf = spark.read.option("header",True).option("inferSchema",True).csv("/input_data/employees.csv")
empdf.printSchema() 
```
