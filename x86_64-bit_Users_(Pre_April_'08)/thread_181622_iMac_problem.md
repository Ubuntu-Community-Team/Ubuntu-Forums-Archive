---
title: "iMac problem"
date: 2006-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by JaredW on 2006-05-24
I installed Ubuntu on my iMac last night.  I went to sleep when it was installing the last of the packages.  I woke up to a log in screen, I tried to log in with "root" (without the quotes) and it says incorrect password.  So I log in with the non-administrative account that I created during installation.  It logs in, but I only see my mouse cursor and a brown background.  I bring up the terminal and type in "display=:0 gnome-panel" an error come up.  It says (gnome-panel : 3872) : Gtk-WARNING **: cannot open display:

What is going on with the errors and is there a default password for root siice it didn't let me make one?

---

### Post by meng on 2006-05-24
Ubuntu does not install with a root password. If you really want to create one you can, but otherwise you're encouraged to use "sudo". I'm not sure what's going on with your GUI though.

---

### Post by JaredW on 2006-05-24
I set the date with sudo date -s "Wed May 24 15:00:00 GMT 2006"
But when I try to restart by typing in sudo /ect/init.d/gdm restart it says command not found.......

---

### Post by meng on 2006-05-24
/etc? or /ect?

---

### Post by JaredW on 2006-05-24
Oh, oops.  I accidently put ect, not etc!

---

