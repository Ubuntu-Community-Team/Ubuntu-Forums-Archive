---
title: "Wine 1.7 won't install from repository - Lubuntu 14.04 AMD64"
date: 2014-06-11
forum: Wine
---

### Post by leopheard on 2014-06-11
Hi all,

I'm having trouble getting Wine 1.7 to install on Lubuntu 14.04 64 bit.

I've done:
[B][I]sudo add-apt-repository ppa:ubuntu-wine/ppa
[/I][/B][COLOR=#000000][FONT=bitstream vera sans][B]sudo apt-get update
[/B][B]sudo apt-get install wine1.7

[/B]Which provides the following output (after listing many dependencies to install):

[/FONT][/COLOR]
0 upgraded, 77 newly installed, 0 to remove and 21 not upgraded.
Need to get 8,561 kB/169 MB of archives.
After this operation, 550 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
**Media change: please insert the disc labeled**
** 'Lubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)'**
**in the drive '/media/cdrom/' and press enter**

I have put the CD in the drive, so why is it saying the CD is incorrect? (I've checked and the data on there is fine). Also, with the 20140416.2 - does that suggest there's a Lubuntu 14.04 disc 2?

Any help would be appreciated!

Thanks

---

### Post by Toby_Hubbard on 2014-06-15
In the Software Center look for an app called "Synaptic Package Manager" which is a "deb" file icon with a green down arrow and without the swirl, the go to "software & Updates" in the "system settings" and check all of the "Canonical Partners' boxes in all the tabs, Go to "Synaptic" and reload, and search for "Wine", and right click all of the first 6 and mark them for installation, then click install. This should work, you can use it to get other apps aswell. Hope this helps.

---

