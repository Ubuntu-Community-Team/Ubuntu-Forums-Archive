---
title: "AMD X2 CPU Frequency Scaling - powernowd"
date: 2008-05-03
forum: x86 64-bit Users
---

### Post by awi on 2008-05-03
Hi. I was having the message 

> CPU frequency scaling unsupported
You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

And looking for a solution, tried cpufreqd, then I checked the site, and saw that there were no News since 2008. :(

After reinstalling powernowd, I realized that the Gnome applet went to 800Mhz!
I rebooted the machine, and the same issue was there, no cpu scaling...
Then I realize, after some trial and error, that the module powernow_k8, the one that got me this output from /var/log/messages
```

May  3 21:40:32 megan kernel: [   33.617391] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
May  3 21:40:32 megan kernel: [   33.617567] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x13
May  3 21:40:32 megan kernel: [   33.617572] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x15
May  3 21:40:32 megan kernel: [   33.617574] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x17
May  3 21:40:32 megan kernel: [   33.617576] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
```
wasn't there, when there were no cpu scaling support.

Added the line powernowd_k8 to the /etc/modules, rebooted and voila!
I got CPU Frequency scaling enabled.
BTW, I have a HP Pavilion tx1000z, and running:

```
root@megan:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy

root@megan:~# uname -a
Linux megan 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```

---

### Post by luke16 on 2008-05-24
I can't even install x64 hardy due to it stopping at the "starting powernowd" line when using the cd installation. Any ideas on how I would fix that when I can't even get to the desktop?

---

### Post by phlembob on 2008-05-25
I haven't used any software to scale frequency during normal operations, but in my bios I do set it higher.  I have no problems, but everything has its limits.  Overall, I haven't had any major problems, but I've seen little things that really don't stop my computer from doing its job.  For loading problems with a cd --- IDE HDDs _have not all_ worked well.  SATA HDDs work well and load fine.  SATA drives have a more logical storage sequencing than IDE drives.  Hardware specific problems will exist with many of the cheaper Chinese motherboards.  A lot of these manufacturers do not have the necessary QC standards to prevent software problems with their hardware.  Remember that most manufactures of hardware work with windows os, and like all computers --- windows is a monopoly needing broken up --- American based engineering tends to work with any OS with exception to American IDE HDDs. :lolflag:

---

### Post by Yellow Pasque on 2008-05-25
First off, verify your media is good. If it passes, try disabling "Cool 'n' Quiet" in the BIOS.

---

### Post by aaron.d on 2008-05-27
> **phlembob said:**
> I haven't used any software to scale frequency during normal operations, but in my bios I do set it higher.  I have no problems, but everything has its limits.  Overall, I haven't had any major problems, but I've seen little things that really don't stop my computer from doing its job.  For loading problems with a cd --- IDE HDDs _have not all_ worked well.  SATA HDDs work well and load fine.  SATA drives have a more logical storage sequencing than IDE drives.  Hardware specific problems will exist with many of the cheaper Chinese motherboards.  A lot of these manufacturers do not have the necessary QC standards to prevent software problems with their hardware.  Remember that most manufactures of hardware work with windows os, and like all computers --- windows is a monopoly needing broken up --- American based engineering tends to work with any OS with exception to American IDE HDDs. :lolflag:

:confused:

---

### Post by cubeist on 2008-05-28
If powernow is installed but not working, add at least one CPU frequency scaling monitor applet to your gnome-panel then type
```
sudo dpkg-reconfigure gnome-applets
```
and answer the questions.

I don't run mine with root powers and it fixed powernowd on my amd phenom.

---

### Post by awi on 2008-05-30
> **luke16 said:**
> I can't even install x64 hardy due to it stopping at the "starting powernowd" line when using the cd installation. Any ideas on how I would fix that when I can't even get to the desktop?

Maybe this post helps you:

[http://ubuntuforums.org/showthread.php?t=660687](http://ubuntuforums.org/showthread.php?t=660687)

---

### Post by luke16 on 2008-05-31
Turning cool and quiet off in the bios works, and I imagine that turning apic off would also work, but ideally, I would want a way to fix this so that scaling works.

Would reinstalling powernowd or anything like that possibly work?

---

### Post by Yellow Pasque on 2008-06-02
luke16, at this point it sounds like the CPU is not getting enough voltage. Try upping the Vcore a bit if your BIOS allows it (remember to check temps occasionally). Also, see if you can get a sensors readout from lm-sensors. Your 12V rail might be "sagging", as is common with cheap/OEM PSU's.

```
sudo apt-get install lm-sensors libsensors3 libsensors4 sensors-applet libsensors-applet-plugin0 hddtemp
sudo sensors-detect *(Answer 'y' to all the probe/module questions)*
```
Restart your system and you should be able to gather hardware info with the *sensors* command or by adding the Hardware Info Monitor applet to one of your GNOME panels/taskbars

---

### Post by luke16 on 2008-06-02
> **Temüjin said:**
> luke16, at this point it sounds like the CPU is not getting enough voltage. 

Where did that come from?

Sorry, but I'm fairly certain it's a problem with Ubuntu not being able to properly scale down X2 voltages, and not a system problem.

---

### Post by foxy123 on 2008-09-28
> **luke16 said:**
> I can't even install x64 hardy due to it stopping at the "starting powernowd" line when using the cd installation. Any ideas on how I would fix that when I can't even get to the desktop?

I've got the same problem with Intrepid. The CD hangs on 'powernowd'. I managed to install it with an Alternative CD but my PC still hangs on 'powernowd' and after I have uninstalled it on 'cpufreq something'.

I wonder if it is really a problem with undervoltage. The thing is that I use 32bit version of Hardy on this PC and it shuts off without any reason now and then. However, there is no problem with Windows whatever load I have it has never switched off.

The PSU should be enough (it is 550W). I can experiment with voltage in teh BIOS but I am a bit afraid to fry the CPU.

Any suggestions? Is there any way to see if the CPU or my graphic card are undervoltaged? I have lm-sensors and hardware monitor installed but what I should be looking for?

---

