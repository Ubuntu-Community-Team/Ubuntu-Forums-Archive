---
title: "xpdf?"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Snodgrass on 2005-10-15
Just installed Badger 64, xpdf doesn't work, can't find it with apt-get or synaptic. Do I need to open a special repository?

---

### Post by Manny C on 2005-10-15
1. You need to enable the Universe repositories. Edit /etc/apt/sources.list as superuser:
```
 sudo gedit /etc/apt/sources.list 
```
2. Uncomment the two lines referring to the Universe repositories.
3. Then reindex the packages:
```
 sudo apt-get update 
```
4. Install xpdf
```
 sudo apt-get install xpdf 
```

Hope that works.

---

### Post by Snodgrass on 2005-10-15
Worked a treat, Manny C, many thanks, & g'day. 

[QUOTE=Manny C]1. You need to enable the Universe repositories. Edit /etc/apt/sources.list as superuser:
```
 sudo gedit /etc/apt/sources.list 
```
2. Uncomment the two lines referring to the Universe repositories.
3. Then reindex the packages:
```
 sudo apt-get update 
```
4. Install xpdf
```
 sudo apt-get install xpdf 
```

Hope that works.[/QUOTE]

---

