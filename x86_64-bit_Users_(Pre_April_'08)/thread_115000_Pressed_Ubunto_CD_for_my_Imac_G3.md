---
title: "Pressed Ubunto CD for my Imac G3"
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by socktan on 2006-01-09
Hi all.

I have an iMac G3 with no operating system... it's quite useless as it sits in storage.

It's a tray load model, so it will not read burned CD-R discs, thus, I'm not able to make use of the ISO downloads.

I wanted to ask the community if the free pressed CD's are cross platform, or do I need to request mac-specific discs?  Or maybe pressed CD's are not available for my purpose.

Thanks in advance,

-
Chris.

---

### Post by stuporglue on 2006-01-09
There are Mac pressed CDs but you'll need to choose what type for them to send you. There are Mac, x86, and AMD-64 CDs. They come with both the live and install CDs in the same package. 

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

We had a pretty old G3 tray loader and it never had trouble reading burned disks. Maybe it depends on the disk?

---

### Post by Suger on 2006-01-10
Well, I have two G3 333 Mhz tray loader iMacs here and one will read them, the other not. Strangely enough, it's the older one (by something like 3 months) that reads them.

If you are a little OpenFirmware savvy and have another *nix running machine, you can try an NFS install.

---

### Post by socktan on 2006-01-10
Thanks everyone.  

I've tried everything to get the iMac to read burned CDs - even installing slim drives from PC laptops.  It will then read burned discs without trouble but *will not* boot up from them.

Perhaps I will try a different disc type before I put in the request for pressed discs.

Thanks again

-
Chris.

---

### Post by Paradise on 2006-01-10
Make sure your firmware is up to date.  The old iMacs needed some help with booting and Apple released a Firmware updater; albeit some time ago. Check [http://docs.info.apple.com/article.html?artnum=86117]("http://docs.info.apple.com/article.html?artnum=86117")
for which level you should be at.

I am working on a Bondi with Badger-Live. I found I have to hold the C key down anyway, just like booting to a Apple CD.  I also have found some graphics issues which I am currently trying to resolve.  

Good Luck:p 

P

---

### Post by 3rdalbum on 2006-01-16
When you go to ShipIt, you get the option of asking for one of a few "normal requests", or a "custom request". Choose the "1 PC, 1 64-bit, 1 Mac" option; it'll get to your house quicker.

With those iMacs, the trick is to buy Audio CD-Rs. You know, the ones which are designed to be used in the CD recorders in hi-fis. I've burnt a Live CD onto one of those and it has worked flawlessly in my tray-loading iMac. Sure, those CDs cost a little more, but it's worth it.

---

### Post by pandan on 2006-02-09
I have an orange iMac G3 333MHz 96 MB RAM

I got pressed CD's of Ubuntu 5.10
I updated the OS to Mac OS9.2  from OS 9.0
Somehow I think this updated the firmware and allowed me to boot from CD
by pressing "C" instead of having to use BootX.

The install had some problems, so after some trial and error I found that installing with 'expert' option got me through ok.  Why? I was somehow not added to the sudoers list so needed a root password and account.  (added manually)

I find that Gnome is actually bearable once I switch from 24-bit color to 16-bit.

But I prefer using the following setup:
Installing: XFCE, abiword (word processor) and alacarte (menu editor)
Dialup using: wvdial (used alacarte to add menu item)
Enabled: gnome-volume-manager (to autodetect USB key)

I this gives someone out there some encouragement to make their old iMac into a very functional computer once again.
Details on how I did most of these things are in other threads.

---

### Post by 3rdalbum on 2006-02-10
[QUOTE=pandan]I have an orange iMac G3 333MHz 96 MB RAM

I got pressed CD's of Ubuntu 5.10
I updated the OS to Mac OS9.2  from OS 9.0
Somehow I think this updated the firmware and allowed me to boot from CD
by pressing "C" instead of having to use BootX.[/QUOTE]

The iMac is "New World", so it has always been able to boot from CD by using the "C" key. BootX doesn't work on our Macs.

[QUOTE=pandan]The install had some problems, so after some trial and error I found that installing with 'expert' option got me through ok.  Why? I was somehow not added to the sudoers list so needed a root password and account.  (added manually)[/QUOTE]

That's very strange behaviour. When I specified a root password, my "normal user" wasn't added to the sudoers list and of course I couldn't log in as root. When I installed WITHOUT a root password, my normal user account was added to the sudoers.

---

