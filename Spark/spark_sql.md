### INNER JOIN
// using DataFrames
val zipCodesDF = spark.read.option("header",
"true").csv("dbfs:/fall_2023_users/piotreks/wa_zipcodes.csv")

val homeDataDF = spark.read.option("header",
"true").csv("dbfs:/fall_2023_users/piotreks/home_data.csv")

// naming views
zipCodesDF.createOrReplaceTempView("zipcodes")
homeDataDF.createOrReplaceTempView("homes")

// SQL INNER JOIN
val joinedDF = spark.sql("""
SELECT z.* FROM homes h
INNER JOIN zipcodes z ON h.zipcode = z.zipcode
""")

val rowCount = joinedDF.count()

println(s"$rowCount houses were sold with a zipcode defined as being in “Seattle")