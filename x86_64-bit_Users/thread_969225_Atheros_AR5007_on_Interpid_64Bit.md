---
title: "Atheros AR5007 on Interpid 64Bit"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by omuony on 2008-11-03
I Have a copaq c776NR, which I have been using with Hardy for Months, However, recently i updated it and realized the atheros wireless was not working. When I load a lower Kernel from the boot menu list, it works. 

Now my problem is, interpid is detecting my card as 

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I have been using the live version of Interpid and I want to install it. How can I make the wireless work? Will I have to install AR5007 or it caan work with this because it only shows wired network under network manager

---

### Post by stanley drew on 2008-11-04
I have the exact same problem and hardware so I'm bumping this. I have a fresh install of 8.10 for amd64. I used to run 8.04 32-bit  with madwifi for atheros AR5007 and i'm wondering what i should do to get my wireless card working now that i've made the jump to 64-bits. Somebody help please! Thanks!

---

### Post by Peter09 on 2008-11-04
Not sure if this thread can help

[http://tennessee.ubuntuforums.com/showthread.php?t=902860](http://tennessee.ubuntuforums.com/showthread.php?t=902860)

---

### Post by sblive on 2008-11-04
Just a quick hAxXx for this problem:

sudo apt-get install linux-backports-modules-2.6.27-generic
sudo apt-get install linux-backports-modules-interpid-generic

Then turn off your proprietary driver for this Atheros card using 'drivers' screen or modprobe with -r  switch every module that starts with ath.

Next step is so simply:

sudo modprobe ath5k

Optionally, you may want to add 'ath5k' at the end of your /etc/modules.

This helped me with LG E-200 notebook.

---

### Post by stanley drew on 2008-11-05
hmm still nothing is working. i have ath5k running right now with no luck, and compiling and installing the madwifi ath_hal and ath_pci didn't work either. anymore ideas out there??

---

### Post by sblive on 2008-11-05
have you turned off madwifi before probing ath5k?

---

### Post by drs305 on 2008-11-05
The 8.10 release notes discuss issues with the ath5 wireless drivers and a possible workaround on how to solve the problem: [releasenotes/810]("http://www.ubuntu.com/getubuntu/releasenotes/810")

---

### Post by stanley drew on 2008-11-05
I definitely unloaded both the ath_pci and ath_hal modules before adding ath5k, rebooting after every change. I've tried it a couple times without any luck. I'm checking out the release notes now.

---

### Post by stanley drew on 2008-11-05
The release notes do explain how to get the ath5k driver but nothing after that. I've been looking on the madwifi site too for open tickets relating to this issue with no luck. I've been googling this like crazy and nobody seems to have a different solution.

---

### Post by stanley drew on 2008-11-05
solved!

It turns out the problem I was having was with wicd. Switching back to network-manager fixed the problem and I am now surfing wirelessly. Thanks for your help everybody.

---

### Post by stanley drew on 2008-11-05
I forgot to mention that ath5k is the driver that eventually worked with network-manager and not wicd.

---

### Post by stanley drew on 2008-11-20
So just to cap this off I did eventually get wicd to work in 64-bit intrepid. It turns out wicd wasn't detecting my wireless interface. After I added wlan0 as the wireless interface under preferences everything was fine.

---

### Post by smooth3006 on 2008-11-23
will this method work with hardy ( 8.04 )x64 as well with an atheros 5007 ?

---

### Post by 4lc0h0l1c on 2008-11-25
Hi,
I came across this thread while searching for a related subject and in case the steps here don't work for someone in the future keep this in mind:

I just switched to OpenSUSE 11.0 and after several days of struggling to get my Atheros 5007 working it ended up being rather simple.  The version of madwifi in the repository, 0.9.4-1, did not work with the Atheros card but compiling madwifi-hal-0.10.5.6-r3875-20081105 worked fine and that's all I had to do.  This card also reports itself as Ath242x with lspci.  I don't know if that's supposed to be that way or a bug in the card.

---

