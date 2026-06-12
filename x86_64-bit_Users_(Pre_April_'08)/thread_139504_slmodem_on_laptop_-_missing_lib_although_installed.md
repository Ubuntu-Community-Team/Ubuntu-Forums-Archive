---
title: "slmodem on laptop - missing lib although installed!?"
date: 2006-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by inkaine on 2006-03-04
Hi folks,

first post here. I'm new to ubuntu (Breezy Badger) but not to Linux. I had used Red Hat for quite some time on my old desktop machine. I have actually bigger problems NOT tweaking config files manually but using graphical surfaces. :mrgreen:

Anyways, my big problem is I'm on dialup and desperately trying to get it working with my internal modem (alsa compatible, module working flawlessly). I already saw that there's no install package for the 64bit ARCH, so I got the source and tried to compile. I'm not gonna publish the long error list here. Then I got the most current i386 package and installed with --force-architecture.

Still running slmodemd gives me an error, namely the following:
```
slmodemd: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory
```

The file is installed in /usr/lib though. I even tried softlinking into /usr/share/lib and /lib, both without success.

Any ideas here? Or any other hint on how to get slmodem going for me?

---

### Post by towsonu2003 on 2006-03-06
for slmodems with alsa support, there is a precompiled package that will make it work. the link to the modem (from linmodems.org) should be in the modemdata.txt of your scanModem output (see second link in my signature for scanModem). I make mine work with:
```

#following is the first time ever
sudo cp /path/to/precompiled/slmodemd /usr/bin
#on every boot, or search forums for update-rc.d for on boot
slmodemd -a -c USA modem:1

```
alternatively, instead of modem:1, try hw:0 or hw:1 or modem:0 
then run sudo wvdialconf /etc/wvdial.conf

let me know if you need more details. 

Important Note: I have no idea whether this works with 64???? check modemdata.txt for that as well...

---

