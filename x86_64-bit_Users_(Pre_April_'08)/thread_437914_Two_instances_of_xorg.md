---
title: "Two instances of xorg"
date: 2007-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by ribenaman on 2007-05-09
Hi, 

I seem to have two instances of xorg running simultaneously under AMD64 Feisty. Is this normal? it would seem to be an utter waste of memory. I am using the fglrx driver and only a single monitor.

```

chris@chris-laptop:~$ ps ax | grep X
 4825 tty7     SLs+   0:05 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 4945 tty7     SL+    0:00 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 5493 pts/0    R+     0:00 grep X


```

According to ksysguard or the gnome equivalent, both xservers use an identical amount of memory but only one appears active. Killing the inactive xserver seems to have no effect on stability. I have also noticed that whether I use kdm or gdm I always end up with two instances of them also.

Thanks in advance.

---

### Post by rai4shu2 on 2007-05-09
What does it look like in "tree" mode when you look at htop?

---

### Post by ribenaman on 2007-05-09
Ok, I'm not sure how to output the 'tree' mode from htop but it would appear that one xorg instance is spawning the other one. The same is true for gdm.

I tried going back to the r300_dri driver and found that the problem went away. I'm using the restricted driver as I can't get the dri one working with suspend/resume.

---

### Post by rai4shu2 on 2007-05-09
Tree view is one of the Setup/Display options in htop.

---

### Post by ribenaman on 2007-05-09
Sorry, I meant I can put it in tree view and look at it myself but don't know how to get the output to post here.

---

### Post by ribenaman on 2007-05-09
Ok, I've typed out the bit relating to the xservers:

```

/usr/sbin/gdm
`- /usr/sbin/gdm
  `- /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
  | `- /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
  `- /usr/bin/gnome-session
  | `- /usr/bin/ssh-agent
  | `- /usr/bin/metacity
  |
  |    # Loads of stuff
  |
  |
  `- /usr/bin/gnome-session


```

Does that help at all?

---

### Post by rai4shu2 on 2007-05-09
I think for gdm that's normal, but it's a little weird for X. Not sure what to make of it, actually.

---

### Post by ribenaman on 2007-05-09
Thanks for trying. It appears to be something to do with the fglrx driver. The only difference between the xorg.conf files I've been using is a change to the 'device' settings from ati to fglrx and changes to disable composite and aiglx.

There are a few modules loaded in xorg.conf that I don't recognize but are left over from the initial setup. Any of them look odd to you?

```

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

```

---

### Post by rai4shu2 on 2007-05-09
The most recent fglrx box I set up I had this:

```
Section "Module"
EndSection
```

(i.e. nothing in the modules.)

---

### Post by markl187ld on 2007-05-10
I'm having the same problems under i386. Can anyone else offer any other solutions?

EDIT:

---

### Post by ribenaman on 2007-05-11
How did you go about removing the applet? I've done:

```

sudo apt-get remove fglrx-amdcccle

```

But that doesn't seem to have cleaned up the problem.

---

### Post by markl187ld on 2007-05-11
> **ribenaman said:**
> How did you go about removing the applet? I've done:

```

sudo apt-get remove fglrx-amdcccle

```

But that doesn't seem to have cleaned up the problem.

Scratch that. The problem re-occured on next boot.

---

### Post by Jouke74 on 2007-05-14
Are you having two monitor outputs or one?

---

### Post by ribenaman on 2007-05-15
Only one monitor in use. I do have an output on the back of my laptop for another monitor and a further output for a TV. There are no dual screen settings in my xorg.conf (to the best of my knowledge).

---

### Post by twent4 on 2007-11-21
got the same issue running kubuntu gutsy in 32 bit, so i dont think it's a 64 bit issue... the tree shows xorg calling up xorg, and they both use the same amount of resources (about 350 megs each), but cumulatively its quite the number... any suggestions?

---

