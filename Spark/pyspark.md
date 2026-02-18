### combine two DataFrames where the column names are permuted differently but should be matched based on the names rather than the positions
df.unionByName(df2)

### works like SQL command UNION
val unionDropDuplicates = readBack1Through7DF.union(readBack4Through12DF).union(readBack9Through18DF).dropDuplicates()

### works like SQL command UNION ALL
val unionDropDuplicates = readBack1Through7DF.union(readBack4Through12DF).union(readBack9Through18DF)


### rops duplicates based on only the surrogate key
df.dropDuplicates("cd_demo_sk")

### drop column from a dataframe
df = df.drop('column1', 'column2')

### Rename a single column
df = df.withColumnRenamed("name", "full_name")