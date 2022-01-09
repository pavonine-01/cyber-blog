---
title: "Building a Python Script to Help Me Buy a Playstation 5"
date: 2021-12-11T21:25:50+11:00
draft: true
image: img/Post1.jpg
tags: ['Projects', 'Bots', 'Python']
---

The newest Playstation 5 console from Sony has been difficult to purchase due to a global manufacturing components shortage, where there is a lack of reliable supply of semiconductor chips necessary to manufacture these consoles.

The lack of reliable playstation 5 stock has lead to a "scalping problem", where re-sellers use "bots" to instantly purchase these consoles and then sell them at absurd markup prices. This causes retailers such as EB Games, JB Hi-Fi or Amazon to immediately go out of stock, making it impossible for the average customer to purchase one at retail price, with a warranty and all of their consumer rights.

With the latest news from Sony confirming the lack of readily available playstation 5 stock into the next year, and after weeks of searching and hoping to get lucky and purchase a console for myself, I decided to take matters into my own hands.

I am going to build a python script that will instantly alert me when a PS5 is restocked online.

## What is a bot?

{{< figure src="/img/Robot1.jpg" height="250" width="250" >}}

A 'bot' is a program that is written to perform a specific task. Bots are used all over the internet to do a variety of important tasks. An example of a good bot is a 'web crawler', which scans content on webpages, usually for search engines such as Google or Bing to learn more about the content on web pages so that human users can search more easily. Bots can also be used to perform a number of different malicious actions, such as spread spam content or carry out Denial-of-Service attacks. Bots can pose a cyber security risk both to organisations and individuals.

In the case of the Playstation 5 console, people colloquially called 'scalpers' have been creating bots to instantly bulk purchase these consoles the moment they become available at retailers, at speeds which the average human buyer cannot hope to match.

## Outline of the Project

The moment a small batch of PS5 consoles are restocked online, particularly in Australian stores such as Big W, Target, Harvey Norman, The Gamesmen or Amazon, they sell out within a few minutes, if not seconds. In order to try to buy one of these consoles, I need to be alerted immediately when they are available for purchase to improve my chances.

In order to build this python script, I am going to use a web-scraping library called **Beautiful Soup**. The link to the documentation for this library can be found [here](https://www.crummy.com/software/BeautifulSoup/bs4/doc/).

The idea of the project is to make an infinite loop that downloads the HTML webpage for the Playstation 5 listing on one of these online stores, and then use **Beautiful Soup** to parse it, looking for changes in the script. Simply put, the script should notice when the "Out of Stock" text changes to "Add to Cart" or "Buy Now", and then should alert me to the change.

The web page I will be parsing is the link to the Amazon listing of the [PS5 Disc Console](https://www.amazon.com.au/Sony-3005718-PlayStation-5-Console/dp/B08FC5L3RG).

To create the alert that will notify me to this change, I will add a trigger that will send me an email. To do this, I will set up a SMTP (Simple Mail Transfer Protocol) server. This can also be done with Python, and I will use the **Nylas Python SDK**. The documentation for this can be found [here](https://developer.nylas.com/docs/the-basics/tutorials/python/send-an-email-with-python/#prerequisites).

## The Project

To install the **Beautiful Soup** library on a Windows OS I used the following commands in my command line:
 
```Python
pip install beautifulsoup4 #Install BeautifulSoup
pip install lxml #Install a Parser
```

A parser is .

[Link](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
[Link](https://realpython.com/beautiful-soup-web-scraper-python/)
[Link](https://realpython.com/python-send-email/)
[Link](https://developer.nylas.com/docs/the-basics/tutorials/python/send-an-email-with-python/#prerequisites)
[Link](https://www.quora.com/How-do-I-make-a-Python-script-that-notifies-me-of-restock-on-best-Buy-I-m-trying-to-get-an-ROG-Strix-3080)
[Link](https://www.pythoncheatsheet.org/)

Tags:
