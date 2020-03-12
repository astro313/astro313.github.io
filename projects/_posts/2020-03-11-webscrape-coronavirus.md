---
layout: post
title: "Webscraping data on Coronavirus"
date: 2020-03-11
---

My (second?) time webscraping. This time I am not scraping [my own facebook data]({{ site.baseurl }}{% link projects/_posts/2019-01-03-Facebook-Network.md %}), instead, I webscrapped some numbers regarding the number of coronavirus from across the world. 

Since the page I webscrapped provides a table with some of these numbers, the code for webscrapping is quite straightforward. On the other hand, I practiced writing codes for data cleaning and formatting unstructured data. In particular, some entries for some rows in the table are missing. 

I use `selenium` and `chromedriver` to do the webscraping.
corona_webscrape.png
tab.png
clean1.png
clean2.png
loop.png
save.png


<!-- ![HTML code corresponding to table shown in website]({{ site.url }}/projects/assets/corona_webscrape.png) -->
<img src="{{ site.url }}/projects/assets/corona_webscrape.png" alt="Table" width="10%" height="30%">

Finally, I use `cron` to webscrape every 6 hours by executing the python script. `0 0,6,12,18 * * * /anaconda2/bin/python corona.py`