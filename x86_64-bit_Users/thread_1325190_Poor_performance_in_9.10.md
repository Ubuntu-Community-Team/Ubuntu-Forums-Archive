---
title: "Poor performance in 9.10"
date: 2009-11-13
forum: x86 64-bit Users
---

### Post by niw_uk1964 on 2009-11-13
I am having performance issues in 9.10. They are so bad I am considering moving to Windows for now.

The problems are:

1. Slow network browsing - slow to browse shares on my NAS box and Windows machines
2. Slow/unresponsive/jerky mouse pointer movement
3. Slow/unresponsive/jerky scrolling in Firefox
4. Slow page loading in Firefox (downloads are fine and full speed).
5. Poor performance in VLC and MPlayer (hesitant playback, dropped frames) - Totem Movie Player seems to be much better in this respect).

This is a fresh install. Hardware is:

J&W AMD780G mini-ITX motherboard with ATI Radeon 3200 IGP using 512MB of shared RAM for video
4GB DDR2 system memory
AMD Phenom II X4 905e 2.5GHz cpu

I am using the proprietary ATI drivers for the IGP.

On a freshly booted system everything is fine and speedy. However, before long and with multiple tabs open on Firefox things begin to bog and I see the issues I have listed above. The only recourse appears to be a reboot every few hours. Closing Firefox doesn't improve things.

Gnome Monitor shows no excessive cpu utilisation (irrespective of whatever mode it is operating in: power on demand etc), there's no excessive network traffic, plenty of free system memory (>2GB), no drive thrashing. Nothing obvious is bogging the system down.

I've checked the bios settings and there is nothing obvious in there causing problems that I can see. AMD's Cool & Quiet is enabled in the bios to allow cpu frequency scaling to happen within the o/s - manually overriding that within the o/s to operate at the maximum of 2.5GHz has no appreciable benefit wrt the problems I am seeing.

The only thing I think it might be related to is USB polling/interrupts. I say this because using a USB/wireless keyboard seemed to make matters worse and the keyboard would often not respond. I changed this out for a ps/2 item, but my mouse is still USB. I have also noticed that the system seems slow to recognise any USB flash drive that is plugged in and sometimes it fails to detect them altogether (ironically I get fantastic USB transfer speeds in excess of 45MB/s on my portable drive).

Any ideas? TIA.

---

### Post by joenieburg on 2009-11-13
Hello, I was also having slow performance with Ubuntu9.10
I have al laptop d630 from Dell.
Before 9.10 I have used 8.04.8.10 and 9.04 and didn't have any problems.
Today at my work started my laptop and forgot to select to windows (I have multiboot) There was no performance problem.
So For me it was simple .At work I use 2 monitors. At home only one.
In the bios from my laptop I can select 
use the internal monitor
instead off the docking monitor.
After changing this setting in the Bios my Ubuntu works normal again

No utilization. (ok almost none around 6%)

I hope this will give u a hint. And if u can plugin a second monitor mayby your trouble go away.

J.

---

