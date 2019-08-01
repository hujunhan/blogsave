---
title: Newline Characters
author: Junhan Hu
tags: [tips,cs]
mathjax: true
date: 2019-7-30 17:00:00
---

## Difference

`'\n'` writes a newline in UNIX

`'\r\n'`writes a newline in Windows

Why Windows use extra `‘\r’` to do this job? 

<!-- more -->

## EOL

Newline, also called `line ending`, `end of line`, `line break` is a control character in a specify **encoding** system.

This control character tell the text editor how to display the text.

In **ASCII**

* CR: Carriage Return `\r`
* LF: Linefeed `\n`
* CRLF: Carriage Return & Linefeed `\r\n`

Windows use CRLF to be backward compatible with MS-DOS for historical reason

## Conclusion

To use plain text in multiple platform, try to use `\n` 