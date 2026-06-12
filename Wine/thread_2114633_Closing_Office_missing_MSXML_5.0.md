---
title: "Closing Office missing MSXML 5.0"
date: 2013-02-10
forum: Wine
---

### Post by Synoc on 2013-02-10
I try to close MS Word 2007 and I get "This feature requires MSXML 5.0 to be properly installed. Run setup and click repair to restore this component."

now here's is what I've found:
sometimes MS Office installation has a problem with 64 bit wine archs

so I ran this 
```

export WINEARCH=win32
mkdir $HOME/.wine_msoffice
export WINEPREFIX=$HOME/.wine_msoffice
wine /path/to/setup.exe

```

I still get the same error.  I try to add the dll through winecfg and winetricks (just in case), but it's not an option 3, 4, and 6 are but 5 is missing. could use some help.

---

### Post by Synoc on 2013-02-11
bump

---

### Post by Synoc on 2013-02-14
re-bump

---

### Post by Synoc on 2013-02-16
bump again. Why does it say I need msxml5?

---

### Post by dino99 on 2013-02-17
if you really want some true answers, then the right place is on winhq's app database

[http://bugs.winehq.org/show_bug.cgi?id=30785](http://bugs.winehq.org/show_bug.cgi?id=30785)

---

