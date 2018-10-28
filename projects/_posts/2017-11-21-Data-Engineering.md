---
layout: post
title: "Data Engineering: Java gateway error on server"
date: 2017-11-19
---

[Documented](https://docs.google.com/presentation/d/1HWmflcatAeo_kBhp8V3YGBzyPw34Guzj1mbqDKjBRv8/edit?usp=sharing) an error encountered on CDS server. 

```
Traceback (most recent call last):
  File "Costly_21nov.py", line 22, in <module>
    .config("spark.driver.maxResultSize", "4g") \
  File "/home/serverteam_1/anaconda3/lib/python3.6/site-packages/pyspark/sql/session.py", line 169, in getOrCreate
    sc = SparkContext.getOrCreate(sparkConf)
  File "/home/serverteam_1/anaconda3/lib/python3.6/site-packages/pyspark/context.py", line 334, in getOrCreate
    SparkContext(conf=conf or SparkConf())
  File "/home/serverteam_1/anaconda3/lib/python3.6/site-packages/pyspark/context.py", line 115, in __init__
    SparkContext._ensure_initialized(self, gateway=gateway, conf=conf)
  File "/home/serverteam_1/anaconda3/lib/python3.6/site-packages/pyspark/context.py", line 283, in _ensure_initialized
    SparkContext._gateway = gateway or launch_gateway(conf)
  File "/home/serverteam_1/anaconda3/lib/python3.6/site-packages/pyspark/java_gateway.py", line 95, in launch_gateway
    raise Exception("Java gateway process exited before sending the driver its port number")
Exception: Java gateway process exited before sending the driver its port number
serverteam_1@master:~/data$ 
```

Anyway, we outlined what needs to be done/summarized in our final writeup: [Performance and Costly Functions on Server](https://docs.google.com/document/d/11boKGYD5LEStrGUDeVpziuAZKRNJQ4ZNP_Qh6_zT3Gg/edit?usp=sharing)

Basically, up to this point, Linnea and I have investigated 
- The theory of
  1. Basics of partitioning in Spark
  2. Caching/Persisting
  3. Lazy Evaluation
- In practice, issues with
  1. OOM
    - Overhang
    - Heartbeat
    - Py4JJavaError
  2. RDD actions
  3. Java issues on server
  4. (Efficient) join operations
