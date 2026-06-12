---
title: "ibook g4 ubuntu 2.6.12-9 battery/hd issues"
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by nelsonmarcelino on 2006-05-29
Just installed ubuntu having switched from osx. My battery life now is less than under osx. I think this is because I hear my hard disk spinning and stopping every second. Is there a way to disable ubuntu writing/reading from disk every second to extend battery life?

---

### Post by slux on 2006-05-30
Logs are one thing that causes constant writes to the hd, some other daemons might also be to blame. You can stop syslog and klog and see if that's enough and continue to shut down other daemon processes if it isn't. /etc/init.d houses start and stop scripts for different daemons. Stopping syslog happens with a "/etc/init.d/syslog stop" from a root terminal and others can be stopped by replacing the script name and running the same command.

When you're happy with it, you either dedicate a new runlevel for mobile operation and remove the daemons you have determined to be the cause from that or remove them altogether (but removing system logging completely probably is not a good idea). Check "update-rc.d" for manipulating what gets started at which runlevel.

You could also adjust some parameters that affect how fast the HD spins down etc and create a more conservative policy for CPU speedstepping.

In the end you're probably not going to have a battery life that's as good as in OS X though. OS X has the advantage of solely existing for the macs so Apple has certainly spent it's time making sure that the power management performs as well as it can. OTOH, you could do some extreme tricks like working off a ramdisk to keep your HD completely shut off all the time and you can perfectly control everything that's going on so you could also for example pin your CPU to the lowest operating frequency it's capable off and I'm pretty sure that would result in a better battery life than what OS X offers (by default anyway). :P

---

### Post by ssam on 2006-05-30
if you have enough ram then try turning swap (virtual memory) off
```
sudo swapoff -a
```
that will probably reduce hard drive usage.

also mounting partitons with the noatime option, prevents the access time being written to disk everytime you read a file. (this can stop some programs from working, though i have never had any problems with a fairly standard system, plus lots of apps, and a web server).
you will need to edit your /etc/fstab file, and put noatime in the options column.
eg
```
/dev/hda12      /               ext3    errors=remount-ro 0       1
```
to
```
/dev/hda12      /               ext3    noatime,errors=remount-ro 0       1
```

also try installing laptop-mode-tools in synaptic package manager.

---

