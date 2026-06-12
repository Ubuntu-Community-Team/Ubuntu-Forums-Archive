---
title: "kernel2.6.15-25 +gnome updates issues"
date: 2006-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by gaatmx on 2006-06-19
after the "big" updates things are wired...:confused: 

I can boot, recah the gdm screen but my mouse and my keybord did not work :confused: 
the cursor blinks in the login prompt for some seconds and stop working also. 
Rebooting----> did not work.
I have installed the restricted modules and no luck.
I use nvida drivers and Xgl. everything works well using the previous kernel.
Any ideas?

---

### Post by Kilz on 2006-06-20
[QUOTE=gaatmx]after the "big" updates things are wired...:confused: 

I can boot, recah the gdm screen but my mouse and my keybord did not work :confused: 
the cursor blinks in the login prompt for some seconds and stop working also. 
Rebooting----> did not work.
I have installed the restricted modules and no luck.
I use nvida drivers and Xgl. everything works well using the previous kernel.
Any ideas?[/QUOTE]
Use the previous kernel. I am, the bugs they patched would allow a local user to gain administrative control. If its a home computer and no one at your house will mess with it trying exploits you will be ok imho.

---

### Post by fragos on 2006-06-20
This may not relate to your problem but, after upgrading from -23 to -25 I had to edit xorg.conf to change the video drive from "nvidia" to "nv" to get past level 3.  I finally got #D back by installing the nvidia driver with the nvida-installer they provide.

---

