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
information that is simply either `on` or `off`. There are a 
couple of ways of describing these, I plan on always referring to `on` 
as `1` and off as `0`.  It'll tie back well into the way computers 
work, if we ever go into the way the hardware itself works.

### More than `1`s and `0`s

There's very little we can do with just a `1` and a `0`. So, we 
need to delve into **Boolean Formulas**. 

We can build off of the `0` and `1` to define

Boolean Variables
: Will be denoted by a capital letter `X`.

Then, we have the `!X` operation, which simply works as taking the 
opposite value of `X`. It works as follows:

| `X` | `!X` |
|-----+------|
|  0  |  1   |
|  1  |  0   |

We have operations on multiple boolean variables as well. There are many ways
to write the operations, but they are simple referred to as `AND`, 
`OR`, `XOR`.  There are others, build off of these, however these 
will define most of the uses we need. We will stick with writing them as the
following:

| `AND`      | `OR`     | `XOR`      |
|------------+----------+------------|
| $$\wedge$$ | $$\vee$$ | $$\oplus$$ |

Using them, `AND` and `OR` are fairly self-explanatory. `XOR` means 
"exclusive or". This means that one has to be `0` and the other `1` in order
for the operation itself to be `1`.

| `X` | `Y` | `X` $$\wedge$$ `Y` | `X` $$\vee$$ `Y` | `X` $$\oplus$$ `Y` |
|-----+-----+--------------------+------------------+--------------------|
| 0   | 0   | 0                  | 0                | 0                  |
| 0   | 1   | 0                  | 1                | 1                  |
| 1   | 0   | 0                  | 1                | 1                  |
| 1   | 1   | 1                  | 1                | 0                  |

From this, we have

Boolean Formula
: A boolean variable, or a combination through an operation that get reduced 
  down to a `1` or `0`

These formulas are useful when building up to the advent of computers, as the
concept of working with these `1`s and `0`s was necessary to reach a type of
system. 