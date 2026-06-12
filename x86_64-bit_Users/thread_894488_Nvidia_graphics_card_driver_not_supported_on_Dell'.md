---
title: "Nvidia graphics card driver not supported on Dell's XPS 1530 computer"
date: 2008-08-19
forum: x86 64-bit Users
---

### Post by ashish424242 on 2008-08-19
Guys ,I had been using Ubuntu on my personal XPS for months. I have now changed to the 8.04 edition of Ubuntu . In Ubuntu 8.04 to enable the desktop effects I must install the nvidia driver in my pc .I tried to do this but after that the display was blurred and I had no way to correct this out ,so I had to install it once again.  Could anyone tell me if what could have been the problem ? Also I saw that the default Desktop decorator was metacity could anybody tell me that how I could enable the compiz as the window decorator???

---

### Post by Nepherte on 2008-08-19
And what graphic card does the m1530 have? If it's a Nvidia 8400M GS, then you should be able to get it running. Did you try envy? To install it:
```
sudo apt-get install envyng-gtk
```

Then you run it by entering:
```
envyng-gtk
```

From then on, you can use the gui to install your nvidia card. Be sure to remove the current nvidia driver, so it won't mess with the new installation.

---

### Post by VeeDubb on 2008-08-19
It also helps to enable the "backports" repository when your run envy, or at least it did for me.

---

### Post by Nysomin on 2008-08-20
I'm kinda surprised this hasn't been suggested before.  Here is what I do:

First go to nvidia's website and find the drivers you want.  I was able to install beta 177.67 this way.  And Regnum is faster, and Blender is much happier now.

When in grub boot in rescue or single-user mode of whatever kernel you want.  It'll give you the rescue options but also ask you to drop to a root shell prompt.  Do that and you can run the nvidia installer like nvidia likes you too.  Only think is that you'll be in init 1 not 3.  I had no problem installing anyway though.  Oh, and I haven't been able to find a functional difference between init 3 and 5 in ubuntu.

---

### Post by falcon61102 on 2008-08-20
When you run envyng-gtk it also helps to run it as sudo:
```
sudo envyng-gtk
```

That way it has the access rights to be able to overwrite or move any files necessary for the installation.

---

### Post by jespdj on 2008-08-20
It works without any problems on my XPS M1530 with nVidia 8600M. I didn't need to use Envy (which is a script not officially supported by Ubuntu to install the driver).

See [Ubuntu on the Dell XPS M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530).

---

