---
layout: post
title: Atari 2600 Sketches No. 1
tags: [atari]
---

![Incrementing the PF1 playfield register]({{ site.url}}/assets/playfield-graphics-demo.gif)

Drawing graphics on the Atari 2600 is something of a production compared to more
modern computing platforms. The hardware has no framebuffer to speak of, no video
RAM at all, and only 128 _bytes_ of RAM.

The image above is from a program created to demonstrate a hardware feature
designed as a solution for the limited graphics task of drawing backgrounds -- 
playfield graphics. By writing a particular pattern of ones and zeros to three
playfield registers `PF0`, `PF1`, and `PF2` which mapped to the Television 
Interface Adapter (TIA), making it relatively striaghtforward to draw simple
patterns to the screen.

For the purposes of demonstration, `PF1` has its contents incremented by one
every 20 frames. Notice the pattern of vertical red stripes changing like the
ones in a binary number incrementing upward.

With a bit of cleverness and careful timing, the playfield graphics can be used
to draw surprisingly sophisticated items in the scene. For a more complete
treatment of the capabilities of the TIA chip and playfield graphics, the 
[2600 (Stella) Programming Guide](https://archive.org/details/StellaProgrammersGuide)
is the Atari documentation of record. It's been helpfully adapted to HTML
[here](https://alienbill.com/2600/101/docs/stella.html).
