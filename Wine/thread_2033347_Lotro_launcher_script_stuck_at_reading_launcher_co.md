---
title: "Lotro launcher script stuck at reading launcher configuration..."
date: 2012-07-26
forum: Wine
---

### Post by aaditmshah on 2012-07-26
I have been playing lotro on ubuntu using wine and it has been working perfectly. I use the [lotro launcher shell script]("http://bmx-chemnitz.de/~mfr/LOTRO/") to patch and launch the game.

Today when I woke up and ran the following command from my home directory to start lotro it didn't get past the reading launcher configuration line:

```
aaditmshah@ubuntu:~$ .wine/drive_c/Program\ Files\ \(x86\)/Turbine/The\ Lord\ of
\ the\ Rings\ Online/lotrolauncher.script

Welcome to the CLI launcher for LOTRO v1.0rc2.
	(C) 2007-2011 by SNy

Reading launcher configuration...
```

I have been waiting for quite some time and I can't understand why it's taking so long. This has never happened before and I am pretty sure that I didn't make any changes in the game directory.

---

### Post by brainwash on 2012-07-26
You can't establish a connection to the login server, so the game servers are most likely offline (scheduled server downtime or whatever).

---

