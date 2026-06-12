---
title: "DDO LOTROLINUX &quot;Error reading launcher configuration file.&quot;"
date: 2008-03-14
forum: Wine
---

### Post by bdoobie on 2008-03-14
I am getting the following error and don't know how to change where it looks for the configuration file as it has moved. I have tried uninstalling from source and reinstalling as a debian package to no avail

Error reading launcher configuration file.


How do I fix this??

---

### Post by Matt Fitzpatrick on 2008-06-04
> **bdoobie said:**
> Error reading launcher configuration file.

How do I fix this??
Sorry for responding to an old post, but I found a solution for this issue.

1) Look in your game directory (the directory containing dndclient.exe, dndlauncher.exe, dndlauncher.exe.config, etc.).  Confirm the name of your launcher config file -- it was "dndlauncher.exe.config" for me.  Case matters.

2) Return to your LotROLauncher directory.  Open DetermineGame.cs in the editor of your choice.

3) Around line 36, find the line```
private const string ddoConfig = "/TurbineLauncher.exe.config";
```  Change that filename to match the name of your config file.  Remember, case matters.  For me, I changed the line to:```
private const string ddoConfig = "/dndlauncher.exe.config";
```


4) Recompile using 'make'.

---

### Post by ajackson on 2008-06-04
DDO switched over to using TurbineLauncher.exe.config a little while ago (I used the US version about a month ago for a test and noticed that change), I should have left a check in to fallback to dndlauncher.exe.config if the first one wasn't found.

An easy way (if you use the precompiled version) is just to copy dndlauncher.exe.config and rename it TurbineLauncher.exe.config.

---

