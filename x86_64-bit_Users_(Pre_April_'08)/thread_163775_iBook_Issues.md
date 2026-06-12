---
title: "iBook Issues"
date: 2006-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by malachakla on 2006-04-21
Hello,
I have an iBook G3 366 Indigo that I just installed Breezy on, and it's having some issues. I'm totally beginner, so bare with me :)

Issue #1: The battery simply doesn't exist. When I unplug the iBook from the charger while the computer is started up, the computer shuts off. The computer won't turn on when the charger isn't plugged in.

Issue #2: I have no idea how to make Java work to install Limewire and Azureus... it's very frustrating. What is the easiest and most compatible way to run Java on the powerpc version to run those programs?

Issue #3: Is there some sort of specific backports repository for powerpc versions of programs? I try to install some programs and there is no powerpc version. Does the powerpc version need to be compiled from the x86 version or something?
Thanks a lot!

---

### Post by 3rdalbum on 2006-04-21
3. Do you have all the repositories enabled? 99% of programs available from the repositories on x86 are there on PowerPC. To check if you've got all repos enabled, go into the Synaptic menu bar: "Settings > Repositories" and all the items in the list should have a tick beside them.

Some programs, like RealPlayer, aren't on repositories on PowerPC but can be downloaded from the web in precompiled binary form. Other x86 programs that aren't on repositories can be compiled from source to run on PowerPC.

---

### Post by malachakla on 2006-04-26
Hi, does anyone have any further help on the battery issue?
I'd reallly like to actually use this computer as a laptop computer...
Thanks.

---

### Post by aimislame15 on 2006-04-26
If you check Apple support, there was a battery recall a while back, but I think it was only for G4 iBooks, you'd have to check. Also, try buying a new battery from Apple or a third party resale-r or test your computer with a friends battery. If all else fails, give me the laptop because I'm in love with clamshells for some reason.

EDIT: there are programs for bittorrent on ppc linux in the repositories. Easiest way to find those is go to the applications menu (top left default) and click add/remove programs. You can try bittorrent. if you search gnutella in synaptic, it should locate the client that is like limewire. I don't use it, completely legal here. :P I just use bittorrent for ISO's and whatnot.

---

### Post by Rxke on 2006-04-26
Did the battery work before you installed Ubuntu? I mean, a friend of mine has an indigo too, running OS9, which has seen so much use his battery is essentially dead, if he unplugs, the computer switches off after less than a second...

---

### Post by farruinn on 2006-04-26
[quote=malachakla]Issue #2: I have no idea how to make Java work to install Limewire and Azureus... it's very frustrating. What is the easiest and most compatible way to run Java on the powerpc version to run those programs?[/quote] 
Try following [http://wiki.ubuntu.com/JavaPPC]("http://wiki.ubuntu.com/JavaPPC")

I think there are some errors on that page:[LIST]
[*]Download the jre rpm, not the sdk (unless you know you want to develop in java)
[*]Do echo 'PATH=/opt/ibm/java2-ppc-50/bin:"${PATH}"' >> ~/.bashrc - not whatever they have listed there.
[*]The sudo update-alternatives --config java command doesn't work for me at all. I think this is because when we do alien with the rpm it doesn't set "Provides: java" for the resulting package.[/LIST]Other than that I think it's ok... I'm investigating these discrepancies and will update that wiki page soon.

**EDIT:**
That wiki page no longer uses the alien method for converting an rpm to a deb. I upgraded to dapper recently and resinstalled java with the same deb I had created before (using alien). I haven't had any problems yet.

---

### Post by markuspm on 2006-04-28
I have an iBook G3 366, too and Breezy is running fine.
(Dapper LIve CD 6.06 does not work, for now)
Did your battery work before you installed Breezy?
My iBook G3 battery died some month ago and I had to buy a new one.

---

