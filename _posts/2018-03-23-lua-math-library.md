---
layout: post
title: "`lmathlib.c`: Lua Math Library"
tags: lua tour
category: lua-tour
---

![Lua project logo](/assets/lua-logo.png)

[Lua Math Library Source](http://www.lua.org/source/5.1/lmathlib.c.html)


The Lua math library is largely self-contained to one ~200 SLOC file, 
[`lmathlib.c`](http://www.lua.org/source/5.1/lmathlib.c.html). It serves as a
straightforward introduction to how structure and present libraries in the
Lua runtime.

## How is Lua's math library implemented?

The bulk of the math library functionality is implemented by directly mapping C
functions from libC's `math.h` to corresponding Lua functions. For example:

```C
static int math_log10 (lua_State *L) {
  lua_pushnumber(L, log10(luaL_checknumber(L, 1)));
  return 1;
}
```

maps the libC math function for taking base 10 logarithms into a function
`math_log10` in the Lua runtime. The syntax for providing that mapping might
appear a little strange at first. For starters, what is the `lua_State`
parameter that appears throughout? What are `lua_pushnumber` and
`lua_checknumber`?

`lua_State` is defined in
[`lstate.h`](http://www.lua.org/source/5.1/lstate.h.html#lua_State).
It is a struct that represents the runtime state for a Lua thread, including 
(importantly in this case) the stack state for the thread. This is where
arguments for each of the implemented Lua functions are derived
from and saved to after execution.

## How is Lua's math library packaged?

At the end of the package, there's the first instance observed of a pattern for cataloging the provided functions and then registering them with the lua runtime:

A list of structs is explicitly created mapping function names to function implementations. This array is then passed to the `luaL_register` function when initializing the library to register all of the defined functions.

The pattern for handling args seems to be to defensively check that arguments
are in fact numeric prior to evaluation and to push results to the top of the
stack. I discovered in testing that lua will coerce string arguments into
numbers in at least some cases. to wit:

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

Useful numbers like Pi and Infinity are also registered at this time (math.pi
and math.huge, respectively).

Also of note in the 5.1.5 source is that backfills for older versions of modular
arithmetic are also provided conditionally by using a #define'd flag
`LUA_COMPAT_MOD`. I would guess this pattern will come up again. 

