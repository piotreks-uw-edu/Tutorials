### Convert the CSV data to parquet format
val csvFilePath = "/dbfs/fall_2023_users/piotreks/loan.csv"

val loanDF = spark.read.option("header",
"true").csv("/fall_2023_users/piotreks/loan.csv")

### read parquet file
val parquetFilePath = "/dbfs/fall_2023_users/piotreks/loan.parquet"
loanDF.write.mode("overwrite").parquet(parquetFilePath)

val loanDFParquet = spark.read.parquet(parquetFilePath)

