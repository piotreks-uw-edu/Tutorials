### etrieve the number of partitions into which the DataFrame is divided
result = store_sales_df.rdd.GetNumPartitions()

### etrieve and display the optimized logical plan along with associated statistics
store_sales_df.explain(mode="cost")








### drop duplicates by key taking the second dataframe values
from pyspark.sql.window import Window
from pyspark.sql import functions as F

data_list_1 = [
        {'id': 0, 'val': '0', 'desc': '000'},
        {'id': 1, 'val': 'a', 'desc': 'aaa'},
        {'id': 2, 'val': 'b', 'desc': 'bbb'},
        {'id': 3, 'val': 'c', 'desc': 'ccc'},
       ]

data_list_2 = [
        {'id': 1, 'val': 'x', 'desc': 'xxx'},
        {'id': 2, 'val': 'y', 'desc': 'yyy'},
        {'id': 3, 'val': 'z', 'desc': 'zzz'},
        {'id': 4, 'val': '-', 'desc': '---'},
       ]

df1 = spark.createDataFrame(data_list_1)
df2 = spark.createDataFrame(data_list_2)

df = df1.alias('a').join(df2.alias('b'), 'id', 'outer')

df = df.select('id',
               F.coalesce('b.val', 'a.val').alias('val'), 
               F.coalesce('b.desc', 'a.desc').alias('desc')
               )

df.show()

### drop duplicates by key taking the second dataframe values using windowing
from pyspark.sql.window import Window
from pyspark.sql import functions as F

data_list_1 = [
        {'id': 0, 'val': '0'},
        {'id': 1, 'val': 'a'},
        {'id': 2, 'val': 'b'},
        {'id': 3, 'val': 'c'},
       ]

data_list_2 = [
        {'id': 1, 'val': 'x'},
        {'id': 2, 'val': 'y'},
        {'id': 3, 'val': 'z'},
        {'id': 4, 'val': '-'},
       ]

df1 = spark.createDataFrame(data_list_1)
df2 = spark.createDataFrame(data_list_2)

df1 = df1.withColumn('source', F.lit(1))
df2 = df2.withColumn('source', F.lit(2))

df = df1.union(df2)

window_spec = Window.partitionBy('id').orderBy(F.desc('source'))

df = df.withColumn('rn', F.row_number().over(window_spec)).filter(F.col('rn') == 1).drop('rn', 'source')

df.show()