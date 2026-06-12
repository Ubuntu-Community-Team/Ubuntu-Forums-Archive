---
title: "Wine + Steam+ ATI = problem!!"
date: 2008-09-10
forum: Wine
---

### Post by v4npro on 2008-09-10
Hey, I'm new to Ubuntu(64bit), linux for a matter of fact, and I installed wine, installed steam, but when I go to install a game, my screen goes all distorted and I have to Alt-Ctrl-Backspace and log back in.  I tried also Cedega with Warcraft 3 and I get the same problem.  Here's a picture I took of what it looks like:

[Picture]("http://customwow.net/pics/linx.jpg")

Now thats what I get aswell in Steam when I click install Counter-Strike.  I tried Warcraft 3 again in Windowed mode and I get same problem. I got two HD3870 in crossfire with the latest ATI drivers 8.8.  I installed them manually by following steps from another site. Any help or hints would be very much appreciated.  

Thanks, can't wait to try some gaming on Linux!!

I do have Vista x64 for real gaming but just want to try something new.

Edit:: Ok so ATI drivers 8.5-8.8 cause the checkerboard of death with Wine and similar programs.  Will ATI's 8.9 that will come with month fix this problem you think??
""Current fglrx drivers as of September 2008 8.4 works but 8.5-8.8 have this problem along with other applications such as WINE. The display will decompose into row blocks offset leading to an entirely unusable screen.""

---

### Post by Caedis on 2008-09-12
I think a large part of your problem is that you went with 64 bit. It has been my experience that 64 bit versions don't produce that much better results, and in fact, when you factor in that you have to use 32bit for many drivers and programs. I went with 32bit on my 64bit systems and noticed no speed loss and DID notice how much easier to setup 32bit was.

ATI also might be the issue. 32bit drivers are difficult to use (as I've heard), so by extension 64 bit would seem to be a bear IMO.

---

### Post by v4npro on 2008-09-12
Looks like  the problem I'm having, happens with 32 bit as well.    People using Cat drivers 8.5-8.8 get this problem when trying to play games.... i.e. through wine etc...

---

### Post by Caedis on 2008-09-12
Wow, so it looks like your out of luck for games in wine. I'd say to jsut buy some Nvidia GPUs but im guessing you didnt win those bad boys in a raffle. ;)

---

### Post by v4npro on 2008-09-12
It's fine lol, I'm just messing around in linux , I do my gaming on vista anyway.

---

### Post by ObiWan2001 on 2008-09-13
The solution is to change the libGL.so with the one from mesa or the one from 8.5 (DRI and Hardware accerlation works with both)

If you used the ATI-binary installer:
```

sudo mv /usr/lib/xorg/libGL.so.1.2 /usr/lib/xorg/fglrx_org_libGL.so.1.2
sudo cp /usr/lib/FGL.renamed.libGL.so.1.2 /usr/lib/xorg/libGL.so.1.2

```

with 64bit:
```

sudo mv /usr/lib64/xorg/libGL.so.1.2 /usr/lib64/xorg/fglrx_org_libGL.so.1.2
sudo cp /usr/lib64/FGL.renamed.libGL.so.1.2 /usr/lib64/xorg/libGL.so.1.2
sudo mv /usr/lib32/xorg/libGL.so.1.2 /usr/lib32/xorg/fglrx_org_libGL.so.1.2
sudo cp /usr/lib32/FGL.renamed.libGL.so.1.2 /usr/lib32/xorg/libGL.so.1.2

```

As alternative you can use the libGL.so from the 8.5 driver:
Download the 8.5 driver from AMD
```

sh ati-driver-installer-8-5-x86.x86_64.run --extract tmp
```
32bit:
```

sudo cp tmp/arch/x86/usr/X11R6/lib/libGL.so.1.2 /usr/lib/xorg/libGL.so.1.2

```
64bit:
```

sudo cp tmp/arch/x86_64/usr/X11R6/lib64/libGL.so.1.2 /usr/lib64/xorg/libGL.so.1.2
sudo cp tmp/arch/x86/usr/X11R6/lib/libGL.so.1.2 /usr/lib32/xorg/libGL.so.1.2

```

---

### Post by v4npro on 2008-09-13
well, the game loads to intro, but if i click the window it just freezes.

---

