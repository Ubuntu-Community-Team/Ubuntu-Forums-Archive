---
title: "opencryptoki won't uninstall"
date: 2008-12-12
forum: x86 64-bit Users
---

### Post by pocketchange on 2008-12-12
I'm having troubles with a package that refuses to uninstall because of an error.

```
username(16522)% sudo dpkg -r opencryptoki                                                                                                             
(Reading database ... 279514 files and directories currently installed.)
Removing opencryptoki ...
Stopping PKCS#11 slot daemon: invoke-rc.d: initscript opencryptoki, action "stop" failed.
dpkg: error processing opencryptoki (--remove):
 subprocess pre-removal script returned error exit status 1
Starting PKCS#11 slot daemon: pkcsslotd.
Errors were encountered while processing:
 opencryptoki
zsh: exit 1     sudo dpkg -r opencryptoki
```


I've tried manually invoking the invoke-rc.d script and it does indeed fail.  I've tried stopping it manually and running ```
/etc/init.d/opencryptoki stop
``` will run, however, it exits with a status of 1 instead of 0 (not quite sure why).  I've tried killing the running process and still no luck.

I'm running opencryptoki-2.2.6+dfsg-1:

```
username(16530)% dpkg-query -l opencryptoki
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                               Version                            Description
+++-==================================-==================================-====================================================================================
ri  opencryptoki                       2.2.6+dfsg-1                       PKCS#11 implementation for Linux (daemon)
```

Any suggestions?

//Shane

---

### Post by pocketchange on 2009-01-05
Per recommendation from this forum entry:

[http://ubuntuforums.org/showthread.php?t=1002856](http://ubuntuforums.org/showthread.php?t=1002856)

I was able to add "exit 0" beneath the "#!/bin/sh" in /etc/init.d/opencryptoki and then do "sudo dpkg -r opencryptoki", which worked.

---

