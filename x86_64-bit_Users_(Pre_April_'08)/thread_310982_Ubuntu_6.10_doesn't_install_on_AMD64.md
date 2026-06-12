---
title: "Ubuntu 6.10 doesn't install on AMD64"
date: 2006-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by ipina on 2006-12-02
Hi, I'm a newbie and try to run Linux Ubuntu for AMD64 proccesor. I downloaded ubuntu610desktopamd64.iso, burned to a cd and tried to start-install. I've got the message "failed to start the X server (your graphical interface), it's likely that it's not set up correctly" so examining the X server output I found "(EE) no devices detected". My pc is dual core AMD 64 and graphical card is ati radeon X700 with monitor Philips 180B2. I've tried ctrl+alt+F2 and sudo nano /etc/X11/xorg.conf, but not sure what I should modify. Any suggestion? Thanks in advance.

---

### Post by kuja on 2006-12-03
Which driver are you using for the video card? 

It should say in the /etc/X11/xorg.conf file, in the section Device. 

If you're using the OSS drivers and it says "ati", try switching it to "vesa", or vice-versa, and reboot.

---

### Post by hainesr on 2006-12-04
Another thing to try might be the "alternate" install CD. This is the one you need for things like LVM setup during install so it doesn't boot into a desktop but just starts the install in text based mode. It's more likely that the installer will be able to set up your graphics card properly than it is that the desktop live CD can handle all known set-ups out of the box.

I have an AMD64 (although a NVidia graphics card) and the alternate CD worked first time.

Cheers,
Rob

---

