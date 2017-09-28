---
title: Output External Command to Vim Window
layout: post
tags: [til]
---

The `:!` command is a useful way to run external shell commands without leaving
vim. It's handy for doing things like invoking one-off commands or tasks. What I
didn't realize until today was that you could trivially paste the output of a
shell command back into the current window's buffer, using `:.!` instead.

```shell
# What's today's date?
:.!date -u
Thu Aug  2 00:51:13 UTC 2017

# What is my machine's name?
:.!uname -m
carbon.local
```

It's a small difference, but a nice improvement to my vim workflow. I hope you
find it useful as well.
