---
layout: post
title: "Data Engineering"
date: 2017-11-12
---

This is me (2018-10-28), trying to recall what I did in 2017 to explore `pyspark` and `hadoop` with the [Cornell Data Science Team](https://cornelldata.science/). I was invited to join the group as part of the server team. 

The goal for this subteam is to create our own CDS server cluster and try to explore how to efficiently store data and perform computation. The vision I had for joining is to ultimately optimize the processing of now Tera-to-Peta byte sizes astronomical data from large sky surveys such as [SDSS](https://www.sdss.org/) and then automate event detection and object classification (e.g., different types of galaxies).  

I was paired with a highly-motivated and talented CS-major undergraduate student, Linnea May, to learn about "Data Engineering", which I am a total stranger of. Our team name is "Final Frontier" :)

Our main task for this week is to mplement spark code:
- refer to spark code in sample_spark_code.ipynb in https://github.com/CornellDataScience/hadoop-spark/

Tasks:
- Do data transformation
- Subset columns and filter rows by using .select() or .where()
- use a groupby() operation and an aggregate function .agg() ( sum by group, average by group etc)
- use distinct(), count() operation
- For those of you who know sql, do a sql operation on a table
    - Register the table view
    - run sql query using spark.sql("SELECT....")
- Create a new column using .withColumnNamed()
- Apply a user defined function (UDF)
- Implement an ML model
- (Optional) Implement Cross validations
- Identify a problem and fill out a diagnostics form


