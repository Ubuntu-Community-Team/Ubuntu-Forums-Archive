---
title: "LIferea lockup after update to Firefox 1.5.0.7"
date: 2006-09-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by a-musing amazon on 2006-09-23
I'm using the most current version (1.0.12) of Liferea available on the 64-bit version of Ubuntu Dapper 6.06.

I use Epiphany as my browser with Firefox as my backend. I'm running 32-bit plugins such as Flash through nspluginwrapper. I keep the installation up to date. Since I got this working I've had no noticeable difficulties with using Liferea.

Yesterday (22-09-06) I installed the latest automatic update from Ubuntu of Firefox 1.5.0.7 and associated packages, 1.5.0.7 is a security release.

Since then Liferea has started to lock up the computer. In some case this is partial and I can continue working by killing Liferea and perhaps associated processes (Epiphany, npviewer.bin), but sometimes I get a complete lockup, am unable to switch to another application and have to reboot.

Just reading headlines does work, but any attempt to view the asociated stories (i.e. invoking Epiphany) can lead to this behaviour.

I either get a lockup or at the very least a continued  switch of the cursor to spinner (loading) mode. There are large increase in cpu utilisation of Epiphany and npviewer.bin.

I've looked at using gtk2html as an alernative viewer but (for me) it lacks functionality. I am now trying Blam but it does seem rather simpistic after Liferea.

I have investigated installing a newer version of Liferea than the ones in the Dapper repositories, both as packages and by compilation but there seem to be major incompatibilities in asssociated libraries (I think associated with the use of newer version of GTk+-2.0) that discourage me from proceeding, so I can't see if the errors have already been addressed in later Liferea releases. Newer version of Liferea seems to be being compiled against Etch/Edgy, now with Gnome 2.16 with the consequence that Dapper (supposedly with LTS) seems to have been orphaned, at least with this application.

Any one else having this problem, or can suggest a solution? I have reported this as a bug.

---

### Post by a-musing amazon on 2006-09-23
I now suspect that this is related to the no-flash problem when using nspluginwrapper and Firefox 1.5.0.7 reported elsewhere.

Anyway I've also now reported this on the nspluginwrapper site on freshmeat.

---

