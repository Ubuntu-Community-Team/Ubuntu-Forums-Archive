---
title: "multiple disk install"
date: 2007-12-13
forum: Wine
---

### Post by mr.farenheit on 2007-12-13
i'm trying to install the first call of duty game. it runs that install process through the first disk but when its asks for disk 2 it won't let me eject and run the second disk. are there any settings i have to change or any add ons i might need for a multiple disk installation process?

---

### Post by cogadh on 2007-12-13
You need to open a second terminal session and use the "wine eject D:" command to remove the disk (if your CD drive is not "D:" in Wine, change the command to match your config). However, after the game is done with the second disk, it will ask for the first disk back and that will produce this error:

```
An I/O error occurred while installing a file. This
is normally caused by bad installation media or
a corrupt installation file
```

There is no way to get around the error, but you can cancel the installation and tell it to not roll back any changes, which will leave the game mostly functional.

This is a known bug in Wine:
[http://bugs.winehq.org/show_bug.cgi?id=9002](http://bugs.winehq.org/show_bug.cgi?id=9002)

---

