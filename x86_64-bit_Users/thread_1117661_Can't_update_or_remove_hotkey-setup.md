---
title: "Can't update or remove hotkey-setup"
date: 2009-04-06
forum: x86 64-bit Users
---

### Post by macic7 on 2009-04-06
After doing an apt-get upgrade in Ubuntu 9.04 beta (64-bit), I got the following error message from dpkg:

```
Setting up hotkey-setup (0.1-23ubuntu10) ...
/etc/init.d/hotkey-setup: 47: Syntax error: ";;" unexpected (expecting "fi")
invoke-rc.d: initscript hotkey-setup, action "start" failed.
dpkg: error processing hotkey-setup (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hotkey-setup
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Since I'm using Ubuntu on a desktop computer, I don't need the package, but attempting to remove it results in the following error:

```
mac@mac-desktop:~$ sudo apt-get remove hotkey-setup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopal3.4.2 libpt2.4.2-plugins-alsa libpt2.4.2 libpt2.4.2-plugins-v4l2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  hotkey-setup
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 98.3kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 176124 files and directories currently installed.)
Removing hotkey-setup ...
/etc/init.d/hotkey-setup: 47: Syntax error: ";;" unexpected (expecting "fi")
invoke-rc.d: initscript hotkey-setup, action "stop" failed.
dpkg: error processing hotkey-setup (--remove):
 subprocess pre-removal script returned error exit status 2
 Removing any system startup links for /etc/init.d/hotkey-setup ...
   /etc/rc1.d/K20hotkey-setup
   /etc/rc2.d/S20hotkey-setup
   /etc/rc3.d/S20hotkey-setup
   /etc/rc4.d/S20hotkey-setup
   /etc/rc5.d/S20hotkey-setup
/etc/init.d/hotkey-setup: 47: Syntax error: ";;" unexpected (expecting "fi")
invoke-rc.d: initscript hotkey-setup, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hotkey-setup
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Is there a solution to this problem?

---

### Post by cruzpaulo on 2009-04-06
I've fixed mine with the solution of this thread.

[http://ubuntuforums.org/showthread.php?p=7022642#post7022642]("http://ubuntuforums.org/showthread.php?p=7022642#post7022642")

---

### Post by macic7 on 2009-04-06
Thanks a lot! It worked perfectly.

---

