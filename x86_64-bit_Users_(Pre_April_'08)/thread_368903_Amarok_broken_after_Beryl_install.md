---
title: "Amarok broken after Beryl install?"
date: 2007-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by modestmelody on 2007-02-23
Is there any reason why amaroK is suddenly broken now that I've installed Beryl?

---

### Post by dfreer on 2007-02-23
How is it "Broken"? Try opening a terminal and run:
```
/usr/bin/amarok
```
And post any information it gives you.

A common error I used to get after reinstalling Amarok was that the DCOP server is not running. If that's the message you get, try [_*this solution*_]("http://www.ubuntuforums.org/showthread.php?t=107269&highlight=dcopserver")

---

### Post by modestmelody on 2007-02-23
/usr/bin/amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
/usr/lib/amarok/amarokapp: symbol lookup error: /usr/lib/libkhtml.so.4: undefined symbol: _ZThn40_N18QXmlDefaultHandler13attributeDeclERK7QStringS2_S2_S2_S2_

---

### Post by dfreer on 2007-02-23
Hmmm try this and post output:
```
ls -l /usr/lib/libkhtml*
```

---

### Post by modestmelody on 2007-02-23
jason@jasonamd64:~$ ls -l /usr/lib/libkhtml*
lrwxrwxrwx 1 root root      17 2007-02-08 18:18 /usr/lib/libkhtml.so.4 -> libkhtml.so.4.2.0
-rw-r--r-- 1 root root 4527384 2007-02-06 00:00 /usr/lib/libkhtml.so.4.2.0

---

### Post by dfreer on 2007-02-23
That file is part of the kdelibs4c2a package. I would try reinstalling kdelibs4c2a with this command:

```
sudo apt-get clean
sudo apt-get install --reinstall kdelibs4c2a
```

Hope this helps!

---

### Post by modestmelody on 2007-02-24
> **dfreer said:**
> That file is part of the kdelibs4c2a package. I would try reinstalling kdelibs4c2a with this command:

```
sudo apt-get clean
sudo apt-get install --reinstall kdelibs4c2a
```

Hope this helps!

Unfortunately, still the same problem.

---

### Post by dfreer on 2007-02-24
Hmmm. I'm running beryl and amarok and I've never seen this error. I think we can safely rule out libkhtml.so.4 being the problem here, that reinstall should've fixed it if it were (and I think a lot more KDE programs like konqueror would be complaining if it were broken). From here on out I'm just guessing, but I would try:

(1) Reinstalling Amarok
(2) Purging the Beryl Packages (beryl beryl-manager beryl-core beryl-plugins libberyldecoration0 beryl-settings emerald-themes beryl-settings-bindings beryl-manager libberylsettings0 emerald libemeraldengine0 beryl beryl-plugins-data). If you spent any time configuring beryl, you probably would want to back up your config files so that you won't lose your changes.
(2.a) After purging beryl, see if amarok will work. Like I said, beryl shouldn't be the culprit here but ya never know :P
(3) Praying? I guess an extreme action would be to reinstall your OS, this problem *shouldn't* replicate.

Sorry I couldn't help you further, Good luck!

---

### Post by ronmarley1 on 2007-02-24
> **modestmelody said:**
> Is there any reason why amaroK is suddenly broken now that I've installed Beryl?
For what it's worth, Amarok runs fine for me along with Beryl.  Sorry for not giving help.

---

