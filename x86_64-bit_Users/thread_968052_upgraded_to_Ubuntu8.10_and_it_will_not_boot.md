---
title: "upgraded to Ubuntu8.10 and it will not boot"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by pneumonic81 on 2008-11-02
I get an error that Module nvidia is not found, and it failed to load. It says the X-server fails to load because no screens are found. 

Has anyone run into this problem?

---

### Post by Kilz on 2008-11-02
What it sounds like is that you need to install the nvidia drivers.

---

### Post by ariel on 2008-11-02
> **pneumonic81 said:**
> I get an error that Module nvidia is not found, and it failed to load. It says the X-server fails to load because no screens are found. 

Has anyone run into this problem?

It looks like you were using the propietary nvidia driver and for some reason the updater didn't install it.

A quick fix would be to do a console login (press Ctrl-Alt-F2, and login with your username and password), and then do:


```


sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup

sudo nano /etc/X11/xorg.conf
```Then scroll down in the file until you find something that looks like this (your nvidia card model will most probably differ):

```
Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8600 GT]"
        Driver          "nvidia"

```
and change the driver line with:

```
        Driver          "nv"
```

Then press "Ctrl-O" and accept the overwrite to save the new file. This should allow your pc to boot with the graphical environment, using the non-accelerated and free nvidia driver. 



Now to properly install the accelerated driver in Intrepid, you can do:

System menu > Preferences > Appearence > Visual Effects

... and click on "Normal" or "Extra", this should do it.

---

### Post by pneumonic81 on 2008-11-02
So it seems that this is a proprietary nvidia driver issue. if I use NV for my driver, its ok, but I can only use one monitor, no accel. If i try to go to the more advanced drivers, I get a crash. 

I guess 3d acceleration isnt working at the moment

---

### Post by surelock22 on 2008-11-02
i have an Nvidea 6800 XT and my machine runs Ubuntu 8.10. i'm brand new to Ubuntu, and i'm just starting to sink my teeth into the platform, so i haven't started running games with 3D or Windows based games yet (something I want to try out just to see how my set-up runs now that i'm going with ubuntu). i thought that if your graphics card didn't work correctly, you didn't get a display, period. the simple fact that i have something on my monitor means my graphics drivers are working properly, right? i will say this: the Nvidea driver i had when it was a Windows machine was much beefier than what i'm looking at now.

---

### Post by surelock22 on 2008-11-02
> **pneumonic81 said:**
> 

I guess 3d acceleration isnt working at the moment

this is what i hope ISN'T true...

---

### Post by aikiwolfie on 2008-11-02
I get this problem on both 32-bit and 64-bit versions of ubuntu 8.10. I'm just about ready to give up. I've going to try one last thing. Copying the xorg.conf file from the previous version which i know works because I've been using it for 6 months.

If that doesn't work I'll just roll back to 8.04 and wait for 9.04. I'm sick and tired of this DIY messing around crap. I might even just go buy a Mac. I thought ubuntu was supposed to "just work".

---

