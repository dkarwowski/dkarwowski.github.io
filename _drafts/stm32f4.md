---
layout: post
title: "stm32f4"
category: stm32 rust
---

I recently found a blog post on working on [embedded in rust][], and spent a
good amount of time looking through [japaric's github][]. After all of that, I
decided a good way to spend (some) of the next month and a half to be writing
my own crate, for the [stm32f429i][] discovery board. I'll go over a bit of the
process here, from setting it up to getting my project running. A lot of it is
similar to [embedded in rust][], but I'll try to describe where I figure out
the different pieces of starting up that are necessary.

[embedded in rust]: http://blog.japaric.io/quickstart/
[japaric's github]: https://github.com/japaric/
[stm32f429i]: http://www.st.com/en/evaluation-tools/32f429idiscovery.html
