---
title: "Memory usage - metacity/gnome eating RAM..."
date: 2005-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by billybofh on 2005-12-20
Hi,

I've got a problem running with my AMD64.  Over time the RAM seems to slowly be eaten - largely by metacity as far as I can make out.  On my AMD64 machine running breezy metacity looks like this from top :

```
 4393 billy     15   0  239m  76m 4292 S  0.3 15.5  13:22.74 metacity
```

But on my plain athlon system it's :

```
 7202 billy     16   0 13408 7408 5908 S  0.0  1.9   0:02.28 metacity
```

Which looks a lot more reasonable!  :)  Once in a while I have to kill metacity or else the system grinds to a halt and swaps like mad.

After a kill it goes back to a more reasonable :

```
18284 billy     15   0 62104 8808 6524 S  0.4  1.7   0:00.15 metacity
```


Anyone else seeing this?

---

