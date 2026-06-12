---
title: "List of installed packages with dpkg"
date: 2005-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tamir on 2005-07-19
Hi,

I want to (not realy :/) reinstall my hoary because I have so many problem,
and that's the easy way. I wanted to know how get a list of all my installed packages with dpkg command, I know there is a thing like that.

---

### Post by DancingSun on 2005-07-19
try:
```
dpkg -l
```

Did you screw something up while making packages for us?  ](*,)

---

### Post by Tamir on 2005-07-19
[QUOTE=DancingSun]try:
```
dpkg -l
```

Did you screw something up while making packages for us?  ](*,)[/QUOTE]
 Huh, no... just from the beginning I had so many problems, the best idea is to reinstall :/.

---

### Post by DancingSun on 2005-07-19
Oh ok, well, glad that it's not because of us that your Ubuntu was getting screwed over for :D

---

### Post by smoon on 2005-07-19
[QUOTE=Tamir]Hi,

I want to (not realy :/) reinstall my hoary because I have so many problem,
and that's the easy way. I wanted to know how get a list of all my installed packages with dpkg command, I know there is a thing like that.[/QUOTE]

I think what you're looking for is
```
dpkg --get-selections
```
and
```
dpkg --set-selections
```

---

