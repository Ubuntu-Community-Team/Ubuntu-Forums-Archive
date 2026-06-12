---
title: "Installed Server, trying to add Desktop"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by mmmFiesty on 2007-04-20
I downloaded the 64 bit server, tossed it on a cd and installed it on a fresh machine.

I picked the LAMP install and after it finished I was looking at a command prompt.

Being a GUI sort of guy, I tried to install the desktop on my machine
 sudo aptitude update
 sudo aptitude install ubuntu-desktop


It says it needs to download a couple hundred megs worth of stuff, I click Y and its off.  Except as I watch it has a bunch of connections reset, and what looks like a lot of packages fail.

The very last thing I see is 
[http://us.archive.ubuntu.com/ubuntu/Pool/main/d/diveintopython/diveintopython_5_4_ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/Pool/main/d/diveintopython/diveintopython_5_4_ubuntu2_all.deb) failed.

I reboot and sometimes it hangs while loading boot scripts,
other times it hangs with the orange bar on the screen, and on a previous install it actually got to the login screen where it hung after a login with a blank tan screen.  (by hung I mean 10+ minutes with no activity)

I can still use the boot menu to get to a prompt and have tried to re-run the install ubuntu-desktop line a few times, but it always kills off at the same point.  Additionally I pointed a browser at the archive site above and it looked like the files were just sitting there.

Bob

---

### Post by Ken_Lewis81 on 2007-05-11
You now need to go through a few rounds of "aptitude dist-upgrade" to get everything properly working.

Ken.

---

