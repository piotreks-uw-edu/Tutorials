### create an RDD from a local Scala collection , distribute the local collection across the nodes of the Spark cluster
val someNums = sc.parallelize(1 to 25)

### retrieves the first n elements from the RDD
someNums.take(5)

###  create an RDD of key/value pairs where the key is the id of a row and the value is everything else
val homeData = sc.textFile("dbfs:/fall_2023_users/piotreks/home_data.csv")

def createPairs(inputData: RDD[String]): RDD[(String, String)] = {
inputData.map(line => {
val columns = line.split(",")
val key = columns(0)
val value = columns.slice(1, columns.length).mkString(",")
(key, value)
})
}

val pairs = createPairs(homeData)

pairs.take(3).foreach(println)