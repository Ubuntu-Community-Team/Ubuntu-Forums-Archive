---
title: "[SOLVED] Bluetooth Blues"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by HanaD on 2008-01-06
Holla Amigos!

I am using ubuntu 7.10 on my desktop while i use XP professional on my x61 lenovo tablet.

my problem is that i can pair the 2 devices through bluetooth and i can also send files from ubuntu to Xp, but when i try to send files from XP to ubuntu it does not work.
says ftp service not found, is it a glitch of windows or do i need to tweek something with ubuntu?

please help
Regards,
Hana

---

### Post by John Jason Jordan on 2008-01-07
> **HanaD said:**
> Holla Amigos!

I am using ubuntu 7.10 on my desktop while i use XP professional on my x61 lenovo tablet.

my problem is that i can pair the 2 devices through bluetooth and i can also send files from ubuntu to Xp, but when i try to send files from XP to ubuntu it does not work.
says ftp service not found, is it a glitch of windows or do i need to tweek something with ubuntu?
I'm not sure if it will help, but I recommend blueman. It's not in the Ubuntu repositories, but you can download a .deb and install it with gDebi. Unfortunately, I did not bookmark the site where I downloaded the .deb file. I think it was on sourceforge. Or search these forums on "bluetooth," because I know it has been mentioned here somewhere - I learned about it on the Ubuntu forums.

---

### Post by aypnia on 2008-01-08
Check in your applications>accessories if you have a program called bluetooth filesharing.
In order to receive anything this must be running

---

### Post by HanaD on 2008-02-02
i have the bluetooth file sharing but somehow things arent working,
devices are not recovered after searching, have checked 100 times that the devices are in discoverable mode but no luck.

---

### Post by HanaD on 2008-02-03
Installed every damn packet that was there in synaptic for bluetooth,
everything works now :-)

---

### Post by steveneddy on 2008-02-03
Install bluetooth file sharing and in your start up 

System --> Preferences --> Sessions

add the **gnone-obex-server** to start when you boot the PC.

This will make all of this automatic. Very easy.

---

