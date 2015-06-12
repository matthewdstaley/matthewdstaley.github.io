---
layout: post
title:  "Project Euler Codes"
date:   2015-06-11 01:03:32
categories: jekyll update
---

With my background in math, and recently learning to code in python, projecteuler.net has been a great way for me to do math in a modern way. My user name is group_theory. Feel free to email me with comments or suggestions. This page will be updated as new solutions are created.



<h2> Problem 1 </h2>
<h1> Find the sum of all the multiples of 3 or 5 below 1000. </h1>

{% highlight ruby %}
one = []
for n in range(1,1000):
    if n % 3 == 0:
        one.append(n)
    if n % 5 == 0:
        one.append(n)
    if n % 5 == 0 and n % 3 == 0:
        one.remove(n)
sum(one)

233168
{% endhighlight %}


<h2> Problem 2 </h2>
<h1> By considering the terms in the Fibonacci sequence whose values do not exceed four million, find the sum of the even-valued terms. </h1>

{% highlight ruby %}
g = [1, 2]
​
for k in range (2,50):
    n = g[k-2] + g[k-1]
    g.append(n)
​
even = []
for x in g:
    if x < 4000000 and x % 2 == 0:
        even.append(x)
​
sum(even)
​
4613732
{% endhighlight %}