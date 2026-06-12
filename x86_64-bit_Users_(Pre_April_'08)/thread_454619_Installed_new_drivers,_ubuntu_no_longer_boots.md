---
title: "Installed new drivers, ubuntu no longer boots"
date: 2007-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by divisortheory on 2007-05-25
I recently upgraded my video drivers (I'm using an nVidia GeForce 7900) with drivers from nVidia's website.  After that, I can no longer boot into Linux. I'm definitely a noob with Linux, can anyone offer some advice?  It gets past the first 2 Kubuntu splash screens, then I just get a black screen with a flashing cursor.  I can actually type in this screen, but it's not a terminal window as the commands do nothing.  At this point I'm stuck.  Pressing Ctrl+Alt+Del actually reboots the system and I get some linux messages as well as another splash screen, but the messages are too quick to read.

The driver installation didn't seem to encouter any problems, so idk what to think.  To install them I did Select Session -> Console Session from the login screen, then logged in as root and typed

sh DriverPackage

and everything else went off pretty much automatically.

Any advice?

---

### Post by divisortheory on 2007-05-25
In case it helps, I read some other post that mentioned Alt+F4 during the boot process.  I did that, and I get no error messages at all.  The last thing I see before it stops is:

Starting K Display Manager: KDM
Running local boot scripts (/etc/rc.local) [OK]


Immediately below that is the flashing cursor I can type in.  Pressing Alt+F1 - Alt+F6 takes me to various other console based login screens, I tried logging into those and there was no problem.  There's just no shell.

---

