---
layout: post
title: Data Science with Functional JavaScript
description: "Part 1 - Data Wrangling"
headline: "Data Wrangling using Chromes Dev Tools"
categories: JavaScript
tags: 
  - data wrangling
  - js
  - data science
comments: false
mathjax: true
featured: true
published: true
david: true
iris: false
---

Chrome's developer tools and JavaScript make it easy to scrape data from web pages. I'll demonstrate this by grabbing a list of [ISO country codes, country names and country ids](http://en.wikipedia.org/wiki/ISO_3166-1) from Wikipedia.

## Console Basics

Before we begin, some general tips with working with the console (OSX):

- Press up and down to navigate command history. This is great for iteratively building up a pipeline
- Press alt and left and right to skip forwards/backwards one word
- Cmd + k to clear the console
- Ctrl + e to skip to end, Ctrl + a to skip to the start
- Ctrl + enter to add a new line without running the current command

## Getting the Data 

First off, we want to find the element that contains our data. Using the elements panel and right click -> 'Inspect element', we highlight the element containing our data.

![Inspect Chrome Dev Tool]({{ site.url }}/images/inspect.png)

## Moving to the Console

Next we move to the console. Chrome places the element you inspected most recently in the `$0` variable, the next most recent on `$1` and so on. It also aliases querySelectorAll as `$$(css [,startNode])`, so we can use these together to check out the rows in our table:

{% highlight javascript %}
> $$("tr",$0)[0].innerHTML
"<td><a href="/wiki/Afghanistan" title="Afghanistan">Afghanistan</a></td>
<td><a href="/wiki/ISO_3166-1_alpha-2#AF" title="ISO 3166-1 alpha-2"><tt>AF</tt></a></td>
<td><tt>AFG</tt></td>
<td><tt>004</tt></td>
<td><a href="/wiki/ISO_3166-2:AF" title="ISO 3166-2:AF">ISO 3166-2:AF</a></td>"
{% endhighlight %}

Great! Looks like some useful data in that HTML. I normally slap [0] at the end of the pipeline to get this insight into what's being produced.

To grab the data from the HTML in another one-liner we can use one of the Array additions - map. Unforunately `$$` returns a NodeList which is array-like but not an array. To work around this we grab `[].map` and `.call` it on the node list.

{% highlight javascript %}
> [].map.call($$("tr",$0),mapper)[0]
{% endhighlight %}

We'll need to define mapper() - a function that takes each element in turn and returns the data we want as a structured object. In this case we want the contents of the 1st and 2nd nodes, so:

{% highlight javascript %}
> function mapper(el) {
    return {
      country: $("td",el)[0].innerText,
      code: $("td",el)[1].innerText,
      id: $("td",el)[3].innerText
    }
  }
> [].map.call($$("tr",$0),mapper)[0]
Object {country: "Afghanistan", code: "AF", id: "004"}
{% endhighlight %}

Excellent - just what we want. Now we have an array full of tasty data, but how do we get it out?

Chrome saves the day again with `copy()`, giving us the data-clipboard bridge we've always wanted. Since we want useful data we'll `JSON.stringify` the data first, and our completed pipeline looks like:

{% highlight javascript %}
> var data = [].map.call($$("tr",$0),mapper);
> copy(JSON.stringify(data))
{% endhighlight %}

What does our final data look like?

{% highlight javascript %}
[{"country":"Afghanistan","code":"AF","id":"004"},{"country":"Åland Islands","code":"AX",id:"..."},/* ... */,{"country":"Zimbabwe","code":"ZW","id":"..."}]
Here's the whole pipeline built up bit by bit
{% endhighlight %}

{% highlight javascript %}
> var nodes = $$("tr",$0);
> function mapper(el) {
    return {
      country: $("tr",el)[0].innerText,
      code: $("tr",el)[1].innerText,
      id: $("tr",el)[3].innerText    
      }
  }
> var data = [].map.call(nodes,mapper)
> copy(JSON.stringify(data))
{% endhighlight %}

That's it. Pretty sweet right? In the following, I will dig deeper into `map` and `reduce` in JavaScript.