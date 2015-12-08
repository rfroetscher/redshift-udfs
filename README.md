# Redshift UDFs

Just a simple place to keep some useful Redshift UDFs, including ruby YAML parsing.

### Notes on the YAML helpers

These are meant to help acccess the values of one-level-deep persisted ruby hashes with symbol keys.

For example:
```sql
warehouse=# SELECT yaml_timestamp(ruby_persisted_hash, 'activity_time') FROM some_table WHERE ruby_persisted_hash LIKE '%activity_time%' LIMIT 1;
   yaml_timestamp
---------------------
 2012-12-01 03:25:49
(1 row)
```

In order to make this work, you must upload [this directory](https://github.com/yaml/pyyaml/tree/master/lib/yaml)
(zipped) to S3 and reference its location in the CREATE LIBRARY call below.
