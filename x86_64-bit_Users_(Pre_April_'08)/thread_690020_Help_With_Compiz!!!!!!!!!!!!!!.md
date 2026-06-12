---
title: "Help With Compiz!!!!!!!!!!!!!!"
date: 2008-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by bloodhacker2 on 2008-02-07
ok guys i am using 7.10 Ubuntu Linux on a 64bit CPU.

this is what happen, i log onto my computer and i had my computer set to auto turn on compiz, well when it did that the terminal would come up as just white and non of my effects would work. so i just thot well it is a glitch so i went in and told the computer not to turn on compiz on start up and then i restarted my computer. after the reboot i log on and everything was working fine without having the compiz on thin i went to the terminal and type compiz to start it up and at that time in the terminal it gave me sum error messages  and then when i try to open up another terminal the terminal was just solid white and you could int see anything and all my effects would int work like the wiggly page thing and my emerald them would int do anything. hear is everything i got after typing compiz in the terminal....

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0245 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
Reloading...
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Reloading...
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Reloading...
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
```


but i have no interest in having all those extra effects on my computer all i care about is have the emerald team manager on my computer and that is it..... how to i go about removing compiz and installing just emerald team manager????

---

### Post by agim on 2008-02-07
Try this.
sudo apt-get install xserver-xgl
Then run compiz again.

If that doesn't work, type the following command into a terminal and post the output.
lscpi

Good luck!

---

### Post by Yellow Pasque on 2008-02-07
Before you go installing XGL, let's have a look at your /usr/bin/compiz file.

---

### Post by bloodhacker2 on 2008-02-07
> **agim said:**
> Try this.
sudo apt-get install xserver-xgl
Then run compiz again.

If that doesn't work, type the following command into a terminal and post the output.
lscpi

Good luck!

no that dint work, it install sum stuff but it dint seem to make a difference. don't you think i could just reinstall compiz over again.
this is what i got when i type that second command.

```
bash: lscpi: command not found
```

---

### Post by bloodhacker2 on 2008-02-07
But now when i put /usr/bin/compiz in the terminal now everything is working..

---

### Post by bloodhacker2 on 2008-02-07
now how do i get the cube to work?????

---

### Post by agim on 2008-02-08
Sorry, that was supposed to be lspci... My mistake.

To get the desktop cube install gnome-compiz-manager, with either synaptic or ...

sudo apt-get install gnome-compiz-manager

Once you start the application go to the third tab: workspaces. From there just click on what you want.

---

