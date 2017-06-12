# Scraping Data from the Web 2: Going farther

## The importXML function in Google Sheets

There's another option you can use when scraping websites. It gives you the ability to be a little more precise, but also requires a little more effort. 

It's called importXML and it looks almost the same as importHTML, but with two arguments instead of three:

```
=importXML("yourwebsite","your xpath")
```

OK. So what is XPath?

XPath is an expression that allows you to point toward things, or groups of things on a web site. Getting too deep into XPath will take us down a rabbit hole. If you want to learn more, you can start somewhere like this [web site](https://www.webperformance.com/load-testing-tools/blog/real-browser-manual/building-a-testcase/how-locate-element-the-page/xpath-locator-examples/).

Luckily, your Chrome browser provides a pretty good way of figuring out the XPath of an element without much work. 

You're interested in keeping an eye on currency rates. My employer, Thomson Reuters, has a table of some selected exchange rates [on this website](http://www.reuters.com/finance/currencies).

Let's say we're only interested in how the Yankee Dollar compares to the Japanese Yen and the Australian Dollar.

Right click anywhere on the page and select "Inspect Element."



![Here's what you want.](../master/scraping7.jpg)



Click on the selector in the developer tools window. 



![Here's what you want.](../master/scraping8.jpg)



Now take the selector and click on the USD/JPY text. 



![Here's what you want.](../master/scraping9.jpg)



Notice how it also highlights the code in the HTML. You can then take your mouse and highlight different pieces of code in the HTML to navigate around the table. To help you out:

The <TR> tags refer to table rows. So each TR is a row in the table. Let's highlight the <TR> code that highlights the USD/JPY row. 

Then right click on the <TR> code you want, then choose COPY and COPY XPATH. 



![Here's what you want.](../master/scraping10.jpg)



OK. Now let's go to a blank Google Sheets document. Enter your XPATH code in one cell and the website address in another. 



![Here's what you want.](../master/scraping11.jpg)



Now in another cell, (using my example as a guide) type this: 

```
=importXML(B1, B2)
```

Wow. Pretty cool huh? You should have a screen that looks like this. 


![Here's what you want.](../master/scraping12.jpg)


OK. Let's repeat that step and do the US dollar/Aussie dollar row. 


![Here's what you want.](../master/scraping13.jpg)


## Now you try

Next, use =importXML and XPATH to extract the following fields from the following [market indices found here](http://www.reuters.com/finance/markets/us). 

![Here's what you want.](../master/scraping15.jpg)


## Scraping with import.io

OK, let's be sports writers now. 

