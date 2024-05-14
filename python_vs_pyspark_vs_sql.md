# Unique value
- mySql: distinct
- Python: .unique()
- pyspark: .distinct()

# now time stamp
- mySql: now()
- python: datetime.now()
- pyspark: current_timestamp()

# date difference
- mysql: datediff(end_date,start_date)
- python: (end_timestamp - start_timestamp).days
- pyspark: datediff(col('end_date'),col('start_date'))

# ceil
- mysql: ceiling()
- python: math.ceil()
- pyspark: F.ceil()

# filter
- mysql: where age =100
- python: df[df['age']==100]
- pyspark: where("age==100")
