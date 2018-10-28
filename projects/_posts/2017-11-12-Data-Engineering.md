---
layout: post
title: "Data Engineering"
date: 2017-11-12
---

We present our overall [progress report](https://docs.google.com/presentation/d/1vHSy9ciaGXcmOzocs1y6TN28VUIi_LwI1ICr-DvYpLg/edit?usp=sharing) to the Cornell Data Science server team. 

Mainly, we tried running last week's Jupyter Notebook on the CDS server, which was just set up running, and wanted to see if that solved the memory issues we were encountering when we ran the ipynb on our own laptops (especially considering the fact that most of the memory on my laptop has been reserved to do my thesis work).

We tried to understand why `pyspark` "committed suicide" many times when we executed methods such as `groupBy, collect`, etc. We learned more about the Spark UI. 

We also encountered some issues with `Py4JNetworkError`... 

It wasn't clear why we were encountering a bunch of issues when we run the ipynb on the server but not on our own laptops.