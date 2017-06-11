# Scraping Data from the Web 1: Free Resources for Storytellers

I try to avoid scraping at all costs. It can be a real pain. Unfortunately, scraping data off websites is unavoidable. 

For advanced scraping, there's no substitute for being able to write a scraper in a coding language, such as Python or Ruby. But the reality is that many of your scraping needs can be accomplished with a number of free tools. 



### What is web scraping

(credit to Rob Gebeloff, NY Times, for finding this quote):

“Web scraping is the act of taking content from a website with the intent of using it for purposes outside the direct control of the site owner.”  [Source:Web Scraping : Everything You Wanted to Know (but were afraid to ask). JULY 22, 2015 by COURTNEY CLEAVES   http://resources.distilnetworks.com/h/i/111901208-web-scraping-everything-you-wanted-to-know-but-were-afraid-to-ask/181642

### What we're going to learn today

Lesson 1: DownloadThemAll, PDF table extraction with Tabula, HTML tables into Excel
Lesson 2: Importing an HTML table into Google Sheets, Using XPATH with Google Sheets, Inspecting a webby map and grabbing the data



## DownloadThemAll!

The most basic web scraping problem is harvesting a bunch of files from a website. For example, [check out how](https://www.fda.gov/drugs/guidancecomplianceregulatoryinformation/surveillance/adversedrugeffects/ucm082193.htm) the U.S. Food and Drug Administration lists files for its adverse events reporting data. 

![Here's what you want.](../master/scraping1.jpg)

Well, it's kind of annoying to grab each one. But there's an add-on for Firefox, [called DownloadThemAll!](https://addons.mozilla.org/en-US/firefox/addon/downthemall/), which can help us automate the downloads and make our lives easier. 

The FDA releases two files for each quarter of data --- one in XML and another in ASCII text.  

Let's only grab the ASCII files. We can use DownloadThemAll's filter. 

![Here's what you want.](../master/scraping2.jpg)

Make sure you tell DownloadThemAll where you want to place the files, then click Start. 

Pretty cool, huh?

## Extracting tables from PDFs using Tabula

Bureaucrats love PDFs. But reporters hate them. Why?

Because PDFs are useless for any kind of meaningful analysis. If you want to analyze the data trapped in PDFs, you need to find a way to get the data into something like Excel or Google Sheets. 

Well, let's learn how to free the data. 

Let's use [this April home sales report](https://www.census.gov/construction/nrs/pdf/newressales.pdf) for New York from the U.S. Census Bureau. Spend a little time taking a look at the tables inside the PDF. 

OK, now let's use [Comet Docs](https://www.cometdocs.com/), a free online file converter. We want to convert from PDF into Excel. 

First thing, click on the "Go to Web App" button. 

![Here's what you want.](../master/scraping3.jpg)

Then click on Upload. 

![Here's what you want.](../master/scraping4.jpg)

Navigate to the Census Bureau housing PDF we downloaded and select it. Comet Docs will import the document. 

![Here's what you want.](../master/scraping5.jpg)

Now drag your uploaded file into the area underneath the convert button. In the next box, to the left of where you just dragged your file, click on "to Excel." Then enter your email address and hit convert. 

![Here's what you want.](../master/scraping6.jpg)

Now wait a short bit and check your email. Comet Docs will send you an email when your file is ready. 

Once you get it, open it up. Voila! 

## HTML to Excel

The best way to get data is a nice, formatted dataset. An Excel sheet. A CSV. But, unfortunately for us, it isn't always that simple. 

Sometimes you see a table online that you want. For example, take a look at [this Wikipedia page](https://en.wikipedia.org/wiki/List_of_United_States_presidential_elections_by_popular_vote_margin)
on presidential election results. Or [this Wikipedia table](https://en.wikipedia.org/wiki/List_of_United_Kingdom_Parliament_constituencies) UK parliamentary constituencies. Today we're going to learn how to get those tables into a spreadsheet with little or no pain. 

### First a little about HTML

As you likely know, underneath what you see in your web browser is a bunch of code, known as HTML (Hypertext Markup Language). It's outside the scope of this course to go deep into HTML (but there are ton of [tutorials](https://www.w3schools.com/html/) out there), but we do need to know a little.

To see what it looks like, let's open up Chrome and go to [this Wikipedia page](https://en.wikipedia.org/wiki/List_of_United_Kingdom_Parliament_constituencies). Right-click and select "View Page Source."

***screen shot here***

HTML uses tags that look something like:

```HTML
<table>Scraping skills table</table>.
```

To start, we are just going to worry about tables. Let's go back to that [Wikipedia page](https://en.wikipedia.org/wiki/List_of_United_Kingdom_Parliament_constituencies) of UK parliamentary constituencies. 

Like many data journalism problems, there's more than one way to tackle the problem. The important thing is to use a method in which you feel comfortable. 

## Basic import of HTML table using Excel

First, let's learn a very simple way to import it into Excel. 

Right click on the web page in Chrome and select "Save as..." We're going to save the page as HTML, so use the "Save as type" pulldown menu to select "Webpage, HTML only." 

Name it whatever you want and click "Save." 

So we've saved the HTML page to our hard drive. Now let's open Excel to a black worksheet. 

Click on the circle thingy in the top left and click "Open." Navigate to where you saved your HTML file. In the bottom left of the window, make sure you change from just looking for Excel files to "All Files *.*)". Select your HTML file. 

It might give you a window that looks like this --- click OK. 

You see a bunch of stuff that looks familiar from the Wikipedia web page. Scroll down until you see the table we're interested in. Great. But we're not done. 

Let's highlight the whole area of the table. Use CTRL-C to copy. Let's click on a new tab at the bottom of Excel and place your mouse in cell A1. Use CTRL-V to paste. 

At this point, I want to get rid of all the flashy HTML links and such. The way I do it is to save the file in some sort of text format, such as CSV or tab-delimited. For this class, let's all save as CSV. 

To do this, go back to that little circle thingy in the upper left-hand corner of Excel. Click on "Save as" again, but this type select "CSV (comma-delimited)(\*.csv)." Click save. 

Now go to the Data tab in Excel. Select "From text" and then navigate to your file. 

Now you'll choose delimited. Click next. 

Change the delimiters to comma. Click next.

For now, we don't have to worry about what's on the next screen. Click finish. 

Voila! Doesn't that look a lot cleaner?

Now to truly make it usable, you'd want to clean up the header row. 


