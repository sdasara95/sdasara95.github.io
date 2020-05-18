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
[Julie Zelenski's](https://www-cs-faculty.stanford.edu/~zelenski/) Stanford Lectures do an amazing job of making you understand recursion. Her [Programming Abstractions Course (CS106B)](http://web.stanford.edu/class/cs106b/) is an amazing place to start for those struggling with recursion or computer science fundamentals in general. Her lectures are quite engaging and she succintly explains the core concepts. The videos are available on [YouTube](https://www.youtube.com/watch?v=kMzH3tfP6f8). She explains recursion in ***videos 8-11***. <br />
<br />
This blog shall go through each of her recursion videos and ***summarize*** the ***core ideas***.

# Introduction
{% include youtube-embed.html id="gl3emqCuueQ" %} 
### What's recursion?

* Recursive functions call themselves....duh 🤷‍♂️ <br />
* Solve problems using co-workers or **CLONES** 🔑 <br />
* For problems which exhibit **Self-Similarity** 👈 <br />

We spawn ***smaller instances*** of the ***same function*** doing the ***same task*** on ***smaller input/ problem***. <br />
***Base Case*** is when the ***input/problem*** is ***so small*** that we ***don't need*** another task repeating ***clone*** <br />
<br />

She then goes on to define ***Functional Recursion*** 
* Function that returns answer or result
  * Outer problem result ⬅ Result from smaller same problem
* Base case
  * Simplest version of problem
  * Can be ***directly solved***
* Recursive case
  * Make ***call to self*** to get ***results for smaller, simpler version***
  * ***Recursive calls must advance towards base case***
  * Results of recursive calls combined to solve larger version
  
**Exponential problem** </br>
***base<sup>exp</sup> = base * base<sup>exp-1</sup>***  <br />
Python code to achieve this would be: <br />
```
def exp(base,power):
  if power==0:
    return 1
  return base * exp(base,power-1)
```


