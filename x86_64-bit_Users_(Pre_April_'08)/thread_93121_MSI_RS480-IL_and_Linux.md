---
title: "MSI RS480-IL and Linux"
date: 2005-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by yelloguy on 2005-11-21
Hi,

This is my first post to this forum so, hello all!

I have searched the forums for any discussions pertaining to this mobo and have seen one post (no answers) with problems similar to mine.  So I thought of bringing up the subject again.

I built this computer back in March 2005 with an MSI RS480-IL mATX mother board.  I am using the on board ATI X200 video chip and the on board sound (RealTek) for now.  I have the Logitech MX500 duo USB wireless keyboard and mouse combo and a D-Link (DWL 610?) PCI wireless card.  Finally, I have an old Hauppauge tuner card (WinTV Go) in another PCI slot.  And that is pretty much all the hardware.  Oh and I have 512 MB memory (I forget which brand) which is shared (32 MB) with the integrated video.

The problem is, I have NEVER been able to install Linux on this rig.  I used to have Mandrake 10.1 and Suse 9.2 on my previous computer but for this one, I downloaded the 64 bit versions of these distros but neither of them would install. The installation hangs while detecting hardware.  I have tried the various switches that Mandrake installation offers (-noacpi, etc etc). I also tried the old 32-bit editions for Mandrake and Suse but had the same problems.  I gave up and forgot all about it all until someone suggested Ubuntu recently.  So I downloaded the 64-bit version of Kubuntu (since I prefer KDE) and gave it a spin.  But I am having similar problems again.  The installation proceeds to a point and then hangs.  I believe it showed me a message saying it is starting some daemons (processor log daemons?) and hung there for 6-7 minutes.  Sorry if this is vague.  I will post the exact messages I get if any of you feel like helping.

I have tried removing the USB keyboard/mouse and attaching a PS2 keyboard in its place (I do not have a PS2 mouse) but that only makes it hang at a different message.

The thing with all this is that I have no real need to have Linux and I have very little time to spend for this, but the sheer challenge of a problem like this is killing me :-) So I thought I would ask the smart people here if they have any pointers for me to try in my free time (heh, like, 30 seconds on the weekend).

Thanks in advance.

---

### Post by yelloguy on 2005-11-21
BTW, Live CD boot hangs in an identical fashion too.

---

### Post by Jiilik on 2005-11-21
I have this mobo, and it works fine for me with breezy.  If you are installing hoary by any chance, it simply will not work.

It works for me with acpi, etc. but only after I updated the BIOS using the flash utility from the manufacturers website.  This was my one major snag.

---

### Post by yelloguy on 2005-11-21
Thanks Jiilik.  I have the latest release which [I believe] is Breezy.  And AFAIK I have the latest BIOS.  I will check both tonight.  However, my impression from searching the net is that it is hit and miss with this mobo.  Some have had success while others, randomly, have had nothing but failures.

Also, it does not seem like the successful ones have had a very easy life either.  How is yours doing on the ATI X200 front?  Are you using this [integrated] chip or do you have a video card in the PCI-E slot?

---

### Post by korakde on 2005-12-04
Hi,
Ive had a rather dissapointing experiance myself with Uuntu on this very same mobo. I am also using this Xpress200 video chipset. Ive even started athread on the same (Live CD does not work  [http://www.ubuntuforums.org/showthread.php?t=95776)](http://www.ubuntuforums.org/showthread.php?t=95776)). I however have the ubuntu in GNOME. If anone comes up with a solution, please inform us GNOME guys too by making a post there too

---

