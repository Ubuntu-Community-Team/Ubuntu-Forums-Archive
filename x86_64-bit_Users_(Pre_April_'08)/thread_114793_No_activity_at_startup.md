---
title: "No activity at startup"
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rovenhot on 2006-01-09
Just installed Breezy supposedly succesfully on my old rebuilt iMac DV SE 500MHz.  Ubuntu works perfectly until I log in, at which point I heard the login chime but I saw nothing except a brown background for over 5 minutes.  Mouse responds, but the OS doesn't.  Does the first bootup (after package installation) always take extremely long?  I think there's some other problem, but later, I might try letting it sit for a while after login.

---

### Post by linear on 2006-01-09
Two possibilities:

1. The Ubuntu date bug. See here: [https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

2. Incorrect settings in xorg.conf. For some reason, Breezy has trouble with the G3 iMacs.

Try the following, after booting is complete:
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/gdm restart (return) to restart Gnome

At the very least you'll need to modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

If you restart Gnome and everything is in extreme slo-mo, you'll also need to edit xorg.conf to disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

---

### Post by Rovenhot on 2006-01-09
It was the date bug!  Ubuntu finished starting up after I reset the time, so apparently X11 was configured properly.  Thanks for the help; I can finally call myself an Ubuntu user!

---

### Post by dombleu on 2006-01-09
Just for the archives, I had the same "symptoms" on my mom's comp now running Breezy and the problem was: ( drum roll ) local loop not running. 

```

sudo ifup lo
```

did solve the problem

and I had to add "auto lo" as in:
```

# The loopback network interface
auto lo
iface lo inet loopback
```

in /etc/network/interfaces to make the local loop started at boot.

Don't know much about why the local loop wasn't configured properly during installation, though.

---

