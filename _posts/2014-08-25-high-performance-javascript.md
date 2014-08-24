---
layout: post
title: Notes on High-Performance JavaScript
description: "Benchmarking, NodeJS and V8"
headline: 
categories: JavaScript
tags: 
- JavaScript
- V8
- Node
comments: false
mathjax: true
featured: true
published: true
david: true
iris: false
---

High-Performance JavaScript? Can JavaScript compete or even be faster than C?
This post is inspired by reading Felix Geisendörfer's [Post](https://github.com/felixge/faster-than-c).
First we will discuss about methods finding out, how to test the performance of your code in general:

## Profiling and Benchmarking
Profiling is useful, when you consider a functional approach in JavaScript.
Node allows you to inspect the speed of your program by using 

{% highlight javascript %}
node --prof 
{% endhighlight %}

which creates a V8.log.
It will show you how long a specific function needs in your program. Perfect to fix bottlenecks.
However this approach has some issues - As mentioned, it won't help much, if you decide a more infunctional javascript approach and put everything in one function.

## Benchmark Driven Development
Benchmarks are the oldest and still best way to test for speed.

{% highlight javascript %}
while (true) {
	var start = Date.now();
	function_to_test();
	var duration = Date.now() - start;
	console.log(duration);
}
{% endhighlight %}

## V8 - the magic machine
Node is build on basis of V8. V8 is Chrome and Google's Magic JavaScript Engine.
Speaking, it converts JavaScript insanely fast into assembly (machine code)
V8 is written in C++ and I will go into V8 into detail in the next post :)

