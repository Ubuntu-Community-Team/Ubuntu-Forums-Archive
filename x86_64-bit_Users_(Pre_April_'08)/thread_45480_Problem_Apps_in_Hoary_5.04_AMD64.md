---
title: "Problem Apps in Hoary 5.04 AMD64"
date: 2005-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by OneSeventeen on 2005-06-30
So far the only apps I've noticed I can't get running (that *should* run):
[list]
[*]Blender 3d
[/list]

Wow... that's actually not so bad... now the ones I can't get running that supposedly shouldn't run anyway:
[list]
[*]Wine
[*]Cedega
[*]Flash plugin for firefox
[*]The Adobe Creative Suite 2
[/list]

Wow, once again, not that long...

And the other items suggested in this list (most of which I don't know what they are):
[list]
[*]dchroot
[*]debootstrap
[/list]

If you intend on suggesting chrooting, please first describe what a chroot is, and what it entails.  (not neccessarily a walkthrough, as there are plenty of those... but what exactly chroot *is*, as I still haven't figured that one out.)

---

### Post by Optimal Aurora on 2005-06-30
you should add dchroot debootstrap to the list...

---

### Post by norman_h on 2005-06-30
[QUOTE=OneSeventeen]So far the only apps I've noticed I can't get running (that *should* run):
[list]
[*]Blender 3d
[/list]

Wow... that's actually not so bad... now the ones I can't get running that supposedly shouldn't run anyway:
[list]
[*]Wine
[*]Cedega
[*]Flash plugin for firefox
[*]The Adobe Creative Suite 2
[/list]

Wow, once again, not that long...

And the other items suggested in this list (most of which I don't know what they are):
[list]
[*]dchroot
[*]debootstrap
[/list]

If you intend on suggesting chrooting, please first describe what a chroot is, and what it entails.  (not neccessarily a walkthrough, as there are plenty of those... but what exactly chroot *is*, as I still haven't figured that one out.)[/QUOTE]
 I have had problems with OpenOffice and its macros when using AMD64...  probably more of an OOo thing than an ubuntu thing.  I haven't tried any of the recent OOo versions, but with OOo2 not far away, we can hope!

---

### Post by FluffyElmo on 2005-06-30
Blender 3D is working for me, I didn't do anything special just installed it any all recommended packages using Synaptic. So I can't help too much there. Nor have I installed Wine, but maybe someone else can help you. If you search this forum there are threads which may point you in the right direction.

For cedaga try the instructions here: [http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64) 

For Adobe Creative Suite, you have to get WINE (or perhaps cedaga?) running. Once WINE is working you should be able to install the Adobe stuff.

For a Flash plugin for firefox, you can try gplflash ([http://gplflash.sourceforge.net/](http://gplflash.sourceforge.net/)) but it's still buggy, for 'real' flash you're going to have to install and run 32bit Firefox in a chroot. Here is my best stab at explaining what a chroot *is*...

*chroot* replaces your root directory with a directory of your choosing. With Ubuntu 64 you chroot to a directory which has a 32bit Ubuntu installation in it. Any applications within the chroot then run as though they were on a seperate 32bit install, using 32bit libraries. 

*debootstrap* is used to create a Debian base system from scratch, without requiring the availability of dpkg or apt. It does this by downloading .deb files from a mirror site, and carefully unpacking them into a directory which can eventually be chrooted into.

So when you install a chroot you basically use debootstrap to download and install 32bit Ubuntu to a directory, then you chroot into it to install and run 32bit applications as though you were running 32bit Ubuntu. chroot instructions are here: [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

### Post by AndreAPL on 2005-07-04
[QUOTE=FluffyElmo]Blender 3D is working for me, I didn't do anything special just installed it any all recommended packages using Synaptic. So I can't help too much there. Nor have I installed Wine, but maybe someone else can help you. If you search this forum there are threads which may point you in the right direction.

For cedaga try the instructions here: [http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64) 

For Adobe Creative Suite, you have to get WINE (or perhaps cedaga?) running. Once WINE is working you should be able to install the Adobe stuff.

For a Flash plugin for firefox, you can try gplflash ([http://gplflash.sourceforge.net/](http://gplflash.sourceforge.net/)) but it's still buggy, for 'real' flash you're going to have to install and run 32bit Firefox in a chroot. Here is my best stab at explaining what a chroot *is*...

*chroot* replaces your root directory with a directory of your choosing. With Ubuntu 64 you chroot to a directory which has a 32bit Ubuntu installation in it. Any applications within the chroot then run as though they were on a seperate 32bit install, using 32bit libraries. 

*debootstrap* is used to create a Debian base system from scratch, without requiring the availability of dpkg or apt. It does this by downloading .deb files from a mirror site, and carefully unpacking them into a directory which can eventually be chrooted into.

So when you install a chroot you basically use debootstrap to download and install 32bit Ubuntu to a directory, then you chroot into it to install and run 32bit applications as though you were running 32bit Ubuntu. chroot instructions are here: [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)[/QUOTE]
 my KDE aplications are almost the time giving Error 11 when exiting.... (kaffeine, konqueror...)
about cedega, i forced i386 version and runing great.

---

