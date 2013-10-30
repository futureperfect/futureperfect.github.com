---
layout: post
title: Example custom UIGestureRecognizers for iOS
tags:
- iOS
- gesture
---
I noticed a number of posts on StackOverflow about people having
problems writing their own UIGestureRecognizers for iOS. In
particular, recognizing continuous gestures seemed to be an issue.

With that in mind, I decided to write a custom UIGestureRecognizer
which recognizes continuous press-drag gestures and release it under a
BSD license for the learning benefit of others.

The included project has an interface which on detecting a press-drag
gesture, drops a red dot on the site of the press and updates the
radius of a blue circle to coincide with where your finger is dragged
to.

[The PressDrag project page is available here](https://github.com/futureperfect/PressDrag). Have at it and feel free to fork it and
send a pull request if you improve on it.
