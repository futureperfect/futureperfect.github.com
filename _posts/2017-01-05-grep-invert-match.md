---
title: Grep Invert Match
layout: post
tags: [til]
---

Grep is a powerful tool for searching files for text matching a pattern. Have you ever
thought to use it to search for lines that **do not** match a search pattern?
Grep can do that! Add the `--invert-match` flag, or `-v` for short.

```shell
~ % cat words.txt
art
article
cities
name
nonsense
part
tart
~ % grep art words.txt
art
article
part
tart
~ % grep art --invert-match words.txt
cities
name
nonsense
```

Now you can use grep to search for presence *or* absence of a search pattern.
