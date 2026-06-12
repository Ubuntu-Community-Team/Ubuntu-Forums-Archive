---
title: "Microsoft Virtual PC under Wine"
date: 2008-07-11
forum: Wine
---

### Post by mavix on 2008-07-11
Is it possible to run Microsoft Virtual PC under Wine? I tried VPC 2004 and it installed perfectly, and when I run it the splash screen shows briefly, and then it quits. Does anyone know how I can get it to run?

---

### Post by Rhubarb on 2008-07-11
You'd be better off running a native Virtual machine using Virtualbox or VMware.
There are tutorials here in the Ubuntu forums that can help you with both.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by mavix on 2008-07-11
Thanks, I think I'll try VirtualBox. I would download VMWare, but having a rather outdated dial-up modem means that a 100Mb download is out of the question. I might soon be getting it from a friend though. Which would you say is better for running Windows XP; VirtualBox or VMWare?

---

### Post by Rhubarb on 2008-07-11
I prefer using VirtualBox myself, it's very easy to get going.
Don't grab the OSE of virtualbox, grab the virtualbox binary (as it has a few more features than the OSE has).

---

### Post by alfalfa31 on 2008-07-11
I totally agree that VirtualBox is the best bet.  VMWare is great, and I use it professionally every day, but VB is just easier to get going.

The MS product is lame because it can only install <ghasp!!> MS products.  What good is that?

---

### Post by mavix on 2008-07-12
OK thanks. I installed VirtualBox and its great! I especially like its seamless desktop integration

---

### Post by xfree07 on 2008-09-21
There are reason's though that you would want to run VirtulPC on Wine if possible... It's tough to run anything previous to Windows XP on Virtual Box.  I'm sure Windows 98 or 95 would be easier to set up in VMWare, but VMWare costs $$ and VirtualPC is free.

I was trying to set up an automatically reconnecting tunnel at work (long story)... following this guide: [http://freshme.at/index.php?page=articles&op=readArticle&id=8&title=Cant-access-remote-desktop-via-SSh-remote-port--Use-a-Windows-98-VM]("http://freshme.at/index.php?page=articles&op=readArticle&id=8&title=Cant-access-remote-desktop-via-SSh-remote-port--Use-a-Windows-98-VM") (Among other pages on that site).

If anyone has been able to run VirtualPC with Wine, I'd be VERY interested in understanding how it was done.

---

### Post by lakersforce on 2008-09-22
According wikipedias comparisons of virtual machines, VMware is by far the best (if you by best means fastest and most feature full). Use Player, not server. Some posts on this forum states that the server should be as fast as the player, but this is definitely not my experience. In my experience, player is 2-20 times faster than server. VMware Player and Server are both gratis to use. Both VMware and VirtualBox are not free software.

---

### Post by asdfoo on 2008-09-22
> **xfree07 said:**
> There are reason's though that you would want to run VirtulPC on Wine if possible... It's tough to run anything previous to Windows XP on Virtual Box.  


I've found that qemu works better for running Windows 95 and 98.  Both of which freeze during install on VirtualBox - It's a known issue and they don't seem too interested in fixing it.


The easiest way to use qemu is to install the qtemu package which gives you a nice GUI for configuring and launching images.

---

### Post by xfree07 on 2008-09-22
> **lakersforce said:**
> According wikipedias comparisons of virtual machines, VMware is by far the best (if you by best means fastest and most feature full). Use Player, not server. Some posts on this forum states that the server should be as fast as the player, but this is definitely not my experience. In my experience, player is 2-20 times faster than server. VMware Player and Server are both gratis to use. Both VMware and VirtualBox are not free software.

I'm pretty sure VirtualBox is free... there's even an open source version!  [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads").  Do you mean VMWare player and VMware Server?

I haven't tried Qemu, I'll check it out.  I think once you have mouse pointer integration, CPU scaling/idling, good video performance, etc.  It's hard to go back to anything that doesn't have those features though (VirtualBox).

---

### Post by Gcentrex on 2008-09-22
VirtualBox is good I use it a lot but VMware beta 6.5 is also installed since it support USB 2.0 pass throught to iTunes can connect to my iPhone plus it has DirectX 9.0c support (DirectX 8.1 is perfect 9 is almost their in the current Beta) so it can run the few things I still want to use that are currently not working in wine without needing to have an XP partition and reboot when ever I need to run them.

---

### Post by killer_d76 on 2008-09-22
i have successfully installed MS Office 2007 on ubuntu using Wine 1.1.4 and i have created a "how to" thread as well, i even included the necessary dll to make it work properly click on the link below

[http://ubuntuforums.org/showthread.php?t=922963]("http://ubuntuforums.org/showthread.php?t=922963")

here are somes pics..

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85585&d=1221701314[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85586&d=1221701314[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85611&d=1221715679[/IMG]

---

### Post by killer_d76 on 2008-09-22
ooopppsss wrong post!.. hehehe sorry.. i use VirtualBox too.. works flawlessly for me.. :guitar:


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=84547&d=1220860424[/IMG]

---

### Post by lakersforce on 2008-09-23
> **xfree07 said:**
> I'm pretty sure VirtualBox is free... there's even an open source version!  [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads").  Do you mean VMWare player and VMware Server?

Seems like I was a little fast...virtualbox is licensed under both a proprietary and GNU GPL license.

[quote=Wikipedia]

There are two versions of the VirtualBox software.

The full VirtualBox package comes under a proprietary license, which allows using the software free-of-charge for personal and educational use and evaluation of the product.[17] Licenses for commercial use of the full VirtualBox package can be purchased from Sun.

A second version called the VirtualBox Open Source Edition (OSE) is free software released under the GNU General Public License (GPL), from which the following closed-source features are missing:[18]

    * The built-in Remote Desktop Protocol (RDP) server
    * USB support (see above) and the combination of running the RDP server with support of remote USB devices
    * iSCSI support for virtual hard disks (see above)

The free software edition was accepted into Debian unstable on 30 August 2007.[19] They are also available from backports.org in etch-backports for Debian etch users. VirtualBox OSE packages are included in the universe repository of Ubuntu 7.10 and newer[20], and are packaged into openSUSE since the 10.3 release.[/quote]

Yes!

---

### Post by touristguy87 on 2008-10-27
"I'm pretty sure VirtualBox is free... there's even an open source version! [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads). "

xVB is free for personal use  and works fine with ubuntu 8.04 on WinXP x86


...killer...who in Sun holds the script that will invert my Linux on WinXP config to a WinXP on Linux config ;)

that looks schweet

you just gotta believe that someone there calls-up Bill Gates on a regular basis just to let him know

---

