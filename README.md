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

## Case when
car_launches.withColumn("diff",when(col("year")=='2019',-1).otherwise(1))

## Date Format
df.withColumn('month',date_format(col('created_at'),'yyyy-MM'))  --- the same with SQL date_format(created_at,'%Y-%m)



## Python vs. sql vs. spark
(1) SQL: case when
python: def + apply lambda
pyspark: when(,).when(,).otherwise()
