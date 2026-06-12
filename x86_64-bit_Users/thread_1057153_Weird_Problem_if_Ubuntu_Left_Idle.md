---
title: "Weird Problem if Ubuntu Left Idle"
date: 2009-02-01
forum: x86 64-bit Users
---

### Post by Kow on 2009-02-01
If I let Ubuntu Intrepid x86-64 idle for more than an hour and try using it again everything seems fine until you need to do something that involves hard disk access. Obviously, I can't get far at all and the syslog starts spewing filesystem read/write errors to the journal and also when trying to read sectors. If I reboot the computer everything works fine again. I checked all the system logs and there is absolutely nothing. I see the ---MARK--- until about 40min-1hr after I last used the computer. The Power Management options have absolutely nothing for me to change with regard to powering down the hard drive. I can only change the time to put the display to sleep and also put the computer to sleep. Display is set to 20 min and computer is set to never.

I guess it only makes sense that there is nothing in the system logs if the hard disk cannot be read or written to.... so how the hell do I debug this problem? I'm not a fan of shutting down the computer every time I'm done using it.

Oh and finally: Why does Ubuntu absolutely refuse to fix this problem? I am not the only one and this has been around since at least hardy (and is probably still there... a LTS "stable" release).
[http://ubuntuforums.org/showthread.php?t=295544](http://ubuntuforums.org/showthread.php?t=295544)
[http://ubuntuforums.org/showthread.php?t=296169](http://ubuntuforums.org/showthread.php?t=296169)
Launchpad bug, marked INVALID because lack of info [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284057](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284057)
I would post my syslog but the log looks identical to the one posted in the bug report around the time of the crash.

Just because the required info cannot be retrieved for a bug doesn't mean ubuntu devs should completely forget about the issue and let it go... If you read my first paragraph I explain why there is no info to be retrieved and yet it is more info to add. However, I can't because the bug was already marked INVALID.

---

### Post by cariboo on 2009-02-01
I would check the BIOS for powersaving settings. As far as the bug is concerned, it looks like driver problems, which is up to the manufcturer to fix, not Ubuntu.

Jim

---

### Post by Yellow Pasque on 2009-02-01
There's probably a clever way to trick your system into thinking it's not idle by running some commands in a cron job every half hour.

---

### Post by Kow on 2009-02-04
Problem is still occuring. After the computer is labeled as idle It seems as if the hard drive just shuts down and will not awaken... This time I actually left a terminal open so I could run dmesg after the problem starts and basically it is endless I/O errors to the hard disk. If I revert back to my hardy install everything works fine. If I reboot everything works fine (until it is marked as idle again.) This does not occur every time the computer is idle, only randomly. Turning off the screensaver, leaving the display on (setting set display to sleep to never), and other settings in Power Management & Screensaver have no effect.

---

