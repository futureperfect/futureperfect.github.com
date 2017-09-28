---
title: Netcat Talks UDP
layout: post
tags: [til]
---

Netcat is something of a Swiss Army knife of a networking tool -- it's
remarkably handy for doing things like creating minimal TCP clients and servers
for development purposes. What I didn't realize was that `netcat` can *also*
communicate via UDP. To, for example, send a UDP message to a server listening
for UDP traffic on port 3333,
you could run:

```
$ echo "This is a UDP message" | nc -cu 127.0.0.1 3333
```

This will send "This is a UDP message" over UDP and include a CRLF line-ending.
This has been particularly handy as a quick way to interact with UDP services.
