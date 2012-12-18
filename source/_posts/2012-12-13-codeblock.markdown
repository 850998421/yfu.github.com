---
layout: post
title: "Codeblock"
date: 2012-12-13 23:44
comments: true
categories: 
---

This plugin seems to be very useful for sharing code, so let me test it.

Example 1

{% codeblock %}
Super awesome code snippet
{% endcodeblock %}

Example 2
{% codeblock lang:python %}
for i in range(1,10):
    print i
{% endcodeblock %}

<!--more-->

Example 3

{% codeblock Time to be Awesome - awesome.rb %}
puts "Awesome!" unless lame
{% endcodeblock %}

Example 4 (Force Highlighting)

{% codeblock Here's an example .py file lang:python %}
a = 1
{% endcodeblock %}

