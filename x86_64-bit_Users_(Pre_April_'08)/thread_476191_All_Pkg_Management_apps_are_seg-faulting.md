---
title: "All Pkg Management apps are seg-faulting"
date: 2007-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by splot on 2007-06-16
Okay, I was messing around with wine and trying to get older games working...I think the last odd thing I did was to try to run neverwinter nights thru wine...didn't appear to do anything, but soon after, KDE crashed...taskbar disappeared, I restarted and it worked fine again.  But now every time I try to start up ANY package management software, it seg-faults and the window closes immediately...this includes synaptic, the updater, and apt (just says "segmentation fault").  The only one that works is Automatix, and that's only the gui, as soon as it tries to use apt in the back-end, that fails too.

wtf???  how do I fix this?  For that matter, how'd I break it?? :( :( :( 

to add insult to injury, in messing with Automatix I found one of the other things I was looking for, but now I can't install it cuz of that seg-fault prob. :(

[COLOR="Red"]EDIT[/COLOR]: It fixed itself.  Very strange. Then it broke itself again.  HEEEEEEEELP!!!!!!!! :(

---

### Post by splot on 2007-06-18
YEAH, it's happening intermittently.  It happened before, and then it went away, now it's happening again and I don't know what exactly makes it stop. :(

---

### Post by Cappy on 2007-06-19
Try
```
apt-get check
```
and ```

apt-get clean
```
and
```

dpkg --configure -a

```
if you can. 

If that doesn't work try
```
sudo aptitude reinstall apt
```
when you get the chance. 
You can also download apt from packages.ubuntu.com if your package managers just won't work any more and install it with
```
sudo dpkg -i packagename.deb
``` while you are in the same folder as it.

---

