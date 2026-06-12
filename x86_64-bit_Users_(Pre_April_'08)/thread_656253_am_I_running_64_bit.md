---
title: "? am I running 64 bit"
date: 2008-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by frenchsquared on 2008-01-02
so how do I know if it installed 64 bit or not

when i tried to install flash I got an error that it was incompatible with 64 bit

so am i running 64 bit?

---

### Post by John.Michael.Kane on 2008-01-02
To see if the machine is running a 64bit kernel you can run the command below
```
uname -a
```

Example uname -a output 
```
Linux (your machine name here) 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 **x86_64** GNU/Linux
```

If the output does not match this then your running a 32bit kernel.

Regarding flash there is currently  an issue surround it's install not working. which you can read about in the thread below.
[http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by ~LoKe on 2008-01-02
A simpler way:
```
uname -m
```
> [12:52:14 loke]$ uname -m
x86_64

---

### Post by frenchsquared on 2008-01-02
its x86_64, hmmm wonder how I did that?
oh well, had to go 64 someday

thanks

---

### Post by ~LoKe on 2008-01-02
You should be able to install flash like this....all one line.

```
cd ~/ && wget http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz && tar xzvf nsplugin*.tar.gz && cd nsplugin*install && sudo ./GetFlash
```
Then follow the steps.

---

### Post by frenchsquared on 2008-01-02
> **~LoKe said:**
> You should be able to install flash like this....all one line.

```
cd ~/ && wget http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz && tar xzvf nsplugin*.tar.gz && cd nsplugin*install && sudo ./GetFlash
```
Then follow the steps.

its asking for the Ubuntu amd64 cd, is that ok. Im running an Intel machine C2D

---

### Post by ~LoKe on 2008-01-02
> **frenchsquared said:**
> its asking for the Ubuntu amd64 cd, is that ok. Im running an Intel machine C2D

Sounds like you still have the cdrom repository in /etc/apt/sources.list
Try..
```
gksu gedit /etc/apt/sources.list
```
And look at the top of the list, look for a line that says anything about cdrom and comment it out or remove it.  Then try again.

---

### Post by frenchsquared on 2008-01-02
THANKS

ive spent days fighting flash in the beginner forum. 
It seemed that I was out of luck becasue of the 64 bit thing

flash is working and I dont have to carry that cd around
[B]
THANK YOU[/B]

---

### Post by ~LoKe on 2008-01-02
No problem.  Happy to help (especially with all the help I've received).  But you could also thank Kilz in [his thread](http://ubuntuforums.org/showthread.php?t=476924), because these packages were upload by him. =]

---

