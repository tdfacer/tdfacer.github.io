---
layout: post
title:  "python comparison"
date:   2022-06-20 08:36:21 -0600
categories: tech python
tags: tech python
author: Trevor Facer
---

## `==` / `!=` vs. `is` / `is not`


### ==

* Equality operator
* Compares values of lhs and rhs

### is

* Identity operator
* Compares by reference (same value in memory)
* Checks whether two references point to the same object, i.e., they point to the same memory address
* Syntactic sugar for `id(a) == id(b)`
