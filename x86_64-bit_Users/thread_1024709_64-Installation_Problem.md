---
title: "64-Installation Problem"
date: 2008-12-29
forum: x86 64-bit Users
---

### Post by Ted Kord on 2008-12-29
Hi

I'm unable to install 64-bit Ubuntu 8.10. 

The CD boots properly.
I select "Install Ubuntu ...".
I get the splash screen.
The activity bar starts to fill and completes.
Then it dissapears and a blank screen with a cursor in the top left corner appears (for a few seconds).
Installation almost starts and then I get a login (text) screen. Something like ubuntu@ubuntu$.
'and' that's it.

I've tried messing with BIOS settings to no avail.
When I set the SATA controller to AHCI instead of ATA, the installation proceeds just that little bit further and then I get returned to a login (text) screen.

My system specs are: 

Dell Precision workstation T7400
Intel Xeon CPU X5482 @ 3.2GHz Quad Core
4 GB RAM

Your help will be greatly appreciated as I'd like to get this sorted as quickly as possible. The system currently has 64 bit OpenSuse 11.0 and 64-bit Windows XP installed so I know that 64-bit installations are not a problem. However, I'd like to replace the suse with Ubuntu.

One more thing, as the installation starts, something 'fails' right at the beginning then a few things 'pass' ok and then the text login screen appears.

Thanks.


Ted

---

### Post by Ted Kord on 2008-12-29
I removed the 'quietsplash' option and it turns out that the problem occurs when starting 'ubiquity'.

It's unable to start ubiquity. 
'XStartupError' was raised.

How can I resolve this.


P.S: I have two 512MB NVIDIA QUADRO FX1700 graphics card installed.

Thanks

Ted

---

### Post by Yellow Pasque on 2008-12-29
If the graphical installer is holding you back, you could try the "alternate install" CD.

---

### Post by cariboo on 2008-12-29
I would suggest starting up in safe graphics mode. To select safe graphics mode at the menu screen press F4 and select it. This should get you to the desktop where you can start the installation process. Safe graphics mode will no effect the installation process, as the closed source drivers are installed after the installation is finished. A word of advice, complete all the upgrades before installing the restricted drivers.

Jim

---

### Post by felker2 on 2008-12-29
As advised by cariboo907, I would try the Safe Graphics boot. I expect that that will work.

If that doesn't work, I would try Ubuntu 8.04.1.

And if that doesn't work either, I would try the 32-bit version. I don't expect anything better from that, but you never know.

---

### Post by Ted Kord on 2008-12-29
I've tried both approaches suggested by cariboo907 and Temujin.

The 'safe mode' results in exactly the same situation.

I burnt an 'alternative' CD. The install went through fine but when the system rebooted, I only got a terminal to log in from. No X.

I will now try your suggestions, felker2.

---

### Post by Ted Kord on 2008-12-29
What a relief!!!!:o Thank you all for all the suggestions.

8.04 is installing fine (graphical interface and all). Whey-hey!

However, I've got 8.10 on my laptop and it is absolutely beautiful.

1. How easy is it to upgrade the 8.04 to 8.10.
2. How do I go about it without using a boot CD.

Ted

---

### Post by Therion on 2008-12-29
I'm not saying I *suggest* it, but here's how you upgrade from 8.04 to 8.10 without the CD.

System/Administration/Software Sources and then the "updates" tab.

Down at the bottom, from the drop down menu "Release Upgrade", select "Normal Releases".  

Checking for updates now should tell you that a new release is available for download/install.  
IMO, you do so at your own risk and peril if you have 8.04 running smoothly; but that's the procedure.

---

### Post by felker2 on 2008-12-29
> **Ted Kord said:**
> What a relief!!!!:o Thank you all for all the suggestions.

8.04 is installing fine (graphical interface and all). Whey-hey!



Great. You could press the medal icon in the right lower button of the posts/persons you want to thank.

> **Ted Kord said:**
> 

However, I've got 8.10 on my laptop and it is absolutely beautiful.

1. How easy is it to upgrade the 8.04 to 8.10.


Easy. But you dare to do that? I would expect the 8.10 problem to come back. Ah never mind ... just do it ...worst case is a few minutes of your time wasted.

> **Ted Kord said:**
> 
2. How do I go about it without using a boot CD.

See here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by felker2 on 2008-12-29
OP: check whether your hardware and/or problems are mentioned here: [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

If not, you could consider reporting a bug on launchpad: 
[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by Yellow Pasque on 2008-12-29
> I burnt an 'alternative' CD. The install went through fine but when the system rebooted, I only got a terminal to log in from. No X.
All you probably had to do was install the nvidia driver and reboot, but now you've installed 8.04 (32-bit?)...

---

### Post by Ted Kord on 2008-12-29
Well, you called it felker2. The same problem came back when I upgraded 8.04 to 8.10.

Shame!

---

### Post by felker2 on 2008-12-29
> **Ted Kord said:**
> Well, you called it felker2. The same problem came back when I upgraded 8.04 to 8.10.

Shame!

Have you checked the 8.10 release notes, and the bugs on launchpad? You can check your GPU hardware with lspci, for example:

```
sander@ubuntu810-on-athlon64:~$ lspci | grep -i vga
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
sander@ubuntu810-on-athlon64:~$
```

Maybe dmesg also contains useful information.

---

### Post by phlembob on 2008-12-29
I think you found something out.  Perhaps your machine is better off with the Hardy version 8.04.1.  Intrepid has been problems with graphics interface with Nvidia.  It is more than difficult to work without any video when you upgrade.  8.04.1 Hardy has worked well with all upgrades for 8.04.1.  I used Intrepid for several weeks, but I'm using Hardy only att.  If you read the forums you may find out who prefers what for what reasons.  Nothing is perfect nor should it be expected.

---

### Post by Ted Kord on 2008-12-30
lspci reported fine. 

I tried to install the nvidia drivers (via nvidia directly and ubuntu), still the same problem resulted.

So, I've reverted back to 8.04. Truth be told, I'm not disenchanted at all. 

Thanks everyone.

---

