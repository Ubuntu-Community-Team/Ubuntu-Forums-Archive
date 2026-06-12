---
title: "Legacy Family Tree V9 using Wine"
date: 2023-11-29
forum: Wine
---

### Post by jamesdean69 on 2023-11-29
Hi There

I've browsed & searched through the threads & posts regarding Legacy Family Tree V9 for Windows running on Wine, but no one has seemed to have run it successfully without issues. I've installed this app, with a minor graphical glitch, especially when changing between the tabs. Also, right click doesn't appear to work on certain individuals especially siblings. I'm running it on a wine 64bit prefix. I've installed the MSCore fonts as per the Wine Tricks menu.

My question is, are there any updates to anyone recently running this app with a very good success rate? Also, which DLL's did you install for additional running of the app?

Cheers

---

### Post by DuckHook on 2023-11-29
I realize that there's usually a heavy investment made into genealogy platforms, so it is unlikely that switching is an option for you, but it still remains a fact that running Windows&#8209;based apps in WINE is a crap&#8209;shoot. You should always check WINEHQ AppDB for ratings. I've inquired on your behalf with the following results: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=3207](https://appdb.winehq.org/objectManager.php?sClass=application&iId=3207)

[LIST]
[*]LFT 9.0 Deluxe is rated "Garbage"
[*]LFT V9.0.0.393 is rated "Silver" which, despite its respectable Olympic score, actually translates to "middling". I usually find anything less than "Gold" to be not worth the effort and frustration I will have to put up with.
[/LIST]
If you haven't invested too much time and effort into LFT, you may find it better to switch to a native Linux genealogy platform. There are a number of them, but the one I am familiar with is Gramps:```
duckhook@Zeus:~$  apt show gramps
Package: gramps
Version: 5.1.5-1
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Ross Gammon <rossgammon@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 45.2 MB
Depends: gir1.2-gtk-3.0 (>= 3.12.0), librsvg2-2, python3-gi (>= 3.12.0), python3-gi-cairo, python3-bsddb3, xdg-utils, python3:any
Recommends: graphviz, gir1.2-gexiv2-0.10, gir1.2-osmgpsmap-1.0, python3-icu, gir1.2-geocodeglib-1.0
Suggests: fonts-freefont-ttf, gir1.2-goocanvas-2.0, gir1.2-gtkspell3-3.0, python3-pil, rcs, python3-numpy
Conflicts: python-gramps, python3-gramps
Replaces: python-gramps, python3-gramps
Homepage: https://www.gramps-project.org/
Download-Size: 7,108 kB
APT-Sources: http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
Description: Genealogical research program
 Gramps is an Open Source genealogy program written in Python, using
 the GTK/GNOME interface. It is an extremely flexible program fitting
 the needs for both the amateur genealogist and serious genealogical
 researcher.
 Gramps has the ability to import GEDCOM files exported from many
 proprietary genealogy programs and can produce a large number of
 reports in many popular formats.
```
…I played with it some time ago but never went beyond the dilettante stage.

If you want full functionality of LFT without leaving the Linux ecosystem, then I recommend running it within a Windows VM. They are easy to set up these days and a number of VM solutions exist, of which I recommend KVM for performance reasons and because it is already built in to the kernel. However, others report perfectly decent performance and ease of use with alternatives like VirtualBox or VMWare.

---

