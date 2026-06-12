---
title: "Nothing displayed on my destop"
date: 2008-06-24
forum: x86 64-bit Users
---

### Post by contactmayankjain on 2008-06-24
Hi,

I have installed Ubuntu 64 bit on my Dell core2Duo Laptop. After installing the updates nothing is displayed on my Desktop:confused:. Right click also doesn't work on Destop:(. From Menu when I try to open my Home folder nothing got displayed . When I try to browse the folder from my music player it kills my music player:mad:. I have googled this problem and have tried all the possible solutions I can find out, reconfiguring my X11. Don't know which package have done all this mess. Please help me otherwise I have to switch to Windows :(

---

### Post by kuja on 2008-06-24
make/model/[detailed ]specifications of the computer?

---

### Post by ad_267 on 2008-06-24
Have you restarted after the updates?

---

### Post by contactmayankjain on 2008-06-24
yes I have restarted my system several times :).

---

### Post by contactmayankjain on 2008-06-24
Configuration of my system. 

-Intel(R) Core(TM)2 Duo Processor T5550
-1.83 GHz, 2MB Cache, 667 MHz FSB
-15.4" Widescreen WXGA (1280x800) TFT Display with
-Integrated 2.0 mega pixel web cam
-2GB (2 X 1024MB) 667MHz Dual Channel DDR2 SDRAM
-160GB SATA Hard Drive
-Internal 8X DVD+/-RW Combination Drive with dual
layer write capabilities
Intel(R) Integrated Graphics Media Accelerator X3
100
-Intel(R) PRO/Wireless 3945 Dual Band 802.11a/g 54
2
Mbps Wireless Mini Card
Integrated Stereo Sound
-Dell(TM) Wireless 355 Bluetooth Module
-9-cell Lithium Ion Primary Battery
8-in-1 media card reader
-Dell(TM) Keyboard with Touchpad (English)
-Dell(TM) Travel Remote Control
Noise Isolation Ear Buds
Dell(TM) Media Direct
Internal 56K Modem


Please let me know if you require any other information.

---

### Post by ad_267 on 2008-06-24
It sounds like it's a problem with the nautilus file manager which also controls the desktop.

Try going to system - administration - synaptic package manager. Click reload then mark all upgrades. Search for nautilus and mark the package nautilus for reinstallation then apply. I guess it wouldn't hurt to mark all the installed nautilus packages for reinstallation.

---

### Post by contactmayankjain on 2008-06-24
I have already tried this but no luck. :(

---

### Post by contactmayankjain on 2008-06-24
Can you let me know the manual way of doing this and the place from where I can get the stable package which I can replace with my pre-installed packages. Any way to use the older version of the package.

---

### Post by ad_267 on 2008-06-24
Can you go to a terminal and type "nautilus" and post the output here.

---

### Post by contactmayankjain on 2008-06-24
It hangs :(

---

### Post by ad_267 on 2008-06-24
> **contactmayankjain said:**
> It hangs :(

:( That's not cool. Hopefully someone else can help you, I don't know what else you can do.

---

### Post by contactmayankjain on 2008-06-24
even nothing is shown in /var/log/messages.

---

### Post by contactmayankjain on 2008-06-24
The problem have occured afer I updated my UBuntu. So getting the older package will definately be the solution I think what say.. ??

---

### Post by ad_267 on 2008-06-24
I think you can do "sudo apt-get remove nautilus"

then "sudo apt-get install nautilus=version_number"

I think there's a "force version" option in synaptic too. This only works if the version specified is available from the repositories.

I would also recommend making sure there is a bug about this on launchpad and if there isn't then file a bug there so that this gets fixed.

---

### Post by contactmayankjain on 2008-06-24
I shall try this in the evening..thx :popcorn:

---

### Post by ad_267 on 2008-06-24
You might want to keep an eye on this thread: [http://ubuntuforums.org/showthread.php?t=839127](http://ubuntuforums.org/showthread.php?t=839127)

Someone else is having problems with nautilus after the update too.

---

### Post by contactmayankjain on 2008-06-24
Have tried doing all this but no luck what more can I try..??

---

### Post by contactmayankjain on 2008-06-24
Jun 24 19:22:40 mayank-laptop kernel: [  149.127292] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 24 19:22:42 mayank-laptop kernel: [  151.297438] sky2 eth0: Link is up at 10 Mbps, half duplex, flow control none
Jun 24 19:22:42 mayank-laptop kernel: [  151.300210] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 24 19:38:39 mayank-laptop -- MARK --
Jun 24 19:39:04 mayank-laptop kernel: [  670.631250] nautilus[12487]: segfault at 0 rip 7f65fe57efde rsp 7fff09f8db20 error 4
Jun 24 19:39:06 mayank-laptop kernel: [  671.692658] nautilus[12506]: segfault at 0 rip 7fa159e9ffde rsp 7fff658ae440 error 4
Jun 24 19:46:33 mayank-laptop kernel: [  922.561758] sky2 eth0: Link is down.
:confused::(

---

### Post by ad_267 on 2008-06-24
> **contactmayankjain said:**
> Jun 24 19:22:40 mayank-laptop kernel: [  149.127292] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 24 19:22:42 mayank-laptop kernel: [  151.297438] sky2 eth0: Link is up at 10 Mbps, half duplex, flow control none
Jun 24 19:22:42 mayank-laptop kernel: [  151.300210] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 24 19:38:39 mayank-laptop -- MARK --
Jun 24 19:39:04 mayank-laptop kernel: [  670.631250] nautilus[12487]: segfault at 0 rip 7f65fe57efde rsp 7fff09f8db20 error 4
Jun 24 19:39:06 mayank-laptop kernel: [  671.692658] nautilus[12506]: segfault at 0 rip 7fa159e9ffde rsp 7fff658ae440 error 4
Jun 24 19:46:33 mayank-laptop kernel: [  922.561758] sky2 eth0: Link is down.
:confused::(

When do you get that message?

---

### Post by contactmayankjain on 2008-06-25
firefox was running properly on my system. When I click on Browse button in some website to upload a file, my firefox got closed and in /var/log/messages this is present.

---

### Post by ad_267 on 2008-06-25
> **contactmayankjain said:**
> firefox was running properly on my system. When I click on Browse button in some website to upload a file, my firefox got closed and in /var/log/messages this is present.

Is that still happening? You might want to start a new thread if you keep having that problem.

---

### Post by contactmayankjain on 2008-06-25
what is still hapening the segmentation falult? yes it it :(
what's the use of starting new thread althougl it all these problems are dur to same nautilus. I have tried all what has been suggested but nothing works. It all have wasted so much of my time. It would be better if I had reinstall my system. I think re install will not help because after installing updates I will face same problem. What If I install kubuntu.. it doesn't have nautilus... looks that is a better solution.. what say.??

---

### Post by ad_267 on 2008-06-25
> **contactmayankjain said:**
> what is still hapening the segmentation falult? yes it it :(
what's the use of starting new thread althougl it all these problems are dur to same nautilus. I have tried all what has been suggested but nothing works. It all have wasted so much of my time. It would be better if I had reinstall my system. I think re install will not help because after installing updates I will face same problem. What If I install kubuntu.. it doesn't have nautilus... looks that is a better solution.. what say.??

Sorry I was getting confused. Thought this was a different thread and that this was an unrelated problem. Well if you have enough time I would say you could try installing and apply the updates and see if it works but it's up to you, if you want to give KDE a go then go for it. I've heard that KDE 4 is still pretty buggy so you might want to stick with KDE 3.5 at the moment.

---

### Post by contactmayankjain on 2008-06-25
thanks for your suggestion. Do I need to do a fresh installation from CD or there is any other way to do it. I have downloaded the iso of kubuntu and I don't want to do any fresh installation is there any way out?

---

### Post by ad_267 on 2008-06-25
> **contactmayankjain said:**
> thanks for your suggestion. Do I need to do a fresh installation from CD or there is any other way to do it. I have downloaded the iso of kubuntu and I don't want to do any fresh installation is there any way out?

You could just try installing the Kubuntu-desktop package. There's also Xfce which you can install with the xubuntu-desktop package. When you log in you can choose what session you want, either Gnome or KDE.

If you've already downloaded the kubuntu cd you can add it as a source of packages so you don't have to re-download the kubuntu-desktop package.

---

### Post by contactmayankjain on 2008-06-26
> **ad_267 said:**
> You could just try installing the Kubuntu-desktop package. There's also Xfce which you can install with the xubuntu-desktop package. When you log in you can choose what session you want, either Gnome or KDE.

If you've already downloaded the kubuntu cd you can add it as a source of packages so you don't have to re-download the kubuntu-desktop package.
Can you please let me know the complete procedure for the same?

---

### Post by ad_267 on 2008-06-26
Ok if your Ubuntu is still sort of usable you can put the Kubuntu cd into your cd drive and a popup should come up saying "would you like to open it with the package manager." Open up the package manager and go to Settings - Repositories. Go to the "Third-Party Software" tab and just make sure that the cdrom is listed there. If not you can click "Add CD-ROM to add it. Then just search for the kubuntu-desktop package and mark it for installation and hit apply.

Then log out and at the log in screen there should be a "Sessions" button. Click that and select the KDE session and log in.

---

