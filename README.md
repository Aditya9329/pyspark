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
