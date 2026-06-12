---
title: "Changing CPUFREQ kernel governor"
date: 2006-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by arnaudsj on 2006-02-11
Hi,

I got breezy running smoothly on my powerbook 17" (5,7) but I have a few things I did not manage to get working and I could not find any post/web page that explained clearly how to fix it, so I hope somebody will have some good pointers :)

The default governor seems to "on demand" which makes the CPUfreq change only to the max speed when the cpu is under demand, whereas it works great on battery (just got 4+ hour last night on a new battery!), I don't like it when I am plugged in. Is there a way to change/recompile the governor kernel module to be "performance" when on the A/C?

I am running pbbuttons and the settings in the conf file don't seem to affect the behavior.

Also, is it possible to disable the "tap" on the trackpad?? It is set to notap in pbbuttons.conf but again to no effect. The rest of pbbuttons seems to be working ok though.

Thank you in advance for your help! 

FYI I am a Gentoo junky, but on the powerbook I can't stand the time it takes to compile packages :rolleyes:  so Ubuntu just replaced my Gentoo install a few weeks ago, and I have been able to actually a little bit more work on it this way.The only thing I have been frustrated so far is the fact that I am now quite as fluent with the Debian/Ubuntu way of things :-k  Like recompiling the kernel, I have no idea what's the proper way to do it in Ubuntu! :mrgreen: 

Cheers!

Sébastien

---

### Post by ssam on 2006-02-11
hi

if you have a look in /sys/devices/system/cpu/cpu0/cpufreq you find a bunch of files. scaling_available_governors gives a list of available governors, and you can "echo >" one into scaling_governor to change it

eg
```
echo "performance" > scaling_governor
```
(you'll need a root shell "sudo su" to do this, see [RootSudo]("https://wiki.ubuntu.com/RootSudo"))

you can do the same with cpu frequency.

i also noticed a command cpufreq-selector, you can do
```
sudo cpufreq-selector -g performance
```
or
```
sudo cpufreq-selector -f 1000
```

---

### Post by arnaudsj on 2006-02-11
Thanks Sam, it works!

The one thing I still don't get though is why pbbuttons does not take care of changing the governor like it is suppose to... I guess since the notap on the touchpad does not work either, maybe I need a more recent version of pbbuttons?

Anyway, for now I found an easy way at least to force the cpu frequency!

Thanks!

---

### Post by ssam on 2006-02-12
you could file a bug against pbbuttons in [malone]("https://launchpad.net/malone").

make sure you mention that you can change the settings with low level tools.

---

### Post by arnaudsj on 2006-02-13
Thanks !

I think I am going to file a few - because somehow I think a few things are not working right for me with PBbuttons on my Powerbook 5,7

- Governor not changed when AC plugged inserted as specified in the config
  ( but lowlevel command does work in changing the userspace governor)
- notap as no effect
  ( but here "trackpad notap" low level tool does NOT work, I get an error when it tries to write to /dev/adb... I installed lsadb, and it does not seem to detect anything in /dev/adb properly... I guess that explains why it does not work at least ;)
 
I don't know if it means anything but when I restart pbbuttons by hand (/etc/init.d/pbbuttons restart) it does display a line on the console that mentions only iBook/Pismo/PB Titanium, not PB Aluminium...

---

### Post by gmc on 2006-02-26
Hi Folks,

I've been playing with the cpu govenor settings. I'm not sure, but does anyone know if it's at all possible to set the govener's for a dual cpu (Centrino T2300) independantly. I seem to be able to lock up the kernel (2.6.15-16-686 #1 SMP) by setting each govener to different values.
For example, set cpu0 to ondemand and cpu1 to powersave.

Can anyone confirm this behaviour before I file a bug report?

G.

---

