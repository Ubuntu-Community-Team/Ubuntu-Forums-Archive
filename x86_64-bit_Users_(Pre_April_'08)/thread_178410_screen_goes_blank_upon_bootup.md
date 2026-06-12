---
title: "screen goes blank upon bootup"
date: 2006-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by noglider on 2006-05-17
I have a Mac Bondi Blue G3. Not sure what I want to do with it yet, as it's so slow. I think it has 256 MB of RAM, and there's little chance I can go beyond that.

I successfully loaded Mac OS X 10.3 on it. Now I want to try Ubuntu. I have lots of experience with Linux on PC hardware, so I'm not a Linux newbie.

My problem is this: I booted the Mac from the Breezy Badger Live CD. It looks good until the GUI login screen is about to start. The brown Ubuntu logo displays briefly. Then the screen goes blank. The power button goes from green to yellow, indicating the screen has gone to sleep.

Any tips?

Thanks.

---

### Post by noglider on 2006-05-17
Aha. Thanks to the "can't login" question, it reminded me of the ctrl-alt-f1 keys for text login. I see the system is up. I guess it has trouble with X. I can't quite figure out what the trouble is, though.

And by the way, what's the root password of the live CD? I can't guess it.

Here is the bottom of the Xorg.0.log I found in /var/log:

(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

Any hints?

Thanks.

---

### Post by Theo-Ubu on 2006-05-18
This is a common problem off the live-CD.  You'll have to drop to a comand line, edit the X config file, then re-start X.  Then you should get the full GUI.  There are instructions in one or two threads on this site.  Good luck.

---

