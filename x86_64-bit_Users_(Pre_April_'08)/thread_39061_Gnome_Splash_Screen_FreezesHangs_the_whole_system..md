---
title: "Gnome Splash Screen Freezes/Hangs the whole system."
date: 2005-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by nandhu on 2005-06-03
Hi All,

I've the following Hardware:

Motherboard: Optronix K9M 200G MLF
[http://www.optronix.co.uk/acatalog/AMD.html](http://www.optronix.co.uk/acatalog/AMD.html)
ATI X200 Chipset.

AMD64 Athlon 3000

I've 2 Hard disks 
1 - 200GB SATA (IDE 5 Master) and 
1 - 8GB IDE (IDE 0 Master).

I installed Windows XP on 200GB SATA and wrote its startup files on the IDE hard disk.

Later installed Ubuntu 5.04 and installed its GRUB into First Boot Sector, So with this setup I can dual boot into XP and Ubuntu.

To add to my miseries, I've Toshiba LCD Monitor. 

After installing Ubuntu with the followign parameters
linux text and disabling framebuffer and USB mouse etc., I got the installation going without my LCD monitor throwing "Signal out of range" error.

Basically my Ubuntu installer only recognised my 8GB IDE, it did not even show any SATA being in my system. I thought it's okay, after getting the Ubuntu working, I could then compile the Kernel to identify any SATA drives in the system. 

After the installation took about an hour or so, I finally was in a position to reboot for the 1st time. When the X-Display should be showing after successful boot up, it displayed "Signal Out of Range".

I did "Cntrl + Alt + -" couple of times and I could see my Ubuntu graphical login screen.

At this point in time, I could also do "Cntrl + Atl + F1" and get to a console.

From the Graphical login, when I attempt to login with my user name and password, it accepts the username/password and then loads a GNOME/Ubuntu splash screen

"Ubuntu"
"Linux for Human Being"

and that's uptil where I could get to.

After that even if I leave my system for 1 hour, it's the same screen that gets displayed.

And I cannot do "Cntrl + Alt + F1" or F2, F3, F4 or anything like that. The whole box including keyboard, mouse etc are frozen/hanged. Only I have to do a hardware reboot, by pressing my reset button on the case.

Is there anything that I could do to get out of this problem?

Any help will be greatly appreciated.

Many thanks for all your help in anticipation.

- Nanda.

---

### Post by Alexander Kirillov on 2005-06-03
[QUOTE=nandhu]Hi All,

I've the following Hardware:

Motherboard: Optronix K9M 200G MLF
[http://www.optronix.co.uk/acatalog/AMD.html](http://www.optronix.co.uk/acatalog/AMD.html)
ATI X200 Chipset.

AMD64 Athlon 3000

I've 2 Hard disks 
1 - 200GB SATA (IDE 5 Master) and 
1 - 8GB IDE (IDE 0 Master).

I installed Windows XP on 200GB SATA and wrote its startup files on the IDE hard disk.

Later installed Ubuntu 5.04 and installed its GRUB into First Boot Sector, So with this setup I can dual boot into XP and Ubuntu.

To add to my miseries, I've Toshiba LCD Monitor. 

After installing Ubuntu with the followign parameters
linux text and disabling framebuffer and USB mouse etc., I got the installation going without my LCD monitor throwing "Signal out of range" error.

Basically my Ubuntu installer only recognised my 8GB IDE, it did not even show any SATA being in my system. I thought it's okay, after getting the Ubuntu working, I could then compile the Kernel to identify any SATA drives in the system. 

After the installation took about an hour or so, I finally was in a position to reboot for the 1st time. When the X-Display should be showing after successful boot up, it displayed "Signal Out of Range".

I did "Cntrl + Alt + -" couple of times and I could see my Ubuntu graphical login screen.

At this point in time, I could also do "Cntrl + Atl + F1" and get to a console.

From the Graphical login, when I attempt to login with my user name and password, it accepts the username/password and then loads a GNOME/Ubuntu splash screen

"Ubuntu"
"Linux for Human Being"

and that's uptil where I could get to.

After that even if I leave my system for 1 hour, it's the same screen that gets displayed.

And I cannot do "Cntrl + Alt + F1" or F2, F3, F4 or anything like that. The whole box including keyboard, mouse etc are frozen/hanged. Only I have to do a hardware reboot, by pressing my reset button on the case.

Is there anything that I could do to get out of this problem?

Any help will be greatly appreciated.

Many thanks for all your help in anticipation.

- Nanda.[/QUOTE]
 Any error messages in /var/log/system ?

---

### Post by NickB on 2005-06-03
I assume you're using the ati driver for xorg.  Set Option "NoAccel" "true"

Nick

---

### Post by nandhu on 2005-06-03
[QUOTE=Alexander Kirillov]Any error messages in /var/log/system ?[/QUOTE]

Hi Alexander,

Unfortunately when the freeze happens, I could not use my keyboard to get to F1 or F2 console or any other console for that matter. The whole system does not respond. I have press my Reset button on my Case. :(

Thanks for your time.

Nanda.

---

### Post by nandhu on 2005-06-03
[QUOTE=NickB]I assume you're using the ati driver for xorg.  Set Option "NoAccel" "true"

Nick[/QUOTE]
 Hi Nick,

I've just did a fresh install and I've not done anything great. It is the first reboot and then I get the "Signal Out of Range" on my LCD monitor where there usually should be the Ubuntu Graphical Login. Later to get to the Graphical Login, I did "Ctnrl + ALT + -" couple of times and then I could atleast get to the Graphical Login. When I attempt to Login, it shows/works till the Gnome splash comes, after that nothing happens, the whole system is hanged.

So, in short for your question, No I'm not using or at least not yet tried to use any ATI drivers. Just a simple straightforward install.

Thanks for your help and time.

-Nanda.

---

### Post by Alexander Kirillov on 2005-06-03
[QUOTE=nandhu]Hi Alexander,

Unfortunately when the freeze happens, I could not use my keyboard to get to F1 or F2 console or any other console for that matter. The whole system does not respond. I have press my Reset button on my Case. :(

Thanks for your time.

Nanda.[/QUOTE]
 The logs are stored - you can view them at next login. 

ALos: iut might be helpful if you posted your xorg.conf configuration file

---

### Post by NickB on 2005-06-03
[QUOTE=nandhu]I've just did a fresh install and I've not done anything great.
...
So, in short for your question, No I'm not using or at least not yet tried to use any ATI drivers. Just a simple straightforward install.[/QUOTE]
If you've got an ATI video chipset (most likely if you're using the on-board video) then ubuntu probably picked the stock xorg ati driver, not vesa (at least mine did).  I'm not talking about ATI's proprietary driver, I'm talking about the actual ati_drv.so module in xorg.  If you use the stock xorg ati driver, you need to specify NoAccel for the xpress 200 chipset.  It should look something like this in /etc/X11/xorg.conf:

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver         "ati"
        BusID          "PCI:1:5:0"
        Option         "NoAccel"               "true"
EndSection
``` 

Nick

---

### Post by jenik on 2005-06-04
Hi,
I have exactly the same problem. Athlon 64 3000, MB MSI K8N SLI, GeForce 6200. The driver used is nv. 
There is a log in /var/log/gdm saying something about skipping /usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o (and two similar ones) plus could not init fotn path element unix/:7100, removing from list
Rings any bells?
Any ideas anyone?
Jan

---

### Post by jenik on 2005-06-05
ok, setting NoAccel to true helped for me. Thanks :)

---

### Post by nandhu on 2005-06-06
[QUOTE=NickB]If you've got an ATI video chipset (most likely if you're using the on-board video) then ubuntu probably picked the stock xorg ati driver, not vesa (at least mine did).  I'm not talking about ATI's proprietary driver, I'm talking about the actual ati_drv.so module in xorg.  If you use the stock xorg ati driver, you need to specify NoAccel for the xpress 200 chipset.  It should look something like this in /etc/X11/xorg.conf:

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver         "ati"
        BusID          "PCI:1:5:0"
        Option         "NoAccel"               "true"
EndSection
``` 

Nick[/QUOTE]
 Hi Nick,

I'll try it this evening and will let you know. Thanks for your kind help.

Nanda.

---

### Post by nandhu on 2005-06-06
[QUOTE=Alexander Kirillov]The logs are stored - you can view them at next login. 

ALos: iut might be helpful if you posted your xorg.conf configuration file[/QUOTE]
 Hi Alexander,

I'll post my Xorg.conf this evening. Thanks.

Best regards,

Nanda.

---

### Post by nandhu on 2005-06-06
Hi All,

Though I've not yet tried. I just found out (literaly couple of hours before), that there is an ATI Driver for X200 series.

The following link has drivers for the X200 Chipset.

[http://support.ati.com/ics/support/default.asp?deptID=894&ticketID=822344](http://support.ati.com/ics/support/default.asp?deptID=894&ticketID=822344)

If you are unable to download it, let me know I can email it to someone who would need it.

---

### Post by NickB on 2005-06-06
I got the ATI drivers working (as well as they work :???: ), but it required the following:

1. You have to compile a custom kernel with NO DRM drivers of any kind.
2. You have to apply patches to the fglrx kernel module to build, don't have them handy, but it also required some manual changes to the source (documented elsewhere).
3. DRM is not supported for the xpress 200 yet, and the driver was flaky anyway. 

Better just to get the fglrx64 RPM from the site, alien it, and use the fglrx driver without the kernel module.  It works fine for 2d acceleration, since 3d doesn't work even if you compile the kernel module anyway.

Nick

---

### Post by nandhu on 2005-06-07
[QUOTE=NickB]I got the ATI drivers working (as well as they work :???: ), but it required the following:

1. You have to compile a custom kernel with NO DRM drivers of any kind.
2. You have to apply patches to the fglrx kernel module to build, don't have them handy, but it also required some manual changes to the source (documented elsewhere).
3. DRM is not supported for the xpress 200 yet, and the driver was flaky anyway. 

Better just to get the fglrx64 RPM from the site, alien it, and use the fglrx driver without the kernel module.  It works fine for 2d acceleration, since 3d doesn't work even if you compile the kernel module anyway.

Nick[/QUOTE]
 Where can I find fglrx64 RPM?. Is it from the same support.ati.com site?
Thanks Nick.
- Nanda.

---

### Post by NickB on 2005-06-07
Try here: [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

This HOWTO was fairly helpful, also find patches here: [http://www.linuxquestions.org/questions/showthread.php?threadid=329268](http://www.linuxquestions.org/questions/showthread.php?threadid=329268)

That will help you get started, search the forums here for other tips.

Nick

---

### Post by vialator on 2005-06-17
I have found that I can get direct rendering with the ATi xpress 200m.  Hardware acceleration works, but the problem is that its using my PCI bus for the transfers, because the pci-e fails to load at boot -- it says that the bus has an improper irq (looking thru the code, i found that its not being assigned one) -- i need help here.

To get the acceleration you must be using a 2.6.11 kernel, and u have to get the 8.13.3 drivers from ati's website.  It's under Motherboard chipsets under linux drivers in the knowledge base.  Compile, and insert the module.  you must have agpgart loaded (As a module or into memory), even tho it wont use it (there is no agp), and the "UseInternalAGPGART" option must be "yes".  

What is wrong with the rs480 that it doesnt assign irq's correctly?

---

### Post by NickB on 2005-06-17
[QUOTE=vialator]To get the acceleration you must be using a 2.6.11 kernel, and u have to get the 8.13.3 drivers from ati's website.  It's under Motherboard chipsets under linux drivers in the knowledge base.  Compile, and insert the module.  you must have agpgart loaded (As a module or into memory), even tho it wont use it (there is no agp), and the "UseInternalAGPGART" option must be "yes".[/QUOTE]
That's the driver I had been using, but if I enable DRI I get a stack dump from the kernel and I have to reboot.  Culprit appears to be:
```
Jun 17 20:28:09 localhost kernel: Unable to handle kernel NULL pointer dereference at 0000000000000100 RIP:
Jun 17 20:28:09 localhost kernel: <ffffffff882be9ce>{:fglrx:firegl_igp_get_agpmem_phys_addr+350}
```

Nick

---

### Post by zue on 2005-06-19
[QUOTE=jenik]ok, setting NoAccel to true helped for me. Thanks :)[/QUOTE]

I'm completely new to Linux and I'm having this problem too.  As you can probably guess, I'm more than a little flustered.  I don't suppose anyone could tell me how I can edit this file (or update drivers or do any of the other wonderful things you've all suggested) when I can't log in to gnome?  Please?

Thanks,
Zuzana

Ok new problem.  I found out how to edit something from the recovery terminal (I know I know, total newbie) but I don't have an x11 directory in /etc, or even anything that looks remotely like it.  Where else could xorg.conf be?  I was under the impression that since I at least get a splash screen when I start up (although it doesn't do anything) that that file has to be there somewhere...

---

### Post by Lambert on 2005-06-25
[QUOTE=nandhu]Hi Nick,

I'll try it this evening and will let you know. Thanks for your kind help.

Nanda.[/QUOTE]
 I believe i have this issue but when I type /etc/X11/xorg.conf i get A permission denied return. I'm logged on as root under a command console.

---

### Post by Alexander Kirillov on 2005-06-25
[QUOTE=Lambert]I believe i have this issue but when I type /etc/X11/xorg.conf i get A permission denied return. I'm logged on as root under a command console.[/QUOTE]
 you should type  
<yourfavorite texteditor> /etc/X11/xorg.conf
For example: 
nano /etc/X11/xorg.conf
or
emacs /etc/X11/xorg.conf

If you have no idea what nano or emacs is, use nano. It is mostly self-expalantory (except that you need to know that in explanations at the bottom of the screen, ^ stand for Ctrl)

---

