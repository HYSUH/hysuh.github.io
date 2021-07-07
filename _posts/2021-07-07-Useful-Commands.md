---
layout: post
title: "Useful commands"
author: YS
tags: unix, productivity
---

The following are some of the commands that have increased my productivity and made my life so much easier

- Finding all files within a directory matching a pattern

```
The following lists the names of all the python files that has the keyword exception in it
find . -name "*.py" -exec grep -l "Exception" '{}' \;
```

- Navigating forwards/backwords by word on the command line

```
Option + right arrow: move right by one word
Option + left arraw: mov eleft by one work
```

- Navigating to the beginning/end of a command on the command line

```
Ctl + A: Move cursor to the beginning
Ctl + E: Move cursor to the end
```

- [Fuzzy Finder](https://github.com/junegunn/fzf)

fzf is an amazing tool to search through your command history and helps you search and rerun commands that you have run before

![fzf serach]({{ site.url }}/assets/fzf.png)