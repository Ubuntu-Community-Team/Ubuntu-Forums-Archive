---
title: "rescue training--"
date: 2007-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by eleim7 on 2007-09-02
I've installed Feisty Fawn three times I think, just because I've broken something on it and didn't know how to fix it, so opted for complete reinstall.  So, it's only a matter of time until I break it again...

So, any pointers on how to NOT screw up the session?  Or mainly, how to rescue my Ubuntu install after I have messed it up?  I had some problems with Envy and couldn't get my graphics driver working again (solution: reinstall) and I've had compiz fusion working until I restarted, where the screen would freeze.  After going into Failsafe:Terminal, I would type 

compiz --replace & emerald --replace & 

and then, I could type gnome-session and things would work (for the most part) but I could never fix it completely (even after googling and looking through pages and pages of these forums... solution: reinstall).  I'm new, and I would be more experienced today if I could just install things like compiz fusion without having to worry about wasting time reinstalling again and actually get to play around with them.  Thanks.

(oh yeah, third reinstall was when I realized my LiveCD was 32bit and I have a AMD 64... which is why I am here)

---

### Post by kuja on 2007-09-03
Rather than doing full reinstalls it'd be a lot easier to purge and reinstall the relevant packages.

ie: sudo apt-get --purge remove [list of packages]
sudo apt-get install [list of packages]

---

### Post by jpkotta on 2007-09-03
> **eleim7 said:**
> (oh yeah, third reinstall was when I realized my LiveCD was 32bit and I have a AMD 64... which is why I am here)

x86-64 chips provide a strict superset of features compared to x86-32 chips.  This means when you install a 32-bit operating system, it will work just as if you had a 32-bit chip.  Thus you have no 64-bit-related problems.

Secondly, I don't think you need Envy.  From what I just read, it's an installer for binary video drivers.  But a) there is already a GUI specifically for installing binary video drivers in Feisty (restricted package manager or something like that), and b) it can be done by simply installing one or two packages anyway.  So don't use Envy because you don't need to, and it will eliminate one possible cause of your troubles.

Also, [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by Kilz on 2007-09-03
> **eleim7 said:**
> I've installed Feisty Fawn three times I think, just because I've broken something on it and didn't know how to fix it, so opted for complete reinstall.  So, it's only a matter of time until I break it again...

So, any pointers on how to NOT screw up the session?  Or mainly, how to rescue my Ubuntu install after I have messed it up?  I had some problems with Envy and couldn't get my graphics driver working again (solution: reinstall) and I've had compiz fusion working until I restarted, where the screen would freeze.  After going into Failsafe:Terminal, I would type 

compiz --replace & emerald --replace & 

and then, I could type gnome-session and things would work (for the most part) but I could never fix it completely (even after googling and looking through pages and pages of these forums... solution: reinstall).  I'm new, and I would be more experienced today if I could just install things like compiz fusion without having to worry about wasting time reinstalling again and actually get to play around with them.  Thanks.

(oh yeah, third reinstall was when I realized my LiveCD was 32bit and I have a AMD 64... which is why I am here)

I have a good suggestion, backup! I use the partimage rescue cd to back up my install at least once a month, or before messing with things likely to make it unusable (like messing with ATI graphics drivers). Then if something does mess up its a quick restore and im back where I was.

---

### Post by eleim7 on 2007-09-03
Lol, so I already messed things up when I tried to update to the latest Nvidia driver.  I backed up my current xorg.conf file with:

             sudo cp /etc/X11/corg.conf /etc/X11/corg.conf.justin

...as instructed by 

             [http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

But how do I revert to that backup if something goes wrong in my install?

---

### Post by Kilz on 2007-09-03
> **eleim7 said:**
> Lol, so I already messed things up when I tried to update to the latest Nvidia driver.  I backed up my current xorg.conf file with:

             sudo cp /etc/X11/corg.conf /etc/X11/corg.conf.justin

...as instructed by 

             [http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

But how do I revert to that backup if something goes wrong in my install?

```
rm /etc/X11/xorg.conf

mv /etc/X11/xorg.conf.justin /etc/X11/xorg.conf
```

should replace the one thats there with the backup.

---

