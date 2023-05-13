# Pyspark data sources


### how to read csv file in pyspark
```bash
if __name__ == "__main__":
    spark = SparkSession.builder.master("spark://localhost:7077").appName("demo2").getOrCreate()
    print(spark)

    # read the csv file from local 
    df = spark.read.csv('/data/')
 ```
 
