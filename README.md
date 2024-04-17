# pyspark

- round() -> .cast('integer')
- nunique() -> .countDistinct()
- calculate column -> .withColumn('', col('')...)
- change column name -> .alias()
- concat column while adding strings in between -> concat(col(A), lit(' to '), col(B))
- using pyspark to perfrom SQL window function
  ```pyspark
  from pyspark.sql.window import Window
  windowspec = Window.partitionBy('device_type').orderBy(col('user_count').desc())
  df = df.withColumn('usr_rnk',dense_rank().over(windowspec))
  df.select('user_count','time_period','device_type').filter(col('usr_rnk') == 1).toPandas()
  ```
