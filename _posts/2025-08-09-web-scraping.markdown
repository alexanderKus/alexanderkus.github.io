---
layout: post
title:  "Web Scraping"
---

For past few months, I have been more reading than coding, and recently I came across a [Robert Greene](https://en.wikipedia.org/wiki/Robert_Greene_(American_author))'s books.
I found them very practical, so I dug deeper, watched some videos featuring Robert Greene, and discovered his [website](https://powerseductionandwar.com/) where he recommends [books to reed.](https://powerseductionandwar.com/books/)


Unfortunately, the sitie only displays book covers as links to Amazoln store, without listing the title or authors. 
That was very inconvenient, so - as a software engineer I created a small program to scrape a website and retrieve the title and author for each book from Amazon.


I used the [HtmlAgilityPack](https://www.nuget.org/packages/htmlagilitypack/) nuget package for working with HTML documents. 
The results are saved to CSV file.
You can find the code in my [github repository.](https://github.com/alexanderKus/150BooksWebScrapper)

