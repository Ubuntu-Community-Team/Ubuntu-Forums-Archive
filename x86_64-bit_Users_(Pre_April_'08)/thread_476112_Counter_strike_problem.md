---
title: "Counter strike problem"
date: 2007-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaGGer on 2007-06-16
Ok well I've had CS on the computer for a while and then all of a sudden i restart the computer and now its giving me at first an error of vgui2, says that it can't start because of that. I searched and it said if I delete the Clientregistry.blob file it will work.  did that and then it says that it can't start because there is more than one steam working.

---

### Post by Ken_Lewis81 on 2007-06-25
There will be a file in Steam -- I don't know it that well -- which lets Steam claim it's running.  Unix usually calls this file 'lock'.  Maybe you need to look for something similar.

take care.
Ken.

---

### Post by fabertawe on 2007-06-25
> **DaGGer said:**
> I searched and it said if I delete the Clientregistry.blob file it will work.  did that and then it says that it can't start because there is more than one steam working.

You can't start Steam even after logging out or rebooting? Or are you getting the "registry is in use by another process" error when trying to launch a game?

Paul

---

### Post by DaGGer on 2007-06-26
Yea some times even when I reboot it will say that its already started or something like that.  I've figured how to get it working but it still isn't working like it should.  All I have to do is delete the clintregistry.blob and then wait like 30 seconds and click steam.exe and it works but having t odo that every time I restart is a pain.

---

### Post by fabertawe on 2007-06-26
If you start Steam with a script then you could always delete that file everytime you exit. Like you say it's a pain but if it's the only thing that works for you then at least it's then automated. If you're interested this is what I use...
```
#!/bin/sh

cd /home/paul/c/Program\ Files/Steam/
touch shortcuts.dat

WINEDEBUG="fixme-all" wine steam.exe

mv *mdmp /home/paul/.Trash
```

Obviously you'd have to alter the 'cd' path to point to your Steam folder.  The 'touch' command recreates 'shortcuts.dat' to prevent the "registry in use" error when launching games. The last line moves the crash dump files to the bin as they tend to mount up rather quickly! You could 'rm' them if you prefer. Change the user name obviously.. unless your name is Paul ;)

You could add
```
rm ClientRegistry.blob
```
to the end.

---

### Post by DaGGer on 2007-06-27
I'll have to give that a try. Thanks for you help.

---

