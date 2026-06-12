---
title: "CPU hotplug problem"
date: 2009-03-23
forum: x86 64-bit Users
---

### Post by nk711 on 2009-03-23
Hi, I am trying to save power during low-load times on a dual quad-core (Intel E5450) 64-bit workstation by using CPU hotplugging. I recently switched to 64-bit Kubuntu, and this is one of the last things I had working on 64-bit Mandriva that I can't get to work in Intrepid (2.6.27-11-generic).

All CPUs (except cpu0) do have an "online" entry under /sys/devices/system/cpu/cpu*/, but powerdevil shows no "CPU can be turned off" capability. Also, the behavior on the command line is confusing me...

I tried, for example,
```
$ sudo echo 0 > /sys/devices/system/cpu/cpu7/online
bash: /sys/devices/system/cpu/cpu7/online: Permission denied

```

which is weird because permissions seem ok:
```
$ ls -l /sys/devices/system/cpu/cpu7/online
-rw-r--r-- 1 root root 4096 2009-03-22 21:26 /sys/devices/system/cpu/cpu7/online

```

OTOH, I can successfully do this: 
```
$ sudo -i
root@mycomputer:~# echo 0 > /sys/devices/system/cpu/cpu7/online

```

Same for CPUs 1-6. I admit I'm still a little vague on the whole sudo thing. I really don't understand why this works for 'sudo -i' but not 'sudo'. I am hoping that once I fix the command line behavior, then powerdevil will start seeing the capability and I can create a 2-cpu profile to use when I don't need all 8.

Thanks much for any help.

---

### Post by kevmitch on 2009-03-23
The reason you're having problems with sudo is that the redirection operator ">" is taking effect after root privileges have been dropped, so that your executing ```
echo 0
``` as root, but then trying to pipe the standard output from that to /sys/devices/system/cpu/cpu7/online
as a regular user. When you use "-i" you become root so that the ">" redirection is done as root.

---

### Post by nk711 on 2009-03-23
Thanks, that makes sense.
Sure enough, 
```
$ sudo sh -c "echo 0 > /sys/devices/system/cpu/cpu7/online"
```

works fine.

So my problem is only that KDE Power management is not recognizing the hotplug capability. I've searched but can't find any leads on this. Any ideas?

---

### Post by kevmitch on 2009-03-23
Ok I admit I'm not expert on the topic as I've never tried this myself. But just to confirm, you are indeed able to bring the individual cpus off-line via the sysfs interface correct? 

In that case, the issue is being able to do the same thing from the GUI. I would recommend starting the GUI from the commandline and looking for any error messages especially relating to permissions. What about running the GUI under sudo (note this is just for testing purposes, you don't want to make a habit of running GUIs as root). If running under sudo works, then that tells you there's a permissions problem somewhere.  

My (very rough) guess about the way it is supposed to work would be 

1) GUI runs as regular user 
2) GUI communicates with dbus or hal or something running with higher privileges
3) dbus or hal or what ever actually manipulates sysfs 

Obviously this can go wrong firstly if dbus or hal are not running. Secondly it can go wrong if they are not permitted to modify the sysfs entries. As to how to fix such a permission problem, maybe someone else can chime in, or offer something better than mere speculation.

---

### Post by nk711 on 2009-03-23
Thanks, those are good suggestions. I am beginning to think, though, that this is simply not implemented yet. From the [KDE 4.2 source code]("http://api.kde.org/4.2-api/kdebase-workspace-apidocs/solid/html/halpower_8cpp-source.html"):

```
00351 bool HalPower::canDisableCpu(int /*cpuNum */) const
00352 {
00353     return false;
00354 }

```

Can *anyone* disable CPUs from the KDE Power Management UI?

I think I'll try a script workaround. Thanks for your help!

---

### Post by kevmitch on 2009-03-24
Yeah, I would have to agree with you on that one. If I correctly understand what you're trying to do, it's probably a job better suited or cron anyway.

---

