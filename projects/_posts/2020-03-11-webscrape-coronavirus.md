---
layout: post
title: "Webscraping data on Coronavirus"
date: 2020-03-11
---

My (second?) time webscraping. This time I am not scraping [my own facebook data]({{ site.baseurl }}{% link projects/_posts/2019-01-03-Facebook-Network.md %}), instead, I webscrapped some numbers regarding the number of coronavirus from across the world. 

Since the page I webscrapped provides a table with some of these numbers, the code for webscrapping is quite straightforward. On the other hand, I practiced writing codes for data cleaning and formatting unstructured data. In particular, some entries for some rows in the table are missing. 

I use `selenium` and `chromedriver` to do the webscraping. <img src="{{ site.url }}/projects/assets/corona_webscrape.png" alt="Table" width="10%" height="30%">
<img src="{{ site.url }}/projects/assets/tab.png" alt="Table" width="10%" height="30%">

To deal with country names that are splited into multiple elements of a list after scraping each row of the table: 
<img src="{{ site.url }}/projects/assets/clean1.png" alt="Table" width="10%" height="30%">

European standard uses ',' for thousands, etc. To convert numbers into floating point, I need to first remove ',' from the entry stored as a string. Since there are missing entries in the table, we want to replace it with something that we could convert into a floating point number, since the rest of the columns (except for country name) should and will become a float in the final dataframe. In Astronomy, it's common that if a number is missing, or a measurement is an upper or lower limit, '-99' is used. I adapted such convension into my webscraping/data engineering step. 
<img src="{{ site.url }}/projects/assets/clean2.png" alt="Table" width="10%" height="30%">

To get the data for all the countries, I wrote a loop and calls a method within that class `parse_row_to_dict()` to get the data for a given country, and put that dictionary `df` into a `pandas` dataframe.
<img src="{{ site.url }}/projects/assets/loop.png" alt="Table" width="10%" height="30%">

After getting the datafrmae, I save the dataframe based on the time and date. The idea is to automate this webscraping and save the dataframe periodically.
<img src="{{ site.url }}/projects/assets/save.png" alt="Table" width="10%" height="30%">

Finally, I use `cron` to webscrape every 6 hours by executing the python script. In particular, I added `0 0,6,12,18 * * * /anaconda2/bin/python corona.py` to my `cron` job list.
<img src="{{ site.url }}/projects/assets/saved.png" alt="Table" width="10%" height="30%">
