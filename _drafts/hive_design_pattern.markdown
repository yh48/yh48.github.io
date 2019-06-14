https://medium.com/datakaresolutions/hive-design-patterns-783d6104d852



Typically the data ingestion process involves following scenarios to add new set of data to the Hadoop Layer.

- Complete load
- Append Load
- Insert or Update Ingestion:


http://dwgeek.com/apache-hive-table-design-best-practices-considerations.html/


Choose appropriate storage format
Compression Techniques
Partition Tables
Bucketing Tables
Data Locality


avoid: text format, sequence file format, complex storage format such as json

ideally, RCFile(Row Columnar File), or **Parquet files**

Compression of data on HDFS query execution time.
consumes lot of CPU power, does not affect map reduce jobs as they are I/O bound.

Partition Large Tables

partition large hive tables if you are collecting time series data.


**bucketing hive tables**

clusters or buckets.


Data Locality

Use Amazon S3 only for backup and restore. Do not use it as a main storage as read/write .

Use adoop HDFS storage to take advantage of data locality.







1. Complete/Full Load


overlapping partitions dropped completely and recreated with new set of data

```sql
set hive.exec.dynamic.partition=true;
set hive.exec.dynamic.partition.mode=nonstrict;


```


2. Append Load

3. Insert or Update Ingestion
