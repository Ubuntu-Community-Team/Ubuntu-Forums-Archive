---
title: "bash redirection"
date: 2007-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-11-23
what does this mean?

> Valid redirection targets and sources

This syntax is recognized whenever a TARGET or a SOURCE specification (like below in the details descriptions) is used.

Syntax	Description
&-	closes the redirected filedescriptor, useful instead of > /dev/null constructs (> &-)

from this website.

[http://bash-hackers.org/wiki/doku.php?id=syntax:redirection](http://bash-hackers.org/wiki/doku.php?id=syntax:redirection)

---

### Post by jpkotta on 2007-11-24
Usually to suppress output, you redirect to /dev/null, the black hole of Unix.  So instead you could just close the stream, which is what "&-" purportedly does.  Only it doesn't work for me.  Even if it did, I would still use ">/dev/null" because it's more standard.  I've never heard of this "&-" before, and neither has the Bash man page.

---

