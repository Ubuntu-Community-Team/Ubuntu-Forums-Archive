---
title: "powerbook G4 freezes when Xorg starts with UseFBDev false"
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by yarikoptic on 2006-01-25
I've got in hands PowerBook5,8 MacRISC3 Power Macintosh running Dapper (since Breezy could not boot from the CD) which had to be configured to have dual display.

simple setups didn't engage second screen at all - although I could move mouse over to the screen of DVI (VGA monitor via adapter), nothing was really plot on it.
I decided to try mergedfb, but now I had to disable UseFBDev since 
"MergedFB does not work with Option UseFBDev, MergedFB mode is disabled"

whenever I set "UseFBDev" to False, Xorg stalls the whole box even before anything is written to /var/log/Xorg.0.log (so it has previous version in there)

So I get something like that on the screen in the terminal (over SSH)
> 
root@max:/etc/X11# Xorg -v -v -v -v -v -v -keeptty -logverbose 5 -config xorg.conf.new 

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 ppc
Current Operating System: Linux max 2.6.15-13-powerpc #1 Thu Jan 19 16:22:31 UTC 2006 ppc
Build Date: 21 December 2005
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 24 15:34:10 2006
(++) Using config file: "xorg.conf.new"
(WW) ****INVALID IO ALLOCATION**** b: 0xf0000400 e: 0xf00004ff correcting
(EE) end of block range 0xefffffff < begin 0xf0000000


and then the box is coocked...

Any hints on how to resolve the situation are more than welcome

---

