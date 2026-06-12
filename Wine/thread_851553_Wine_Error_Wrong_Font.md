---
title: "Wine Error: Wrong Font"
date: 2008-07-06
forum: Wine
---

### Post by dserver on 2008-07-06
When I try to run a program with Wine it gives me the following error:
```
$ err:wineconsole:WCUSER_SetFont wrong font
err:wineconsole:WCUSER_SetFont wrong font
err:wineconsole:WCUSER_SetFont wrong font
err:wineconsole:WCUSER_SetFont wrong font
err:wineconsole:WCUSER_SetFont wrong font

```
I've copied all my fonts from my Windows installation and installed the msttcorefonts package but still no luck. Anyone know how to fix this? Thanks.

---

### Post by cogadh on 2008-07-06
It looks like you are trying to run a console (command line) program. If so, then the problem may just go away if you use the "wineconsole" command to run the app, instead of the normal "wine app.exe". If that doesn't correct the issue, it might help if we had some idea of what app you are trying to run. There may be an existing how-to that adresses this issue in Wine's AppDB or at some other source.

---

### Post by dserver on 2008-07-07
I will try this as soon as I get home from work. Thanks for the quick response.

---

### Post by jkr801 on 2008-07-07
dserver i am having the same problem did you make any headway??

---

### Post by dserver on 2008-07-07
Still doesn't work. For a description of the program I'm trying to run look here: [http://ubuntuforums.org/showthread.php?t=850784](http://ubuntuforums.org/showthread.php?t=850784)

I made two threads on it because I figured that someone who knows how to fix the wrong font error might not look into the Diablo II Maphack thread and I wanted to get maximum exposure.

---

