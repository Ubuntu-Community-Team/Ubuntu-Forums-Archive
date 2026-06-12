---
title: "acrocread not working suddenly"
date: 2007-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Undertwotimes on 2007-05-25
I'm pretty sure acrocread was working before I updated today, but now when I run it it spits out a infinite loop of this error:  (note that this is run without opening any document).

expr: syntax error
expr: syntax error
expr: syntax error
expr: syntax error
expr: syntax error
expr: syntax error


wtf?

---

### Post by quark_77 on 2007-06-05
Hi Undertwotimes,

I had the same problem, I think I updated glibc. The quick and easy answer is adobe's shell script is rubbish. 

There are two solutions, one less neat, the other better.
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=449096](http://ubuntuforums.org/showthread.php?t=449096) the first one, not so neat but does the trick
[*]La deuxième, en français: [http://remi.collet.free.fr/index.php?2007/01/10/273-acrobat-reader-709-et-fedora-core-6](http://remi.collet.free.fr/index.php?2007/01/10/273-acrobat-reader-709-et-fedora-core-6)
[/LIST]

The second one is in french but even if you can't follow the language you'll understand the commands easily enough, basically patch the acroread shell script. I've just tried it on Feisty, no problems here.

Hope this helps, no idea why it's broken (suspect glibc, underlying gtk stuff) but it can be fixed.

Quark_77

---

