---
title: "Wireless network catch 22"
date: 2008-08-12
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Average Joe on 2008-08-12
In a moment of weakness I decided to give openSUSE 11.0 a try. I downloaded the KDE4 live cd and installed the OS on my laptop, next to Ubuntu.

When I want to set up my wireless network, Yast is complaining that it cannot connect to the some update server when it tries to run configSUSE (or SUSEconfig), after the set-up configuration. How stupid is that? In order to get your network to work, you need to have a network connection!

I remember I had the same problem when I tried to install openSUSE 10.2 in the past. Apparently this annoying bug has not been fixed, or I am missing something obvious.

Could anybody out there please tell me how to set up my wireless network, without having any network connection? It does not seem to be possible in openSUSE.

---

### Post by dca on 2008-08-12
I can't think of any other way besides being tethered via ethernet cable.  Even still you run the risk of needing to make settings changes to YaST requiring that network connection.  In the end, it primarily will affect laptop users.

---

### Post by dca on 2008-08-12
Asides from d/l the nec packages from another location first.  Windows driver from manf website, ndiswrapper, or MadWifi plus can't forget the missing kmods in openSUSE that don't show up in any repo...

---

### Post by Average Joe on 2008-08-12
I could try connecting with a cable first. That will probably work. But I find it strange that a plug-and-play OS like openSUSE cannot get my wireless to work.

In Ubuntu I didn't need to download any exotic network driver. It just works with the Network Manager and a default "wext" driver. Also, openSUSE does recognize my wireless card, so it does know what it is dealing with. From the very beginning.

I simply don't understand why openSUSE needs a network connection when I want (re-)configure my computer. IMHO that does not make any sense. Configuring is just changing some settings, not updating your PC.

---

### Post by dca on 2008-08-12
The needing a network connection for sysconfig changes I can't understand, it puzzles me as well.  Wireless drivers and support on the other hand is a different animal.  Some distro(s) work out of the box with your wireless, some don't.  It's not the distro's fault or the kernel dev's fault, it's the hardware manufacturers fault.

---

### Post by Average Joe on 2008-08-12
All distro's I have tried so far play well with my wireless card. We are talking about an Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04). I never had to download any driver for it. I am quite sure it actually did work in SuSE 7.2. :) So I don't want to blame Intel for my wireless not to work with openSUSE 11.0.

I think openSUSE 11.0 also has all the tools installed already to work with the card. Like I said, the card is recognized correctly and I can configure the connection. It is just that when I click on "Finish" in Yast, it runs a bunch of processes and the last one (configSUSE) requires a network connection.

As I recall (I am in Ubuntu now) it actually complains about a not being able to connect to an installation medium. I thought that would be the Live CD I used. But it doesn't help when I put it back in. SUSE indicates that the installation source is some http server. I didn't find any option that I can use my CD as an installation medium. In the repositories I can only put in new http/ftp servers.

I should check if it needs an internet connection for every configSUSE process in Yast. Maybe it is not related to the wireless configuration.

---

### Post by dca on 2008-08-13
From what I can remember, I know (for almost a fact) that starting at 10.0 to .1 to .2 to .3 if you d/l the DVD installer, the firmware was included and added/installed prior to installation being complete.  I'm going off an old Dell laptop that had an IPW2200bg wireless card.  
 
Ubuntu back in the 5.10 & 6.06 days (with same laptop) required complete installation, after first reboot you went to an old website that hosted the necessary firmware that had them all listed accordingly: IPW2100, 2200, etc, etc.  You simply d/l & installed the package and after another reboot it automaigically worked w/ no other user intervention.
 
Somewhere between then and now it possibly either got merged into kernel or something else done due to Intel warming up more and more to open source.

---

### Post by Growbag on 2008-08-13
If you ran the update config tool, it adds online repos.

In yast, go into software sources and disable everything but the CD and try again.

It's a bit silly sometimes!

---

