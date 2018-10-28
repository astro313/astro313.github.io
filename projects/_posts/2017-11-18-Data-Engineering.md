---
layout: post
title: "Data Engineering: More Tests on Server"
date: 2017-11-19
---

Last week, Linnea and I encountered numerous issues when we ran the ipynb file on the CDS server. 

We ran more tests on the server to try to disentangle and identify the underlying issues. We suspected some issues might be coming from problem with "heartbeat" due to out of memory (OOM) and reparition. 

More issues and solutions for them are outlined in the [progress report](https://docs.google.com/presentation/d/1R8RrC7CewS_wMx7QIoLFW2TP9FY7g5_-zmAw9PFmn78/edit?usp=sharing) and we presented our progress to the entire team.

TODO:
- finsih solving Java Server Error
- Profiler for caching techniques on the server?