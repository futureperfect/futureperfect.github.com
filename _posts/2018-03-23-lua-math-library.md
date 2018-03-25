---
layout: post
title: "`lmathlib.c`: Lua Math Library"
tags: lua tour
category: lua-tour
---

The entirety of the math library for lua exists within `lmathlib.c`.

The bulk of the math library is implemented by direct mapping to the underlying math.h lib provided by libC implementation.

The syntax for providing that mapping was a little strange at first. First question was "what is a lua_State *L that all of these functions take?

lua_State is a struct defined in `lstate.h`. It represents the state for a lua thread, including (importantly for this case) the stack for the thread. This is where arguments for each of the implemented lua functions are derived from and saved to after execution.

At the end of the package, there's the first instance observed of a pattern for cataloging the provided functions and then registering them with the lua runtime:

A list of structs is explicitly created mapping function names to function implementations. This array is then passed to the `luaL_register` function when initializing the library to register all of the defined functions.

The pattern for handling args seems to be to defensively check that arguments are in fact numeric prior to evaluation and to push results to the top of the stack. I discovered in testing that lua will coerce string arguments into numbers in at least some cases. to wit:

```
> math.pow(2, 3)
8.0
> math.sin("1")
0.8414709848079
> math.sin("cat")
stdin:1: bad argument #1 to 'sin' (number expected, got string)
stack traceback:
	[C]: in function 'math.sin'
	stdin:1: in main chunk
	[C]: in ?

```

Useful numbers like Pi and Infinity are also registered at this time (math.pi and math.huge, respectively).

Also of note in the 5.1.5 source is that backfills for older versions of modular arithmetic are also provided conditionally by using a #define'd flag `LUA_COMPAT_MOD`. I would guess this pattern will come up again. 

