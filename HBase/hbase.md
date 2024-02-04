### create a table
create 'wiki_1colfam', 'data'
or
create 'wiki_2colfams', 'metadata', 'content'exit

### insert values
put <table>, <rowId>, <columnFamily:columnQualifier>, <value>

put 'sentences', 'row1', 'words:subject', 'I'
put 'sentences', 'row1', 'words:verb', 'drink'
put 'sentences', 'row1', 'words:object', 'coffee'

### get row by row id
get 'sentences', 'row1'

### scans the ‘sentences’ table and passes in its argument dictionary a FILTER whose details are specified as a string
scan 'sentences', {FILTER => "ValueFilter(=, 'binary:English')"}

### scans the ‘sentences’ table and passes a slightly bigger dictionary of arguments for the scan
scan 'sentences', {COLUMNS => 'words:subject', ROWPREFIXFILTER => 'row' }

### 
scan 'sentences', {COLUMNS => 'words:subject', FILTER => "ValueFilter(=, 'substring:I')"}


### 
scan 'wiki_1colfam', {COLUMNS => 'data:author', FILTER => "ValueFilter( =, 'binaryprefix:Ed' )" }


### import from *.csv (one column family)
hbase org.apache.hadoop.hbase.mapreduce.ImportTsv \
-Dimporttsv.separator=, \
-Dimporttsv.columns="HBASE_ROW_KEY, data:author" \
wiki_1colfam \
file:///data/wikidata/author.csv

### import from *.csv (two column families)
hbase org.apache.hadoop.hbase.mapreduce.ImportTsv \
-Dimporttsv.separator=, \
-Dimporttsv.columns="HBASE_ROW_KEY, metadata:author" \
wiki_2colfams \
file:///data/wikidata/author.csv

