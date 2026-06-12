---
title: "Virtualbox x64?"
date: 2007-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by M$LOL on 2007-02-20
Is there a version of [virtualbox]("http://www.virtualbox.org") for the x64 version of Edgy?

---

### Post by ffxr on 2007-02-20
hhhm i wish.. i think its in developement...
but, why dont you just use vmware or zen or something?

---

### Post by M$LOL on 2007-02-21
Well, I saw the .deb package so I decided to DL and see what it was like. I'm gonna use VMware once I get my wireless card and connect to the net. (At the moment only my Windows PC is). Should be coming today...

---

### Post by khermans on 2007-02-22
I built VirtualBox from source on Ubuntu Feisty (7.04) on an amd64 machine and it works great.  However, I am only able to run 32-bit guests, not 64-bit guests.  It still works just as well as VMware and is open source!
--
Kristian Hermansen

---

### Post by screening on 2007-04-19
how do you built from the source? please could explain how to make?

---

### Post by Medieval_Creations on 2007-04-19
Yes khermans, please enlighten us.

I tried compiling it from source on 64bit Edgy and I recieved compile errors that I couldn't figure out.
I can't remember the specifics, but I know they were because of the Host being 64bit.

---

### Post by Bill_Gates on 2007-04-19
With virtual box x64 you cannot acces to your usb devices in your guest machines. Any alternative in 64 bits host system? My usb webcam only works with xp virtualized.

---

### Post by Medieval_Creations on 2007-04-19
> **Bill_Gates said:**
> With virtual box x64 you cannot acces to your usb devices in your guest machines. Any alternative in 64 bits host system? My usb webcam only works with xp virtualized.

Did you compile it from source?
If so did you enable USB support when you configured VBox?

---

### Post by Bill_Gates on 2007-04-19
I didn't compile, because according to this: [http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)  open source edition does not support usb devices.

---

### Post by Medieval_Creations on 2007-04-19
When I was running the 32bit version of VBox I had USB working.  I was able to plug in my iPod and external HD's and they would show up in the Guest OS.

---

### Post by galv on 2007-04-23
> **khermans said:**
> I built VirtualBox from source on Ubuntu Feisty (7.04) on an amd64 machine and it works great.  However, I am only able to run 32-bit guests, not 64-bit guests.  It still works just as well as VMware and is open source!
--
Kristian Hermansen
Can you walk us through? I'm not (yet) installing Feisty 64bits because of VirtualBox...
Thanks :)

---

### Post by Kilz on 2007-04-23
> **galv said:**
> Can you walk us through? I'm not (yet) installing Feisty 64bits because of VirtualBox...
Thanks :)

I have managed to figure out how to [force in the 32bit version]("http://ubuntuforums.org/showthread.php?t=417192"). While not what you asked, it may prove helpful.

---

### Post by galv on 2007-04-23
But on the VBox site says that the 32bits version **does not** work in a 64 bit environment. Could you actually run a virtual machine (not just install VBox)?

Thanks

---

