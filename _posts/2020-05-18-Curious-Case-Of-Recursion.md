---
layout: post
title: Curious case of recursion
subtitle: Trying to understand this beautiful concept
gh-repo: sdasara95/
gh-badge: [follow]
tags: [recursion, dp]
comments: true
---
Recursion has always been a tough concept to wrap my head around.  My main flaw in trying to understand it was not visualising it as a ***tree unrolling***. Maybe my obsession with imperative programming paradigm could be to blame for this.  Ever since I started to visualise recursion as a ***method*** to ***brute-force*** the ***search space***, I have been able to write recursive code better. <br />
<br />
[Julie Zelenski's](https://www-cs-faculty.stanford.edu/~zelenski/) Stanford Lectures do an amazing job at making you understand recursion. Her [Programming Abstractions Course (CS106B)](http://web.stanford.edu/class/cs106b/) is an amazing place to start for those struggling with recursion. I like her teaching style, watching her feels like a fellow peer explaining a concept to you thereby, keeping you more engaged in her videos. <br />
<br />

<iframe width="560" height="315"
src="https://www.youtube.com/embed/gl3emqCuueQ" 
frameborder="0" 
allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" 
allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6EVs0BrG57I" frameborder="0" allowfullscreen></iframe>



This is a demo post to show you how to write blog posts with markdown.  I strongly encourage you to [take 5 minutes to learn how to write in markdown](https://markdowntutorial.com/) - it'll teach you how to transform regular text into bold/italics/headings/tables/etc.

**Here is some bold text**

## Here is a secondary heading

Here's a useless table:

| Number | Next number | Previous number |
| :------ |:--- | :--- |
| Five | Six | Four |
| Ten | Eleven | Nine |
| Seven | Eight | Six |
| Two | Three | One |


How about a yummy crepe?

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)

It can also be centered!

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg){: .mx-auto.d-block :}

Here's a code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.