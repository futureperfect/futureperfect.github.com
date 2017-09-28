---
title: First Elixir Open Source Contribution
layout: post
tags: [til]
---

Today my first open source contribution
to an [Elixir](http://elixir-lang.org) project was released! 
[Tentacat](https://github.com/edgurgel/tentacat), a library for interacting with
the [GitHub](https://github.com) REST API now supports [requesting the latest
release for a
repository](https://github.com/edgurgel/tentacat/releases/tag/v0.6.0).

I learned a number of things in the process, including translating techniques for
testable API interactions for verifying clients. In short `exvcr` is a library
patterned after the VCR rubygem allowing recording and replaying of API
interactions for the purpose of testing. API replay has its issues around not
catching API contract changes, but it is a nice way for a library maintainer to
begin to verify contract adherence coupled with a stable API or further
integration testing.
