---
title: "Restarting hotplug"
date: 2005-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by les-h on 2005-12-07
I have recently install the latest kubuntu, I have attached via usb a epson R200 printer and an orange spv smartphone. Both of these devices work but are not reconized until I restart hotplug. Any help would be appreciated.

---

### Post by xmastree on 2005-12-07
Can't help you, but how do you restart hotplug?

I have a [problem]("http://www.ubuntuforums.org/showthread.php?t=98427") with my card reader and I think restarting hotplug might help.

---

### Post by les-h on 2005-12-07
If you go to System Settings, then system services, go to admin mode, highlight hotplug and click restart. Hope this helps..

---

### Post by xmastree on 2005-12-07
I can't see System Settings in any of the menus... I'm still running 5.04, is it only available in 5.10?

Ideally I'd prefer a command line solution, then I can make a script and put a launcher on the desktop.

---

### Post by les-h on 2005-12-07
I'm a bit of a newbie, but you could try sudo /etc/init.d/hotplug restart

---

### Post by xmastree on 2005-12-09
Well, that appears to do something relevant (I ran it with the card in and mounted, it disappeared and reappeared again), of course now that I want it to fail so I can test the fix, it doesn't. Which is equally acceptable. :-)

Thanks

---

### Post by les-h on 2005-12-09
Glad to be of help.  Wish someone could help me.  Have to restart hotplug after each reboot!

---

### Post by xmastree on 2005-12-09
Can't you make that command run when you login? 
System > Preferences > Sessions > startup programs
You might need to tweak the permisions, as it needs to be su normally.

---

### Post by les-h on 2005-12-09
I don't have a preference option in the system menu, maybe i'm missing a package.

---

### Post by les-h on 2005-12-10
Sorted it.  Don't know why, but just changed usb ports of one of the devices.  Must be something in the order they load.;)

---

### Post by xmastree on 2005-12-10
That's rather strange. Glad it now works for you, but it sounds like a bug.
IMO it shouldn't matter where USB devices are plugged in. :confused: 
It might be worth making a few tests with things in different ports, noting what's where with lsusb, and whether or not it works. Then file a bug report.

Just a thought.

---

