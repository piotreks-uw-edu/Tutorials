### enter the scala intepreter
scala

### exit the Scala interpreter
Control-D

### defines a range of numbers from 1 through 10 (inclusive)
val nums = 1 to 10

### using the map function to transform each element of the nums sequence by doubling it
val doubledNums = nums.map( x => 2*x )

### using the reduce function to compute the sum of all elements in the doubledNums sequence
val sumOfDoubledNums = doubledNums.reduce( (x,y) => x+y )

### defining an immutable value that refers to a sequence of strings
val plays = Seq(
    "tamingoftheshrew", "comedyoferrors", "loveslabourslost", "midsummersnightsdream",
    "merrywivesofwindsor", "muchadoaboutnothing", "asyoulikeit", "twelfthnight")
	
### returns a new collection with only those elements for which the predicate returns 'true'.
val evenNums = someNums.filter( x => (x%2==0) )

### Assing a file and count all it's words
val theBestWords = sc.textFile("dbfs:/fall_2023_users/piotreks/words")
theBestWords.count

### load Scala code from file
:load file.scala

### reset session
:reset

### sapmple function
def parseEmail(email: String): (String, String, String, String, String) = {
    val messageId = "1"
    val date = "2"
    val from = "3"
    val to = "4"
    (messageId, date, from, to, email)
}

### If you need to recurse down into a directory tree, you can use glob stars suitably (get all of the files in the directory below maildir, and in the two levels of directories beneath that)
abfss://data-enron@bd510fall2021.dfs.core.windows.net/maildir/*/*/*

### Read a directory of text files from HDFS, a local file system (available on all nodes), or any Hadoop-supported file system URI. Each file is read as a single record and returned in a key-value pair, where the key is the path of each file, the value is the content of each file. 
### ((a-hdfs-path/part-00000, its content), (a-hdfs-path/part-00001, its content), ...)
val rdd = sc.sparkContext.wholeTextFile("hdfs://a-hdfs-path")





	
