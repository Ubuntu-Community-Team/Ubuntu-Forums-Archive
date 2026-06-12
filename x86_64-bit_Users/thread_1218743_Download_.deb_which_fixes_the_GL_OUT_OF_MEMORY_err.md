---
title: "Download .deb which fixes the GL_OUT_OF_MEMORY error in wine under Ubuntu 64-bit"
date: 2009-07-21
forum: x86 64-bit Users
---

### Post by ACLBandit on 2009-07-21
You can get the "RAM fix" patched Wine 1.0.1 .deb here: [http://aclbandit.ucoz.com/wine_1.0.1-0ubuntu6_amd64RAMPatch.deb]("http://aclbandit.ucoz.com/wine_1.0.1-0ubuntu6_amd64RAMPatch.deb")

I was playing World of Warcraft earlier today, having finally picked up the Wrath of the Lich King expansion. I had finished Borean Tundra and entered Dragonblight, and then the graphics exploded and the program crashed and/or froze. It's apparently a common problem for WoW users running the program under Wine on a 64-bit Linux system, especially in Dragonblight and Dalaran.

I looked up my options. They included the following:
1) Remove some of my RAM. [Unacceptable. I have 8GB that OTHER programs which run while WoW is on that might want some of that.]
2) Reduce available RAM for my system, ignoring that above 3-4GB [Also unacceptable, see above] 
3) Install 32-bit Ubuntu or a Windows OS [No. I don't want to.]

So I went in search of another option, one which would FIX the problem in Wine and let my other programs have all of my RAM.

I ran upon this fine page: [http://www.startux.de/index.php/articles/51-wine-patch-to-use-3gb-userspaceyvComment51](http://www.startux.de/index.php/articles/51-wine-patch-to-use-3gb-userspaceyvComment51)

It's a patch that fixes the problem!

I learned how to apply a patch to source code, downloaded the Wine 1.0.1 source code, applied it, made a .deb file of the patched Wine, and installed it. Voila! I haven't had a WoW crash since. (YMMV, please give me feedback and let me know how it works for you.)

To install this .deb, PLEASE ensure that you've completely removed any other versions of Wine. Don't install Wine updates from the repositories, either, since they won't include this patch at all. 

Also, be aware that I'm NOT completely certain what it is the patch fixed -- something about a 3GB limit to Windows 32-bit apps not enforced by Wine conflicting with video memory. Or something. It's more complex than I grasped, but whatever -- the patch fixed it.

Enjoy Northrend, without crashes. Or other things that have this issue -- the patch was originally made by a guy with Everquest 2 problems. (Thanks again, Stefan Reimer!)

You can get the "RAM fix" patched Wine 1.0.1 .deb here: [http://aclbandit.ucoz.com/wine_1.0.1-0ubuntu6_amd64RAMPatch.deb]("http://aclbandit.ucoz.com/wine_1.0.1-0ubuntu6_amd64RAMPatch.deb")

EDIT: It's also supposedly fixed in the latest build (or, more accurately, since 1.1.25), according to [http://bugs.winehq.org/show_bug.cgi?id=13335](http://bugs.winehq.org/show_bug.cgi?id=13335); however, if you prefer the stable build, or don't know how to compile the (I think still-in-testing) 1.1.25 version, this .deb is your best bet until the fix gets into the stable version.

---

