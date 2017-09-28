---
title: Text Expansion
layout: post
tags: [til]
---

When translating from one language to another, the amount of text
required to represent the same idea will expand or contract
depending on the language. This idea is referred to in internationalization work
as "text expansion".

Languages like English and Chinese tend to be written in very compactly, while
languages like German and Italian can expand to a surprising degree -- 2-3 times
by some measures.

One way to account for this during development is generate a pseudo-translation
of your source language where strings have been padded out to expand as much as
the largest language you expect to internationalize into.

So translation files like

```
---
en:
  model:
    key: Click to Login
```

becomes


```
---
es:
  model:
    key: '[~~~~~ Click to Login]'
```


For more on text expansion,
[this W3C article](https://www.w3.org/International/articles/article-text-size)
is a good introduction for how to account for this phenomenon and how it affects
various aspects of user interface design.
