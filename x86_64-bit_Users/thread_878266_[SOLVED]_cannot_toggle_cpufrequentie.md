---
title: "[SOLVED] cannot toggle cpufrequentie"
date: 2008-08-02
forum: x86 64-bit Users
---

### Post by Bloemetjesgordijn on 2008-08-02
Hi,

I have just build a new computer with an AMD Phenom 9550. This baby is running to hot and I want to scale down my frequentie.

However I cannot get Powernowd working. If I run powernowd it states:
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus: No such file or directory
powernowd: err=2
powernowd: Found 4 scalable units:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later 
# checked and ok
 - That you have sysfs mounted /sys 
# guess so dont know how to check
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel 
# dont know how to check
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors.
# typed dmesg no special items noticed, but not sure where to look for


Please help me, my cpu is burning up in here

Kind regards,

Bloemetjesgordijn

---

### Post by Bad_Byte on 2008-08-02
Since dmesg gave no answers, I am thinking you might be missing the software. Try```
sudo apt-get install cpufrequtils
``` that will install 2-3 pieces of software that allows for cpu speed switching.
Just on a side note if you do the frequency change by hand, all cores must be set to the same speed, then the hardware actually changes frequency.

---

### Post by Bloemetjesgordijn on 2008-08-03
Thx.

I just installed cpufregutils via "sudo apt-get install cpufrequtils"


However when I type "cpufreq-info" ([link]("http://www.kernel.org/pub/linux/utils/kernel/cpufreq/cpufrequtils-README"))

I get: 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 2:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 3:
  no or unknown cpufreq driver is active on this CPU


It seems no cpufreq driver is installed!!!

Got any idea how I can install them?? I dont :-(

Cheerz

Bloemetjesgordijn

---

### Post by soxs on 2008-08-03
Do it like that, worked for me (Phenom 9500) 
```
sudo apt-get install powernowd 
sudo dpkg-reconfigure gnome-applets 

```
Answer "ru with root privleges" with "YES"
```

sudo apt-get install sensors-applet 
sudo nano /etc/modules 
```
# add:
```
powernow-k8
```
reboot:
```
sudo init 6
```

Note: If it still doesn't work after rebooting, remove any cpuscale-applet from your panel and run:
```
sudo dpkg-reconfigure gnome-applets
``` (answer yes, when asked to run the applet with root previliges)
again
-> reboot again

---

### Post by soxs on 2008-08-04
> **Bad_Byte said:**
> Since dmesg gave no answers, I am thinking you might be missing the software. Try```
sudo apt-get install cpufrequtils
``` that will install 2-3 pieces of software that allows for cpu speed switching.
Just on a side note if you do the frequency change by hand, all cores must be set to the same speed, then the hardware actually changes frequency.

That'sworng, because K10 arch allows singlecore downvolting

---

### Post by Bad_Byte on 2008-08-04
> **soxs said:**
> That'sworng, because K10 arch allows singlecore downvolting

I stand corrected, I believed this was not out in the wild yet.

---

### Post by Bloemetjesgordijn on 2008-08-04
Thanx you all.

Soxs, I followed your instuctions by the letter and powernowd works like a charm now. If I type cpufreq-info it says 

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1.10 GHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 1.10 GHz
  available cpufreq governors: ondemand, powersave, conservative, userspace, performance
  current policy: frequency should be within 1.10 GHz and 2.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.10 GHz.
analyzing CPU 1:
etc.

One issue down and zillion to go :-)


Thanx again

Kind regards,

Bloemetjesgordijn

---

### Post by soxs on 2008-08-05
> **Bloemetjesgordijn said:**
> 
...

Thanx again

Kind regards,

Bloemetjesgordijn
use the thank you button if you feel like ;-)

---

### Post by Bloemetjesgordijn on 2008-08-05
* searching for thanx button * 

* searching * 

* logging in * 

* found * 

Done :-)

---

