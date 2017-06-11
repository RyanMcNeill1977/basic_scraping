# Scraping Data from the Web 2: Going farther

So unfortunately, there's a number of steps involved in getting an HTML data into Excel. There's a few reasons why you might want to do it the way we just learned. But generally speaking, getting an HTML data into a spreadsheet is significantly easier using Google Sheets. Let's learn how. 


## Importing an HTML table using Google Sheets. 

So that's a lot of steps, right? For years, we had to do it that way. But now there's something simpler: Google Sheets. 

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



## The importXML function in Google Sheets

There's another option you can use when scraping websites. It gives you the ability to be a little more precise, but also requires a little more effort. 

It's called importXML and it looks almost the same as importHTML, but with two arguments instead of three:

```
=importXML("yourwebsite","your xpath")
```

OK. So what is XPath?

XPath is an expression that allows you to point toward things, or groups of things on a web site. Getting into XPath will take us down a rabbit hole. If you want to learn more, you can start somewhere like this [web site](https://www.webperformance.com/load-testing-tools/blog/real-browser-manual/building-a-testcase/how-locate-element-the-page/xpath-locator-examples/).

Luckily, your Chrome browser provides a pretty good way of figuring out the XPath of an element without much work. 

Go to Chrome's dropdown menu. Select "More tools" and then "Developer tools."

![Here's what you want.](../master/scraping7.jpg)
















## Now you try. 

Let's try two examples. 

Now you try scraping a table from a [Wikipedia page](https://en.wikipedia.org/wiki/United_States_presidential_election,_2016). Let's grab the electoral results found in this table: 

<screen shot here>

And grab the table from [this BLS site](https://www.bls.gov/news.release/archives/metro_05312017.htm). 




## The XML Miracle

I first learned this trick from Charlie Szymanski, a 





### Answers

Answer to Example 1: 

```
=ImportHTML("https://en.wikipedia.org/wiki/United_States_presidential_election,_2016", "table", "35")
```

Answer to Example 2: 

```
=ImportHTML("https://www.bls.gov/news.release/archives/metro_05312017.htm", "table", "1")
```



