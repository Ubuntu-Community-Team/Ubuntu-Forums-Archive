---
title: "X Server failed to start."
date: 2006-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by bttfpromo on 2006-05-28
[http://bttfpromo.net/ubuntu/](http://bttfpromo.net/ubuntu/)


Can someone tell me what's wrong?

[http://bttfpromo.net/computer.html](http://bttfpromo.net/computer.html)
That's my computer.

EDIT: Sorry, I meant to add that this is a LiveCD (on a DVD).

---

### Post by jon_z on 2006-05-28
paste us what the error in: /var/log/Xorg.0.log is  make sure to use the code tags so no smilies pop up inside the log.     and try to remove redundant information cuz it may take up a few posts.

---

### Post by bttfpromo on 2006-05-28
Sorry, I meant to add that this is a LiveCD (on a DVD).

---

### Post by jon_z on 2006-05-28
okay after the errors close it kicks you back to console type in: 
```
 sudo dpkg-reconfigure xserver-xorg
```
change the driver from ATI to VESA  save and try that.

---

### Post by bttfpromo on 2006-05-28
But...I don't go back to the console.

It is about to load the OS, and then that pops up.

---

### Post by jon_z on 2006-05-28
sorry forgot: press Control + Alt + F1  then do that

---

### Post by jon_z on 2006-05-28
if that doesnt get you into a terminal, when grub loads or is about to load, hit escape and select recovery, this will put you in a root terminal.

---

### Post by bttfpromo on 2006-05-28
Cool, that sudo command worked, but I also had to do this:

```
sudo dpkg-reconfigure gdm
```

---

### Post by jon_z on 2006-05-28
glad to help

---

