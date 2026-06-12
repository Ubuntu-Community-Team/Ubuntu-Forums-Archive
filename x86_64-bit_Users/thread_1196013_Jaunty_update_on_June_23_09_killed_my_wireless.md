---
title: "Jaunty update on June 23 09 killed my wireless"
date: 2009-06-24
forum: x86 64-bit Users
---

### Post by rwgehl on 2009-06-24
After reseting my Compaq f700 after a Jaunty update, my wireless is completely dead. Output of iwlist:
> lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

relevant lspci:
> 03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

In WICD, my wireless has always been auth0 with Wext as the WPA supplicant driver. I use madwifi. I tried to change to the restricted hardware driver - no luck.

According to synaptic, the updates on the 23rd were:
> Upgraded the following packages:
app-install-data-commercial (11.9.04) to 11.9.04.2
app-install-data-partner (11.9.04) to 11.9.04.2
compiz (1:0.8.2-0ubuntu8) to 1:0.8.2-0ubuntu8.1
compiz-core (1:0.8.2-0ubuntu8) to 1:0.8.2-0ubuntu8.1
compiz-gnome (1:0.8.2-0ubuntu8) to 1:0.8.2-0ubuntu8.1
compiz-plugins (1:0.8.2-0ubuntu8) to 1:0.8.2-0ubuntu8.1
compiz-wrapper (1:0.8.2-0ubuntu8) to 1:0.8.2-0ubuntu8.1
file (4.26-2ubuntu3) to 4.26-2ubuntu4
gstreamer0.10-esd (0.10.14-1) to 0.10.14-1ubuntu0.1
gstreamer0.10-plugins-good (0.10.14-1) to 0.10.14-1ubuntu0.1
gstreamer0.10-plugins-good-dbg (0.10.14-1) to 0.10.14-1ubuntu0.1
gstreamer0.10-pulseaudio (0.10.14-1) to 0.10.14-1ubuntu0.1
gvfs (1.2.2-0ubuntu1) to 1.2.2-0ubuntu2
gvfs-backends (1.2.2-0ubuntu1) to 1.2.2-0ubuntu2
gvfs-bin (1.2.2-0ubuntu1) to 1.2.2-0ubuntu2
gvfs-fuse (1.2.2-0ubuntu1) to 1.2.2-0ubuntu2
hal (0.5.12~rc1+git20090403-0ubuntu2) to 0.5.12~rc1+git20090403-0ubuntu3
libdecoration0 (1:0.8.2-0ubuntu8) to 1:0.8.2-0ubuntu8.1
libgvfscommon0 (1.2.2-0ubuntu1) to 1.2.2-0ubuntu2
libhal-storage1 (0.5.12~rc1+git20090403-0ubuntu2) to 0.5.12~rc1+git20090403-0ubuntu3
libhal1 (0.5.12~rc1+git20090403-0ubuntu2) to 0.5.12~rc1+git20090403-0ubuntu3
libmagic1 (4.26-2ubuntu3) to 4.26-2ubuntu4
linux-backports-modules-jaunty-generic (2.6.28.11.15) to 2.6.28.13.17
linux-generic (2.6.28.11.15) to 2.6.28.13.17
linux-headers-generic (2.6.28.11.15) to 2.6.28.13.17
linux-image-generic (2.6.28.11.15) to 2.6.28.13.17
linux-libc-dev (2.6.28-11.42) to 2.6.28-13.44
linux-restricted-modules-common (2.6.28-11.15) to 2.6.28-13.17
linux-restricted-modules-generic (2.6.28.11.15) to 2.6.28.13.17
python-cupshelpers (1.1.3+git20090218-0ubuntu19.1) to 1.1.3+git20090218-0ubuntu19.2
system-config-printer-common (1.1.3+git20090218-0ubuntu19.1) to 1.1.3+git20090218-0ubuntu19.2
system-config-printer-gnome (1.1.3+git20090218-0ubuntu19.1) to 1.1.3+git20090218-0ubuntu19.2
tzdata (2009f-0ubuntu1) to 2009j-0ubuntu0.9.04
tzdata-java (2009f-0ubuntu1) to 2009j-0ubuntu0.9.04
xserver-xorg-video-intel (2:2.6.3-0ubuntu9) to 2:2.6.3-0ubuntu9.3

Installed the following packages:
linux-backports-modules-2.6.28-13-generic (2.6.28-13.14)
linux-headers-2.6.28-13 (2.6.28-13.44)
linux-headers-2.6.28-13-generic (2.6.28-13.44)
linux-image-2.6.28-13-generic (2.6.28-13.44)
linux-restricted-modules-2.6.28-13-generic (2.6.28-13.17)

There is nothing in those updates that struck me as a wireless-killer, but maybe I'm missing something.

And yes, my wireless switch is on. :D I've read that Ubuntu likes us to press the wireless hotkey for 5 seconds to switch it on or off, but I don't have a hotkey; I have a hard switch on the front.

Prior to the update, my wireless LED light would blink orange and blue based on activity.

---

### Post by empty_spaces on 2009-06-24
<quote>
linux-generic (2.6.28.11.15) to 2.6.28.13.17
linux-headers-generic (2.6.28.11.15) to 2.6.28.13.17
linux-image-generic (2.6.28.11.15) to 2.6.28.13.17
</quote> 

It looks like your kernel was updated from 2.6.28.11 to 2.6.28.13.
It is very likely that if you boot into your earlier (2.6.28.11) kernel at the grub screen, your wireless will work as before.
Maybe the new kernel has issues with your wireless, you may want to do some google searching on that to see if anyone else has this issue.

Personally, I use the 2.6.30-020630rc8 kernel that I manually installed.

---

### Post by rgehl on 2009-06-24
Good call, ES, but it's not the kernel. I booted up in the two previous ones, but no change. Wicd doesn't detect any wireless networks. I know my wireless net is working, because I am connected on my wife's computer.

In fact, the wireless on the compaq seems completely dead:
> iwlist scan
lo      Interface doesn't support scanning.

eth0    Interface doesn't support scanning.

pan0    Interface doesn't support scanning.

---

### Post by rwgehl on 2009-06-25
I figured it out. My Atheros wireless was dependent upon a script by Bob Nelson (t [http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)). I had forgotten that the script needs to be reinstalled after each kernel update. I ran the script and boom - right back where I need to be. Anyone dealing with Atheros problems should take a look at Nelson's page.

---

