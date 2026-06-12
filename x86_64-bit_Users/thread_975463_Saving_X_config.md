---
title: "Saving X config"
date: 2008-11-08
forum: x86 64-bit Users
---

### Post by NeilBlanchard on 2008-11-08
Hello,

I had to reinstall the nVidia driver (what a pain in the tuckus!) and I am (finally) able to run the nVidia X Server Settings -- but when I try to Save to X Configuration File, I get:

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.

I've tried deleting this file manually -- but I cannot do this because the option is not available.

Also, all programs open on the lefthand monitor, instead of where the were last run/maximized.  Is this just a matter of changing the primary display, or how can I get programs to open on the monitor where they were last run?

Lastly, this problem of the nVidia driver needing to get reinstalled is quite annoying -- how can I get the system to keep using it after system updates?

---

### Post by cariboo on 2008-11-08
What version are you using? How did you install the video drivers?

to do any files operations on files not in your home directory you need to use sudo. To run nautilus as root, press Alt-F2 then type:

```
gksu nautilus
```

Jim

---

### Post by NeilBlanchard on 2008-11-08
Hello Jim,

Sorry, I should have said: v8.04 x64, and I installed the NVIDIA-Linux-x86_64-177.80 via the root console in the Recovery start up mode.

I have Twin X running, with 1280x1024 on the left monitor, and 1600x1200 on the right.

I tried deleting the current xorg.conf.backup using:

sudo del xorg.conf.backup

in the console while I was in the appropriate folder -- or do I need to use the path?

What is nautilus?

---

### Post by gummygod on 2008-11-08
ive had that problem too. i just got by it from running 'sudo nvidia-settings' from the terminal, then it will have write privileges. im not sure if thats the way this should be handled but it works

---

### Post by Artemis3 on 2008-11-08
A little late but, FYI if you use 8.04.1 with backports, there is a package called **nvidia-glx-new-envy** which comes with version 173, so no need to go the manual method.

Just FYI you could revert the changes you painfully made, by runnning the nvidia binary with option --uninstall, and delisting the modules you probably blacklisted.

The changes made to xorg.conf are fine tho.

If you ever want to upgrade to 8.10, its a good idea to do this first to ease pain.

If you keep using the binary from nvidia's page, everytime there is an update to a package beginning with the name "linux", you must reboot, reinstall this driver (in console), and reboot again.

btw: In a terminal type: **sudo rm /etc/X11/xorg.conf.backup** (the command del is not unix style, msdos commands are not recognized without aliases defined, so just **del**ete (**r**e**m**ove) it from your mind and use rm instead).

Nautilus is the name of the file browser, don't run it as root, its dangerous!

---

### Post by NeilBlanchard on 2008-11-08
Hiya,

> **gummygod said:**
> ive had that problem too. i just got by it from running 'sudo nvidia-settings' from the terminal, then it will have write privileges. im not sure if thats the way this should be handled but it works

Thank you -- this worked perfectly.  The link they provide for convenience is not all that convenient, I guess -- they should use a sudo command and make you type in the password, I guess.

> A little late but, FYI if you use 8.04.1 with backports, there is a package called nvidia-glx-new-envy which comes with version 173, so no need to go the manual method.

Just FYI you could revert the changes you painfully made, by runnning the nvidia binary with option --uninstall, and delisting the modules you probably blacklisted.

The changes made to xorg.conf are fine tho.

If you ever want to upgrade to 8.10, its a good idea to do this first to ease pain.

If you keep using the binary from nvidia's page, everytime there is an update to a package beginning with the name "linux", you must reboot, reinstall this driver (in console), and reboot again.

btw: In a terminal type: sudo rm /etc/X11/xorg.conf.backup (the command del is not unix style, msdos commands are not recognized without aliases defined, so just delete (remove) it from your mind and use rm instead).

Okay, what is it that I should do before upgrading to 8.10?

Is there an nVidia driver that is "integrated with" Ubuntu?  And if so, how do I use it?

Thanks to you all for your help.

---

