---
title: "openSUSE 10.3 Beta 2 Released"
date: 2007-08-24
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Dark Star on 2007-08-24
[IMG]http://www.imgx.org/files/3411_rezia/800px-SuSE-logo.svg.png[/IMG]The openSUSE team is working hard on the new version of their free Linux operating system, scheduled for release somewhere in October, very close to the Ubuntu 7.10 release. They are proud to announce today the second beta version of openSUSE 10.3. This beta comes with the latest and greatest Linux kernel 2.6.22.3, GLibc 2.6.1 and an improved YaST infrastructure. Let's have a quick look at the changes compared to the first beta:

[LIST]
[*] Linux kernel 2.6.22.3
[*] glibc 2.6.1
[*] libzypp 3.18.2
[*] Amarok 1.4.7
[*] Banshee 0.13.1
[*] Compiz 0.5.4
[*] Qt 4.3.1
[*] Thunderbird 2.0.0.5
[*] Wine 0.9.43
[*] more documentation and applications on the one CD installation media
[*]YaST infrastructure was improved to allow writing complete YaST modules
[*] Bootloader-related improvements: openSUSE 10.3 will use "chainloader" if it detects additional installations' bootloader code in other partitions, otherwise "configfile" sections will be used (see Call for Testing below!)
[*] improved package lists of 1-CD GNOME and KDE
[*] countless bug fixes in every component
[/LIST]

As usual, the openSUSE team urges users to test this beta release and report back through the [**openSUSE's bugzilla. **]("http://bugs.opensuse.org/")The areas that require attention are:

[LIST]
[*] HAL
[*] compare lshal output with lshal output from <= Beta1
[*] check if you get an info on the desktop when you insert a USB-disk/stick, DVD/CDs etc. and if the volumes get mounted correctly
[*] test if you are able to umount/eject the media from the desktop
[*] try to mount LUKS (encrypted filesystem) media
[*] check if suspend is working correctly (via KPowersave or g-p-m)
[*] test if you can change the brightness of your laptop panel on <= Beta1, are you able to do the same with the new HAL version?
[*] libzypp / Package Management / Update
[*]before you report a bug, make sure to check for duplicates
[*] perl-Bootloader/Yast-Bootloader
[*]As we switched to using chainloader or configfile sections for other installations, instead of just using the default entry as image section, please check if all other installed operating systems are still bootable.
[/LIST]
**openSUSE 10.3 release schedule:**[LIST]
[*]Thu, Sep 6: openSUSE 10.3 Beta 3
[*]Thu, Sep 20: openSUSE 10.3 Release Candidate 1
[*]Thu, Sep 27: openSUSE 10.3 Goldmaster release (internal)
[*]Thu, Oct 4: openSUSE 10.3 public release
[/LIST]

**Download** : [Mirror 1 DVD i386 ISO]("http://download.opensuse.org/distribution/10.3-Beta2/iso/torrent/openSUSE-10.3-Beta2-DVD-i386.torrent") [Torrents] | [Mirror 1 DVD x64 ISO]("http://download.opensuse.org/distribution/10.3-Beta2/iso/torrent/openSUSE-10.3-Beta2-DVD-x86_64.torrent") [Torrents]

---

### Post by RedDwarf on 2007-08-24
Theres is also a package named opensuse-codecs-installer with description: &#8220;A cross platform component for multimedia frameworks to use to initiate package installation for missing codecs, specific to openSUSE. Supported by GStreamer and Xine.&#8221;

I don't know what Novell is planning...

---

### Post by Erunno on 2007-08-25
I wrote a email to the kernel mailing list and asked if they would make an exception to the beta freeze and merge the CFS patches with the 10.3 kernel but the maintainers told me that CFS is out for 10.3 due to said beta freeze and their distrust in the brand new scheduler. Plus, they assured me that I probably wouldn't notice a difference anyway (they may be even right with this one ;-)).

On other news: Thank god they returned to the blue wallpaper. While SuSE's native color has always been green I find the color too hard on the eyes as a default.

---

### Post by RedDwarf on 2007-08-25
Yes, the timing has been really bad.
- Xorg 7.3 (with HAL support!!!)
- CUPS 1.3 (with Zeroconf support)
- Kernel 2.6.23 (CFS... and some WiFi drivers using the new stack?)

All will be missing.

---

### Post by Erunno on 2007-08-26
It's not that bad if you are willing to use the unsupported Build Service repositories as there's one for each of the applications / frameworks you mentioned, even one for an up-to-date vanilla kernel (although I personally don't replace such a critical components like the kernel). openSUSE makes it relatively easy to stay bleeding edge if you care to.

---

### Post by Dark Star on 2007-08-26
Yep I d/loaded this ver. and its way better than 10.2 :) Am impressed :D

---

