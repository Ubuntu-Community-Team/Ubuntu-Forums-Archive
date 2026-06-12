---
title: "Wine can't open windows"
date: 2006-12-17
forum: Wine
---

### Post by penguinland on 2006-12-17
I'm running Xubuntu (the Edgy Eft version), and have recently installed wine. The installation itself went fine, but now when I try to run winecfg, I get the following output:
```
mycomputer% winecfg    
wine: creating configuration directory '/home/alan/.wine'...
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  143 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x122
  Serial number of failed request:  19
  Current serial number in output stream:  19
wine: wineprefixcreate failed while creating '/home/myusername/.wine'.
wineserver: could not save registry branch to /home/myusername/.wine-X5e4pe/system.reg : No such file or directory
wineserver: could not save registry branch to /home/myusername/.wine-X5e4pe/user.reg : No such file or directory

```This seems to be related to graphics in some way, so here's what I've got: I'm running Xorg 1.1.1 with xinerama on two GeForce2 cards (one PCI, one AGP), both running nvidia's drivers. I have this same problem when running winecfg from either screen. 

Any idea what's going wrong, or how I can fix it? Thanks very much!

---

### Post by tauil on 2007-01-15
I'm having the same problem. Probably because I'm working with xinerama too

The only way that I've found to "fix" it is killing X and starting it up again!

Cya,
Tauil

---

### Post by randomperson83 on 2007-01-22
I'm having the same general problem, also running NVidia GLX with three monitors and xinerama... go figure. I need my wine! :(

---

### Post by little cazy on 2007-09-04
same here, but i'm is
```
eyez@Zola:~$ winecfg
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x3c00007
  Serial number of failed request:  13
  Current serial number in output stream:  15

```
and i'm running fiesty.

---

### Post by cogadh on 2007-09-04
What version of Wine are all of you using? Someone else posted the same problem and they were using Wine 0.9.12, when the latest version is 0.9.43. If you aren't using the latest, you might try updating to it:
[http://www.winehq.org/?announce=latest](http://www.winehq.org/?announce=latest)

---

### Post by little cazy on 2007-09-06
i run 0.9.44 ofwine

---

### Post by citizenr on 2007-12-18
> **little cazy said:**
> same here, but i'm is
```
eyez@Zola:~$ winecfg
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x3c00007
  Serial number of failed request:  13
  Current serial number in output stream:  15

```
and i'm running fiesty.


delete "+0+0" from the video mode in xorg.conf

---

