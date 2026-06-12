---
title: "VirtualBox With XP Guest Very Slow"
date: 2009-11-11
forum: x86 64-bit Users
---

### Post by dyous87 on 2009-11-11
I am running Ubuntu 9.10 x64 on a Sony Vaio VGN-FZ140e. I use VirtualBox to run a Windows XP virtual machine but the performance is terrible for lack of a better word.

I had 2gigs of ram and was assigning a gig to the Virtual machine. 1 gig should be more then enough for Windows XP but apparently it wasn't.

I upgraded my laptop to 4 gigs figuring this would give a nice performance boost. After this I assigned 2 gigs of the 4 gigs of RAM to the Vitual Machine. This really did not help the performance at all. It takes over 3 minutes for XP to even boot up and once it does, the operating system is very slow and nothing moves quickly and snappy. It is all very laggy. 

I have the latest version of VirtualBox with the Guest additions installed. I have even switched to XP classic thinking the less flashy theme would help. I've played with all of the settings including PAE/NX, VT-x and Nested Paging but nothing seems to help. 

Surely with 4 gigs of ram and an Intel Core 2 Duo processor I should be able to run a Windows XP virtual machine quickly. Please any help on this issue would be greatly appreciated.

Best Regards,
David

---

### Post by artmendez on 2009-11-12
How's your XP Virtual Harddisk?
Have you tried cleaning it up a bit?
Remember... even if it's Virtualbox... it's Windows XP behind it... it's can be so much like the real thing... :P

I switched to 9.10 x64 in a Dell 630c, 2GB, Centrino vPro, when I installed Virtualbox and imported the virtual machine files for an XP (set @ 1GB), I had to tweak it a bit. I just have it now running "manageably", and actually faster (may be 64-bit related?)

Try switching off PAE/NX and Nested Paging (both), but leave the VT-x on. 

Please do share results.

saludos!

---

### Post by dyous87 on 2009-11-12
I took you advice by switching off PAE/NX and Nested Paging. I am now defragging the virtual hard drive. I'll let you know how it goes!

Thanks!

David

---

### Post by dyous87 on 2009-11-13
Ok so I finished degragging and turned off all of the effects completely. Menu shadows, dragging windows etc.)

The speed of the operating system did increase but not by much.

Anyway, I decided to try installing Windows 7 instead. Well I just did and I must say it is much much faster. So that takes care of that problem.

The Windows 7 guest is 64 bit and is my Ubuntu host. The XP i was running was 32 bit. I wonder if that is why it didn't run well?

David

---

### Post by niw_uk1964 on 2009-11-13
FWIW I have several XP installations running on my quad core 9.10 box and they are extremely fast. As fast as many clean native installations. I don't think it's anything to do with 32/64bit.

---

### Post by KayakJim on 2009-11-13
I am running WinXP Pro in VirtualBox on Intrepid and Jaunty on laptops with only 2GB RAM and Intel Core 2 Duos @ 2.0GHz and they all run fairly fast, almost as fast as a native WinXP system.

Perhaps it has something to do with 9.10's newer kernel?

---

### Post by codenamezero on 2009-11-13
Yea, XP runs extremely slow even after i reinstalled it... even during the installation took FOREVER. However, i've discovered a way to make it run faster... is lame... you have to hover your mouse on the taskbar and have the VBox XP window to show up on the thumbnails... then it would run a bit faster. That's the only way to get the XP **** reinstall without taking HOURS...

---

### Post by DodgeV83 on 2009-11-15
I had these same issues.  Fixed it by installing the 32-bit version of Windows 7, giving it only 1 CPU in the settings, turning off all advanced CPU options besides VT-x/AMD-V, giving 128MB of Video Memory and enabling 3D acceleration.

Really, most of these settings are already the default, it was my messing with the settings in the first place which caused issues.

---

### Post by Chronon on 2009-11-16
I am having problems with slow 32-bit guests since installing 64-bit Karmic.  I had no such problems with 32-bit Jaunty.

---

