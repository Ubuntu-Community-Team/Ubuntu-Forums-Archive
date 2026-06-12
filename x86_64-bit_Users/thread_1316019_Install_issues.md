---
title: "Install issues"
date: 2009-11-05
forum: x86 64-bit Users
---

### Post by dsmithnc on 2009-11-05
Started 9.10 64-bit from live cd. Live CD came up ok and I checked a couple of things to make sure it was working. Then ran the installer to an esata drive attached to the laptop.  Thought this would give me the opportunity to run Linux when I wanted it and Windows when I wanted.  I think that may have been a mistake. :o

Things seemed to go well, until rebooting.  Grub loads ok shows all possible boot disks.  When I try to boot into ubuntu, the screen flashes and I get a flickering (what looks to be) a shell login. Character entry is spotty and results in errors.

If I reboot and go to recovery from Grub I can get to the recovery operations area and then I drop to a text log-in again.  Ran aptitude from the shell and it shows a bunch of missing files, but can't update, probably due to no internet connection.

Does this sound like a botched installation?  Should I try again?

BTW, if I unplug the esata drive, the laptop won't start at all.  That's a real pain but something for another post, I think.

Dick


Problem solved.  Evidently a bad install.  Re installed and things are working, still having an issue with the Grub loader but all else seems to be well.

Thanks for looking.

---

