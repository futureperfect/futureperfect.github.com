---
layout: post
title: Offline Ruby Documentation With ri
tags: [til]
---

`ri` is a useful documentation tool that ships with the ruby language. To use it
from the command line, type (for example) `ri ClassName` or `ri ClassName.method` and ri will
present documentation for the class or method you've requested. The docs for
`Socket.new`, for example:

```
= Socket.new

(from ruby core)
------------------------------------------------------------------------------
  Socket.new(domain, socktype [, protocol]) => socket

------------------------------------------------------------------------------

Creates a new socket object.

domain should be a communications domain such as: :INET, :INET6,
:UNIX, etc.

socktype should be a socket type such as: :STREAM, :DGRAM,
:RAW, etc.

protocol is optional and should be a protocol defined in the
domain. If protocol is not given, 0 is used internally.

  Socket.new(:INET, :STREAM) # TCP socket
  Socket.new(:INET, :DGRAM)  # UDP socket
  Socket.new(:UNIX, :STREAM) # UNIX stream socket
  Socket.new(:UNIX, :DGRAM)  # UNIX datagram socket

```

The man page for `ri` is worth a look as it documents a number of handy
different querying techniques that the tool affords for things like limiting
yourself to instance or class methods or partial method name lookup.
