### how many houses sold were built prior to 1979
// Read the CSV file
val homeDataDF = spark.read.option("header",
"true").csv("dbfs:/fall_2023_users/piotreks/home_data.csv")

// Filter out houses
val oldHouses = homeDataDF.filter(homeDataDF("yr_built").cast("int") < 1979)

// Count the number of houses
val oldHousesCount = oldHouses.count()
println(s"Number of houses built prior to 1979: $oldHousesCount")

### what is the most expensive zipcode in the data set
import org.apache.spark.sql.functions.{avg, max}

val homeDataDF = spark.read.option("header",
"true").csv("dbfs:/fall_2023_users/piotreks/home_data.csv")

// Calculate the average price
val avgPriceByZipcode = homeDataDF
.groupBy("zipcode")
.agg(avg("price").alias("avg_price"))

val maxAvgPrice =
avgPriceByZipcode.agg(max("avg_price").alias("max_avg_price")).first().getAs[Double](
"max_avg_price")

println(s"The most expensive zipcode is:
${mostExpensiveZipcode.getAs[String]("zipcode")} with an average price of
${mostExpensiveZipcode.getAs[Double]("avg_price")}")

### How many unique zipcodes have sales data in the home_data.csv data set
import org.apache.spark.sql.functions.{avg, max}

val homeDataDF = spark.read.option("header",
"true").csv("dbfs:/fall_2023_users/piotreks/home_data.csv")

// Count unique
val uniqueZipcodeCount = homeDataDF.select("zipcode").distinct().count()

println(s"There are $uniqueZipcodeCount unique zipcodes with sales data.")

### drop columns from a dataset
val homeDataDF = spark.read.option("header",
"true").csv("dbfs:/fall_2023_users/piotreks/home_data.csv")

// Drop columns
val modifiedDF = homeDataDF.drop("sqft_living15", "sqft_lot15")

### register a user-defined function (UDF) in your code that can then be used like any builtin Spark functions
// Define the function
val extractStateCode = udf((isoRegion: String) => {
isoRegion.split("-") match {
case Array(_, stateCode) => stateCode
case _ => null
}
})

// Register the functions
spark.udf.register("extractStateCode", extractStateCode)

val airportCodesDF = spark.read.option("header",
"true").csv("dbfs:/fall_2023_users/piotreks/airport_codes.csv")

// Add a new column with the state code
val airportCodesWithState = airportCodesDF.withColumn("state_code",
extractStateCode($"iso_region"))

### Applying a Schema to an RDD to Make a DataFrame
import org.apache.spark.sql.types.{StructType, StructField, StringType, IntegerType}
import org.apache.spark.sql.Row

// Sample data
val peopleData = Seq(("John", 29), ("Ann", 35), ("Steve", 25))

// Create an RDD
val peopleRDD = spark.sparkContext.parallelize(peopleData)

// Define the schema
val schema = StructType(
Array(
StructField("name", StringType, true),
StructField("age", IntegerType, true)
)
)

// Convert to RDD[Row]
val rowRDD = peopleRDD.map(attributes => Row(attributes._1, attributes._2))

// Apply the schema to the RDD
val peopleDataFrame = spark.createDataFrame(rowRDD, schema)