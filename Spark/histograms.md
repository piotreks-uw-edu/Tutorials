### Create a “histogram” of the counts for each type defined in the “home_ownership” column.
import org.apache.spark.sql.functions.count

val loanDF = spark.read.option("header",
"true").csv("/fall_2023_users/piotreks/loan.csv")

// Group by "home_ownership" and count each type
val homeOwnershipHistogram =
loanDF.groupBy("home_ownership").agg(count("home_ownership").alias("count"))

// Show the histogram
homeOwnershipHistogram.show()