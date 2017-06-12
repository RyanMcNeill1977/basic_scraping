# Scraping Data from the Web 1: Free Resources for Storytellers

I try to avoid scraping at all costs. It can be a real pain. Unfortunately, scraping data off websites is unavoidable. 

For advanced scraping, there's no substitute for being able to write a scraper in a coding language, such as Python or Ruby. But the reality is that many of your scraping needs can be accomplished with a number of free tools. 



### What is web scraping

(credit to Rob Gebeloff, NY Times, for finding this quote):

“Web scraping is the act of taking content from a website with the intent of using it for purposes outside the direct control of the site owner.”  [Source:Web Scraping : Everything You Wanted to Know (but were afraid to ask). JULY 22, 2015 by COURTNEY CLEAVES   http://resources.distilnetworks.com/h/i/111901208-web-scraping-everything-you-wanted-to-know-but-were-afraid-to-ask/181642

### Why do we scrape

Scraping can be a pain, but it is also a way to keep you ahead of your competition. It can also help you "datify" something that isn't very structured. 

A few examples of what we might scrape:

--- A state courts website that doesn't make available the raw underlying data

--- If you're working on a story and want to make sure your spreadsheet always has the most up-to-date information on something like currency exchange rates, stock prices or weather. 

--- Sports stats

--- Message board postings from people seeking to get rid of adopted children. 


When I first arrived at Reuters, I was assigned to work on a project that would become [The Child Exchange](http://www.reuters.com/investigates/adoption/#article/part1). We'll talk about it in class, but the entire quantiative spine of the series was made possible by scraping. 

The most important: 

"Reuters analyzed 5,029 posts from a five-year period on one Internet message board, a Yahoo group. On average, a child was advertised for re-homing there once a week. Most of the children ranged in age from 6 to 14 and had been adopted from abroad – from countries such as Russia and China, Ethiopia and Ukraine. The youngest was 10 months old."

And it allowed us to build this interactive.

![Here's what you want.](../master/scraping16.jpg)

As you can see, scraping is an essential skill for reporters, no matter the beat. 

### What we're going to learn today

Lesson 1: DownloadThemAll, HTML tables into Excel

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


## HTML to Excel

The best way to get data is a nice, formatted dataset. An Excel sheet. A CSV. But, unfortunately for us, it isn't always that simple. 

Sometimes you see a table online that you want. For example, take a look at [this Wikipedia page](https://en.wikipedia.org/wiki/List_of_United_States_presidential_elections_by_popular_vote_margin)
on presidential election results. Or [this Wikipedia table](https://en.wikipedia.org/wiki/List_of_United_Kingdom_Parliament_constituencies) UK parliamentary constituencies. Today we're going to learn how to get those tables into a spreadsheet with little or no pain. 

To start, we are just going to worry about tables. Let's go back to that [Wikipedia page](https://en.wikipedia.org/wiki/List_of_United_Kingdom_Parliament_constituencies) of UK parliamentary constituencies. 

Like many data journalism problems, there's more than one way to tackle the problem. The important thing is to use a method in which you feel comfortable. 

## Basic import of HTML table using Excel

First, let's learn a very simple way to import it into Excel. 

Right click on the web page in Chrome and select "Save as..." We're going to save the page as HTML, so use the "Save as type" pulldown menu to select "Webpage, HTML only." 

Name it whatever you want and click "Save." 

![Here's what you want.](../master/scraping17.jpg)


So we've saved the HTML page to our hard drive. Now let's open Excel to a black worksheet. 

Click on the circle thingy in the top left and click "Open." Navigate to where you saved your HTML file. 


![Here's what you want.](../master/scraping18.jpg)


In the bottom left of the window, make sure you change from just looking for Excel files to "All Files *.*)". Select your HTML file. 


![Here's what you want.](../master/scraping19.jpg)


It might give you a window that looks like this --- click OK. 

![Here's what you want.](../master/scraping20.jpg)


You see a bunch of stuff that looks familiar from the Wikipedia web page. Scroll down until you see the table we're interested in. Great. But we're not done. 

Let's highlight the whole area of the table we want. Use CTRL-C to copy. 


![Here's what you want.](../master/scraping21.jpg)


Let's click on a new tab at the bottom of Excel and place your mouse in cell A1. Use CTRL-V to paste. 


![Here's what you want.](../master/scraping22.jpg)


At this point, I want to get rid of all the flashy HTML links and such. The way I do it is to save the file in some sort of text format, such as CSV or tab-delimited. For this class, let's all save as CSV. 

To do this, go back to that little circle thingy in the upper left-hand corner of Excel. Click on "Save as" again, but this type select 
"Other formats."


![Here's what you want.](../master/scraping23.jpg)


Then choose "CSV (comma-delimited)(\*.csv)." Click save. 


![Here's what you want.](../master/scraping24.jpg)


OK. Exit out of that and open a fresh new blank spreadsheet. 

Now go to the Data tab in Excel. Select "From text" and then navigate to your file. 


![Here's what you want.](../master/scraping25.jpg)


Now you'll choose delimited. Click next. 


![Here's what you want.](../master/scraping25.jpg)


Change the delimiters to comma. Click next.


![Here's what you want.](../master/scraping26.jpg)


For now, we don't have to worry about what's on the next screen. Click finish. 


Voila! Doesn't that look a lot cleaner?


![Here's what you want.](../master/scraping27.jpg)


Now to truly make it usable, you'd want to clean up the header row. 



## Importing an HTML table or list using Google Sheets. 

That took quite a few steps, huh? Well, there's an easier way. 


### First a little about HTML

Underneath what you see in your web browser is a bunch of code, known as HTML (Hypertext Markup Language). It's outside the scope of this course to go deep into HTML (but there are ton of [tutorials](https://www.w3schools.com/html/) out there), but we do need to know a little.

To see what it looks like in the wild, let's open up Chrome and go to [this Wikipedia page](https://en.wikipedia.org/wiki/List_of_United_Kingdom_Parliament_constituencies). Right-click and select "View Page Source."

HTML uses tags that look something like:

```HTML
<table>Scraping skills table</table>.
```

That creates a table. 

Let's take a look at [this page together](https://www.w3schools.com/html/html_tables.asp) to see how tables work. 

The other thing we need to know about are lists. 

Again, let's [take a look at this page](https://www.w3schools.com/html/html_lists.asp) together to see how lists work. 



So when we learned to import HTML tables into Excel, it took a lot of steps, right? But there's something simpler: Google Sheets. 

With the use of just a single function, you can bring the same table into Google Sheets. It's really simple. 

```
=ImportHTML("url","element", "number of element")
```

It's pretty self-explanatory, right? The first argument, "url", is the web address. 

The second argument, "element", is either "table" or "list". We're going to use "table" for this exercise.

The third argument is the number of of the element (the list or the table). The numbers start at 0, not 1.  

So let's give it a try. Open up Google Sheets and get a nice, blank worksheet. 

In cell A1, type this:

```
=ImportHTML("https://en.wikipedia.org/wiki/List_of_United_Kingdom_Parliament_constituencies", "table", "0")
```

Nope. Let's try again. 

```
=ImportHTML("https://en.wikipedia.org/wiki/List_of_United_Kingdom_Parliament_constituencies", "table", "1")
```

Still not right. Maybe the third time is the charm. 

```
=ImportHTML("https://en.wikipedia.org/wiki/List_of_United_Kingdom_Parliament_constituencies", "table", "2")
```

Wow. Look at that. Easy right?




