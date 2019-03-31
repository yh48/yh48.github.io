
**Create external table (Dump table into s3)**

Hive:

```sql
CREATE DATABASE IF NOT EXISTS my_table
ROW FORMAT DELIMITED FIELDS TERMINATED BY '\t' LINES TERMINATED BY '\n'
LOCATION 's3://my_bucket/my_path/my_table/';
```



**Add column to table**

Hive:

```sql
ALTER TABLE my_table ADD COLUMNS (my_column string COMMENT 'a new column');
```

MySQL

```sql
ALTER TABLE my_table ADD [COLUMN] (my_column string COMMENT 'a new column');
```



**コラムネーミング変更**

```sql
ALTER TABLE my_table CHANGE my_old_column my_new_column column_definition;
```

**コラムネーミング定義変更**

```sql
ALTER TABLE my_table MODIFY my_column column_definition;
```

```sql
ALTER TABLE my_table DROP my_column;
```


**Load into table**

```sql
CREATE EXTERNAL TABLE my_schema.my_table (
  url string
  ,category1 string
  ,category2 string
  ,remark string
  ,uploader string
)
ROW FORMAT DELIMITED FIELDS TERMINATED BY '\t' LINES TERMINATED BY '\n'
LOCATION 's3://my_bucket/my_path' ;
```
