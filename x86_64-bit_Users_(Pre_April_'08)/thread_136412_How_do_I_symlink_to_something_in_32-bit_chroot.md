---
title: "How do I symlink to something in 32-bit chroot?"
date: 2006-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryan76 on 2006-02-25
I'm trying to create a menu item for a training log program called Kipina which I installed in my 32-bit chroot. If I go

**dchroot -d**

then run **kipina** it works fine. But I want to run it from the menu. For my other apps (synaptic, firefox) running in the 32-bit environment I followed these instructions in this thread [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575) but I don't really know what I'm doing, other than looking for a SH file called kipina and linking it to kipina 32.

Can someone please help me create a menu item for this?

---

### Post by John Jason Jordan on 2006-02-25
[QUOTE=ryan76]I'm trying to create a menu item for a training log program called Kipina which I installed in my 32-bit chroot. If I go

**dchroot -d**

then run **kipina** it works fine. But I want to run it from the menu. For my other apps (synaptic, firefox) running in the 32-bit environment I followed these instructions in this thread [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575) but I don't really know what I'm doing, other than looking for a SH file called kipina and linking it to kipina 32.

Can someone please help me create a menu item for this?[/QUOTE]
I did this for Firefox, RealPlayer and Adobe Reader 7.0, all of which I have running in chroot. Here's how I did it:

1) With the mouse hovering over Applications on the Gnome panel, right-click and select Edit Menus.

2) Click on the group where you want it listed, then on New Entry. In the Command box enter "dchroot -d <application name>". Click on OK and close the Edit Menus window. It should now be listed when you click on Applications.

Note: If there is no New Entry button on the bottom of the Edit Menus window, it's because smeg has not been installed. Go to Synaptic64 and install it, then repeat the above instructions.

Now, if you want to link a file in your 64-bit world to the same file in chroot, that is a different matter. I need to do that because I have Firefox in chroot and it can't find the DNS servers when I connect to a new wifi place. I use the following from a command line to link the resolv.conf file in 64-bit to the chroot copy:

sudo -ln -f /etc/resolv.conf /chroot/breezy/32bits/etc/resolv.conf.

What this does is overwrite the existing resolv.conf file in chroot with the version in the 64-bit world. The -f option means "just do it and don't bug me about error messages that I'm overwriting an existing file."

Unfortunately, this link is not permanent. In other words, if the resolv.conf file in 64-bit world is later changed, I have to run the command again to make the version in chroot a copy of it.

---

### Post by ryan76 on 2006-02-25
Thanks heaps, that worked fine. I didn't have to use the resolv.conf solution but I'm sure it will come in handy sometime.

Cheers!

---

