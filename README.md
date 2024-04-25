# pyspark

- round() -> .cast('integer')
- nunique() -> .countDistinct()
- calculate column -> .withColumn('', col('')...)
- change column name -> .alias()
- concat column while adding strings in between -> concat(col(A), lit(' to '), col(B))
- using pyspark to perfrom SQL window function
  ```pyspark
  from pyspark.sql.window import Window
  # over后面的部分
  windowspec = Window.partitionBy('device_type').orderBy(col('user_count').desc())
  # over及其前面的部分
  df = df.withColumn('usr_rnk',dense_rank().over(windowspec))
  # 选出最大值
  df.select('user_count','time_period','device_type').filter(col('usr_rnk') == 1).toPandas()
  ```
- use .count() instead of len()

## Join
shopify_orders.join(shopify_carriers, shopify_orders['carrier_id'] == shopify_carriers['id'], 'inner')
