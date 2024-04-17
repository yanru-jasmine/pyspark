# pyspark

- round() -> .cast('integer')
- nunique() -> .countDistinct()
- calculate column -> .withColumn('', col('')...)
- change column name -> .alias()
- concat column while adding strings in between -> concat(col(A), lit(' to '), col(B))
