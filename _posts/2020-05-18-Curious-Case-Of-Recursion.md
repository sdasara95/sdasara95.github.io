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
> Recursive function calls itself....duh 🤷‍♂️ <br />
> Solve problems using co-workers or **CLONES** 🔑 <br />
> For problems which exhibit **Self-Similarity** 👈 <br />
We spawn **smaller instances** of the **same function** doing the **same task** on **smaller input**. <br />
{% include youtube-embed.html id="gl3emqCuueQ" %} 
<br />
> Recursive function calls itself....duh 🤷‍♂️ <br />
> Solve problems using co-workers or **CLONES** 🔑 <br />
> For problems which exhibit **Self-Similarity** 👈 <br />
We spawn **smaller instances** of the **same function** doing the **same task** on **smaller input**. <br />

