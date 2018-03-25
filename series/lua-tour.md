---
layout: series
title: A Tour of Lua
category: lua-tour
---

![Lua project logo](/assets/lua-logo.png)

[Lua 5.1 Source Code](http://www.lua.org/versions.html#5.1)

This series is a reading through the Lua 5.1.5 code base. Each post covers a
different part of Lua, doing a deep dive along the way and highlighting notable
aspects of the project.

## Why Lua?

[Lua](http://www.lua.org) is a lightweight, embeddable scripting
language implemented in C. It is generally considered a "well-written" C project
and weighing in at fewer than 13k lines of code for version 5.1.5, it seemed 
like a small enough project to be able to read and understand completely.

It is also a non-trivial project in what it implements: a high performance,
multi-paradigm, dynamically-typed language interpreted as bytecode for a
virtual machine. 

## Posts

{% assign posts = site.categories[page.category]%}
{% for post in posts reversed %}

* [{{ post.title }}]({{ post.url | absolute_url }}) {{ post.date | date_to_long_string }}

{% endfor %}

