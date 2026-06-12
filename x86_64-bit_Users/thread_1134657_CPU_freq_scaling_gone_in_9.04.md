---
title: "CPU freq scaling gone in 9.04"
date: 2009-04-23
forum: x86 64-bit Users
---

### Post by cyprusxr3 on 2009-04-23
I've just upgraded to Jaunty, and on first boot up receive "CPU Frequency Scaling Unsupported" and a notice that I will be unable to change the frequency of my CPU. It is currently stuck at 2.19ghz.

Doing some searching it seems that jaunty changed the way acpi-freq was implemented (though I could decipher no details). Could this be the issue?

Information:
uname -a: Linux cyprus-laptop 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux
CPU: Intel Core 2 Duo T7500 (2.2ghz)
Laptop: Dell m1330
Power Management in BIOS is ENABLED.

Everything was working fine prior to upgrade. I disabled all third party repositories, and I don't recall keeping any configuration files relating to scaling. I don't believe anything in 8.10 was other than the default.

If anyone has any information that could get scaling back, I'd greatly appreciate it! Laptops are much less useful when they are always plugged in.

EDIT: It appears on further inspection that the cpufreq folder that should be under /sys/devices/system/cpu/cpu0/ does not exist. Could this mean a package that should have been installed was not?

SOLVED: Rather silly, but I'll post here for posterity. I ran "sudo modprobe acpi-cpufreq" and saw my cpu freq changed from 2.19ghz to 2.20ghz. I then rebooted and found that scaling worked once again. I have no idea why this didn't "just work," but perhaps someone else will find this helpful.

---

### Post by spallared on 2009-04-24
Hi and thanks for the hint, that was really useful...

Just a small note, in my case (cpu frequency scaling not supported after upgrade to Ubuntu 9.04) i had to add the module you suggested to /etc/modules, just a modprobe was not enough.

Regards
Luca

---

### Post by sub.mesa on 2009-04-24
Could you tell me how to edit the /etc/modules file, or give me an URL? the modprobe didn't work for me, said the module acpi_cpufreq was not found. I did use a dash (-) though, but it appears it converts it to underscore. Any suggestions?

---

### Post by frozenskunk on 2009-04-24
> sub.mesa  	
Re: CPU freq scaling gone in 9.04
Could you tell me how to edit the /etc/modules file, or give me an URL? the modprobe didn't work for me, said the module acpi_cpufreq was not found. I did use a dash (-) though, but it appears it converts it to underscore. Any suggestions? 

I had the same problem, modprobe didn't do it for me (though I saw my frequency go from 2.19 to 2.2 as reported earlier). I added the module and rebooted, and it worked like it used to in 8.10.

```
sudo gedit /etc/modules
```

and add the following to a new line at the end of the file and save:

```
acpi-cpufreq
```

Reboot, and (hopefully) all will be back to normal.

---

### Post by sub.mesa on 2009-04-24
I already tried that on my own, but that didn't work. :(

---

### Post by nusch on 2009-04-25
In my case I had to manually change /boot/grub/menu.lst because upgrade added new kernel and didn't change entries in menu, so it was still runing old one.

---

### Post by curtiswtaylorjr on 2009-04-27
I had the same problem and was looking for a solution. I tried the command above but it told me "FATAL: Module acpi_cpufreq not found.". So I searched Synaptic for acpi-cpufreq and found powernowd which in it's description looked like it should be installed. So I installed powernowd and all is well. As soon as the package finished installing my cpu scaled back not even a restart was required.

---

### Post by Geryon on 2009-04-28
> **curtiswtaylorjr said:**
> I had the same problem and was looking for a solution. I tried the command above but it told me "FATAL: Module acpi_cpufreq not found.". So I searched Synaptic for acpi-cpufreq and found powernowd which in it's description looked like it should be installed. So I installed powernowd and all is well. As soon as the package finished installing my cpu scaled back not even a restart was required.

Hey man, thanks for the tip.  This worked like a champ on my Averatec 3200.  I feel my lap cooling off already.  phew.. :) 

FYI, I tried modprobing acpi-cpufreq only to tell me:

# modprobe acpi-cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.28-6-386/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

But installing powernowd did the trick.  Thanks a bunch!

---

### Post by JonyBoyct on 2009-05-01
Thanks getting ***powernowd*** from symantic worked like a champ.

---

### Post by rainwalker on 2009-05-13
Installing powernowd didn't work for me (though it looked like it did at first); I installed it and rebooted, and the CPU frequency scaling monitor in the panel finally let me set my processor back up to 1700 MHz (Pentium M). Just like when I first added the applet earlier today, it stayed at that speed for about 30 seconds then dropped back down to 600 MHz (where I'm stuck now), meanwhile my whole computer slowed down and the fan went crazy (but it was blowing out cool air, not warm)...so I think it got confused. 
Also, adding "acpi-cpufreq" to my modules didn't do anything, and modprobing it from the terminal says that the module was not found.

EDIT:
Nevermind, I lied. Scaling works, at least in "ondemand" mode, so I'm not going to mess with it any more.

---

### Post by vdubbus77 on 2009-05-24
> **frozenskunk said:**
> I had the same problem, modprobe didn't do it for me (though I saw my frequency go from 2.19 to 2.2 as reported earlier). I added the module and rebooted, and it worked like it used to in 8.10.

```
sudo gedit /etc/modules
```

and add the following to a new line at the end of the file and save:

```
acpi-cpufreq
```

Reboot, and (hopefully) all will be back to normal.

This worked for me, Thank you.

---

### Post by schmolch on 2009-05-29
How do i get this module?
I have powernowd installed but the module is not found.

---

