---
title: "Help, Wine Windows look bad, corrupt looking theme..."
date: 2008-10-07
forum: Wine
---

### Post by DieseL1988 on 2008-10-07
Take a look at the image I've uploaded. If you look at the corners of the buttons they have which pixels in them. This happens everywhere and it looks quite terrible when you've got an application that's got quite a few scrollbars and buttons.

I haven't seen this problem reported anywhere else. I've tried downgrading, upgrading all sorts of things and I haven't been able to cure it. AFAIK I've always had the problem on this machine. Any able to shed any light on the issue?

---

### Post by Hairy_Palms on 2008-10-07
does it still happen with a fresh wine directory? 
try running 
> env WINEPREFIX="/home/**YOURUSERNAME**/.wine-testing" wine winecfg

---

### Post by DieseL1988 on 2008-10-07
Still the same problem with a fresh wine directory, this is what I got from running that command

```

markt@XENOMORPH:~$ env WINEPREFIX="/home/markt/.wine-testing" wine winecfg wine: created the configuration directory '/home/markt/.wine-testing'
Could not load Mozilla. HTML rendering will be disabled.

```

---

### Post by Hairy_Palms on 2008-10-07
hmm,  are you running compiz? if so does it happen with compiz disabled

---

### Post by DieseL1988 on 2008-10-07
Problem remains when compiz is disabled.

---

