---
layout: post
title:  "Background Information"
date:   2015-12-03 14:19:00
categories: bg-info update
---

There are a few things that need explanation. It would probably be best to
start from a brief example of the basics, then build up to the more complicated
topics (more or less).

## Boolean Logic

The simplest information that we have stems from boolean logic. Where we have
information that is simply either <tt>on</tt> or <tt>off</tt>. There are a 
couple of ways of describing these, I plan on always referring to <tt>on</tt> 
as <tt>1</tt> and off as <tt>0</tt>.  It'll tie back well into the way computers 
work, if we ever go into the way the hardware itself works.

### More than <tt>1</tt>s and <tt>0</tt>s

There's very little we can do with just a <tt>1</tt> and a <tt>0</tt>. So, we 
need to delve into **Boolean Formulas**. 

We can build off of the <tt>0</tt> and <tt>1</tt> to define

Boolean Variables
: Will be denoted by a capital letter <tt>X</tt>.

Then, we have the <tt>!X</tt> operation, which simply works as taking the 
opposite value of <tt>X</tt>. It works as follows:

| <tt>X</tt> | <tt>!X</tt> |
|-----+------|
|  0  |  1   |
|  1  |  0   |

We have operations on multiple boolean variables as well. There are many ways
to write the operations, but they are simple referred to as <tt>AND</tt>, 
<tt>OR</tt>, <tt>XOR</tt>.  There are others, build off of these, however these 
will define most of the uses we need. we can write all of these in multiple 
ways, such as

| <tt>AND</tt> | <tt>OR</tt> | <tt>XOR</tt> |
|-------+------+-------|
| $$\wedge$$ | $$\vee$$ | $$\oplus$$ |

