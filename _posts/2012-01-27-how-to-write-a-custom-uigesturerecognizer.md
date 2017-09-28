---
title: How to Write a Custom UIGestureRecognizer
layout: post
tags: [iOS, tutorial]
---

![Press Drag gesture recognizer]({{site.url}}/assets/press-drag.png)

Here's a custom UIGestureRecognizer I've written to demonstrate recognizing
continuous gestures.

It recognizes continuous press-drag gestures, a concept that is perhaps
under-documented in Apple's documentation.

The project includes an interface which on detecting a press-drag
gesture, drops a red dot on the site of the press and updates the
radius of a blue circle to coincide with where your finger is dragged
to.

[The PressDrag project page is available here](https://github.com/futureperfect/PressDrag).
Have at it and feel free to fork it and send a pull request if you improve on it.
