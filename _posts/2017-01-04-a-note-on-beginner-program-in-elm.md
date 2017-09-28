---
title: A Note on `beginnerProgram` in Elm
layout: post
tags: [til]
---

[Elm](http://elm-lang.org) is a functional programming language designed
designed to compile to JavaScript. It has made something of a name for itself
with high quality compiler error messages and excellent documentation.

One thing you may encounter in your initial reading of example applications is
an entity called `beginnerProgram`, for example:

```elm
import Html exposing (beginnerProgram, div, button, text)
import Html.Events exposing (onClick)

main =
  beginnerProgram { model = 0, view = view, update = update }
```

It may be the peculiarity of how it is named, but `beginnerProgram` seems to confuse
programmers new to Elm's syntax as to what it is -- [a function imported from the `Html`
package](http://package.elm-lang.org/packages/elm-lang/html/latest/Html#beginnerProgram).
Think of it as a convenience method for defining a root `Program` without having
to define [some of the more sophisticated elements Elm affords](http://package.elm-lang.org/packages/elm-lang/html/latest/Html#program).
`beginnerProgram` only requires defining a `model`, `view`, and `update` function,
the kernel of any application using the Elm architecture.

