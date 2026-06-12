---
title: "Restart POST issue"
date: 2008-05-03
forum: x86 64-bit Users
---

### Post by spanglefox on 2008-05-03
hello all,

New(ish) to linux and ubuntu but very happy with the flexibility linux offers!

Having worked through a few issues, such as getting the wireless networking to function fairly normally, I have one main issue.

On selecting restart the system follows this command neatly and the computer brings up the POST screen; however, this is where things go awry. The computer simply hangs. I have to hard switch the power off and on again for the computer to boot.

Experience from other operating systems lead me to have an educated guess that it may be a driver, or similar, remaining in memory after the reboot. A similar issue to when Windows 98(I know, I know) didn't kill all drivers on shutdown?

So, firstly are there any other problems it could be? Secondly are there any ways of ensuring that ubuntu kills all running drivers, TSRs, etc.?

FYI my machine is a Toshiba Satellite A215-4817 with ndiswrapper providing wireless support using the net5211.inf driver. Other than all drivers are ones provided by ubuntu.

Any help greatly received and if I've missed half of the pertinent information, apologies, and I'll endeavour to post!

Thanks and Happy Sailing!

---

### Post by Yellow Pasque on 2008-05-03
Does the system actually finish POST'ing? (i.e. does it beep?) After that it should be looking for the boot device. Since there are no error messages, I'm assuming this is where it gets stuck.

So try this:
Press the restart button and try to enter the BIOS/System Setup (probably by pressing 'Del or 'F1'). If it passes the POST test, it should have no problem letting you do so. Make sure the BIOS is seeing your hard disk properly. Also, what order are your boot devices in? Does it try to boot from the CD first?

---

### Post by spanglefox on 2008-05-05
Well I'm a little further down the line in working out what it could be! Suspicions are pointing directly at the wifi card/drivers.

I managed to stop the wifi drivers loading and when I reset the machine it rebooted no problem. As soon as I use the wifi drivers then the issue appears.

In answer to your question the BIOS does not beep but appears to have finished doing its POST. RAM checks, HDD found and so on.

In addition the boot order is HDD first, then CD then LAN and USB (if installed).

Trying to enter either boot selection menu (by pressing F12) or the BIOS itself, which I think is F2, nothing happens. I do have the most up to date BIOS installed.

As an aside I noticed you have information about install ATI drivers. My computer has a Radeon mobility X1200 card and have been able to install and use 3D support very easily. Using the synaptic package manager. Thought you may have some interest in that :-)

The saga continues......... hehe

---

