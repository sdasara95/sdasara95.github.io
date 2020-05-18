---
layout: post
title: Curious case of recursion
subtitle: Trying to understand this beautiful concept
gh-repo: sdasara95/
gh-badge: [follow]
tags: [recursion, dp]
comments: true
---
Recursion has always been a tough concept to wrap my head around.  My main flaw in trying to understand it was not visualising it as a ***tree unrolling***. Maybe my obsession with imperative programming paradigm could be to blame for this.  Ever since I started to visualise recursion as a ***method*** to ***brute-force*** the ***search space*** using ***clones***, I have been able to write recursive code better. <br />
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

### Exponential problem 
***base<sup>exp</sup> = base * base<sup>exp-1</sup>***  <br />
Python code to achieve this would be: <br />
```python
def exp(base,power):
  if power==0:
    return 1
  return base * exp(base,power-1)
```
How many recursive cases will be called before base case? <br >
There'll be ***power*** number of recursive calls. Let's say time complexity is ***O(N)*** <br >
Can we make it more efficient? <br />
🤔 Well yeah, there's a way. Consider this property: <br />
***base<sup>exp</sup> = base<sup>exp/2</sup> * base<sup>exp/2</sup>***  <br />
Now a question might arise....what about ***odd powers***? <br />
Well....for ***odd powers*** it'll be something like this: <br />
***base<sup>exp</sup> = base * base<sup>exp/2</sup> * base<sup>exp/2</sup>***  <br />
*Remember that we are considering absolute division of the powers here* <br />
Python code to achieve this would be: <br />
```python
def exp(base,power):
  if power==0:
    return 1
  val = exp(base,power/2)
  if power%2==0:
    return val*val
  else:
    return val*val*base
```
If you're a bit confused about this, then think of it as you are ***decomposing for even power always*** <br />
***base<sup>5</sup> = base<sup>4</sup> * base*** <br />
Hence, if odd multiply with an additional base. <br />
This algorithm will be faster with a time complexity of ***O(log N)*** <br />
<br />
Julie cautions against ***arm's length recursion***. <br /> 
An example would be: <br />
```python
def exp(base,power):
  if power==0:
    return 1
  if power==1:
    return base
  return base* exp(base,power-1)
```
* Aim for ***simple and clean base case***
  * Don't anticipate ***earlier stopping points***
  * Avoid looking ahead before recursive calls, ***let simple base case handle***

***Just let the code fall through*** <br />

All recursive problems have a pattern. Our goal should be to find that pattern and use clones to solve the problem. <br />

### Palindrome Problem
The pattern of a palindrome is that if first and last letters match then it's a palindrome if the inner substring is also a palindrome. <br />
If we consider a word like **sasas**. <br />
s [asa] s <br />
 a [s] a  <br />
Our base case would be if we were left with one or none character. <br />
Python code for this would be:
```python
def palindrome(string):
  if len(string)<=1:
    return True
  if string[0]==string[-1]:
    return palindrome(string[1:-1]
  else:
    return False
```
One way of formulating a recursive solution is to get a base case and test it, then consider one layer out( one recursive call out ). <br />
You can think as it works for 0, it works for 1, it works for 2, ***take a leap of faith*** ,it works for n, it works for n+1. <br />
This idea is very similar to bottom-up dynamic programming. <br />

### Binary Search
This classic decrease and conquer problem can be solved both iteratively and recursively. However recursive solutions are always elegant and short pieces of code. <br />
Python code for this would be: <br>
```python
n = len(array)
def binary_search(array,key,start=0,end=n):
  mid = (start+end)//2
  if array[mid]==key:
    return True
  if start>end:
    return False
  if mid>key:
    binary_search(array,key,start,mid)
  else:
    binary_search(array,key,mid+1,end)
```
Some may get confused with the following base-case: <br>
```python
if start>end:
    return False
```
When the key **is not** present in the array, we will reach a stage where start=n and end = n+1. In such a case, mid = n. This will make our new start = n+1 and end = n+1 reamains same. This time our mid=n+1 and new start = n+2 but end remains n+1. Hence, the base case gets triggered. <br>




