---
layout: default
---

# Part 6: Getting help

There are a number of ways to get help or figure out how to do something new:
    
- Google it
- Stackoverflow
- Read the documentation (often surprisingly useful)
- Look at the source code (can be difficult, but sometimes needed)

Generally:

- If you don't know what tools you need, or what packages you need to use: **Google or Stackoverflow**
- If you are having trouble with code not working, an unusual error etc: **Google or Stackoverflow**
- If you want to know details about a specific package or function: **Documentation or source code.** Google or Stackoverflow if this doesn't help.

Being a proficient coder is not about knowing the details of every package, but rather knowing how to search for this information effectively...

# Extras

## Python Style Guide

The [Python Enhancement Proposal 8 (PEP 8)](https://www.python.org/dev/peps/pep-0008/) outlines coding conventions when it comes to writing Python code. While there are a lot of different ways that you could *technically* write valid Python code, enforcing consistency in coding style makes reading other people's code much easier. Plus it's one less thing for you to have to decide on as a programmer!

It is worth having a read through the PEP 8 document [here](https://www.python.org/dev/peps/pep-0008/) and absorbing what you can. While some of the guidelines may not make sense at this stage in your Python journey, others should be easy to implement immediately. For example, always use 4 spaces for indentation (A tab is bad. Two spaces is worse).

### Easter eggs...

Time for some Python Zen:

```python
import this
```

Python doesn't have braces to designate code blocks (instead using indentation). But will this always be the case?

```python
from __future__ import braces
```

And just run this one...

```python
import antigravity
```