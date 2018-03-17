---
layout: post
title: PICO-8 Sketches No. 1
tags: [pico8]
---

![Diffusion Limited Aggregation]({{ site.url }}/assets/dla-demo.gif)

[Source Code on GitHub](https://github.com/futureperfect/pico8-demos)

[PICO-8](https://www.lexaloffle.com/pico-8.php) bills itself as a "fantasy
console", a modern implementation of a microcomputer like the [BBC
Micro](https://en.wikipedia.org/wiki/BBC_Micro) or the [ZX
Spectrum](https://en.wikipedia.org/wiki/ZX_Spectrum) affording many of the
interesting design constraints of these microcomputer like limited screen
resolution, tiny program size, and sprite-based graphics but with the benefit
of being programmable with a subset of a modern high-level language, [Lua](https://www.lua.org).

The above animation is a demo I put together in about an hour modeling
Diffusion-limited Aggregation. This [short course on
simulation](https://n-e-r-v-o-u-s.com/education/simulation/week1.php) was
helpful to getting a grounding in the topic. I was initially inspired by a
beautiful low-resolution Mandelbrot set visualizer that ships with PICO-8 as a
demo program. DLA-based visualizations can be quite beautiful, but some of that
dendritic beauty seems to be lost in a 128x128 screen.

Something interesting to note is that even with this incredibly small demo, the
computational complexity of doing a naïve collision detection algorithm between
particles and the aggregate makes
for a choppy rendering experience as aggregated particles accumulate. The linked "Simulation and Nature in Design"
course hints at a number of straightforward methods for addressing this -- I
suspect something as basic as keeping track of a bounding box around the central
aggregate and only testing for collisions if inside the box would go a
long way to improving the framerate. You could get more sophisticated and keep a
Binary Space Partition data structure, but that feels a bit sophisticated for
something with a LoFi aesthetic.


