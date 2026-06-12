---
title: "How to tell if I'm actually running Ubunutu AMD64 OS?"
date: 2007-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by oxbadfood on 2007-11-13
Hello, sorry to post something that on the surface seems so simple, but after much searching the forums and Google I couldn't answer this simple question:
[B]
After I've seemingly successfully installed Ubuntu 7.10 (Gutsy Gibbon), despite all the horror stories I've read on the forums, I can't tell if I am using my AMD64 6000+ Dual Core CPU to its potential...  Do I have a 64-bit OS installed and will it use the dual cores?[/B]

When I look at the kernel installed via ```
uname -r
``` I get the OS response "2.6.22-14-generic" which seems like what I get on my 32 bit system.  When I look at Synaptic and see what linux-kernel package are installed, it also provides little comfort/help because its description is that it is "This package provides kernel header files for version 2.6.22 on x86/x86_64."  Great.... so I have the Linux headers for both x86 and x86_64... and the linux-kernel I have installed (not the headers) doesn't even have any description of which CPU it was compiled for.

When I issue the command ```
top
``` I only see CPU usage delineated as one number... same with load averages... I sort of understand that with load averages it represents the effective number of CPUs required for the loading... so under 1.0 means an under-utilized system, and over 1.0 means more work that you have CPU/memory for.  I would have thought though there would be multiple CPU percentages listed for each core, or some way to see which threads (PIDs) were running on which processor.

Anyhow, sorry for the long post on such a simple question, but there has to be some magic software or command line switch for some application that can help me confirm/unravel/monitor the performance of both processor cores and ensure I'm using the 64 bit OS.

Thanks.

---

### Post by jocko on 2007-11-13
Check the output of:```

uname -m
```On 32bit you'll see i686, on 64bit you'll see x86_64.

And the gnome system monitor (system-->administration-->system monitor) should show both cores.
(Or press 1 (the number) while top is running to see both cores).

---

### Post by oxbadfood on 2007-11-13
Sweet.  Thanks!  I also did some searching and found that ```
uname -a
``` gives all the info that both you and I posted.  I also found a Linux Widget/Applet/whatever you call them that runs on the task bar in Gnome that has a CPU monitor.  The monitor allows for me to choose which core I want to see... so it does appear I'm running 64bit code with both cores.

SWEET.  Ubuntu seemingly rocks... it is almost like the people producing this distro actually understand what users want and continually make their product better.  Kudos guys.

On a side note, anyone know of an app or widget that monitors CPU temps, fan speeds, etc?  (Maybe it is an option on one of the ones you or I found... I haven't looked at all the tabs and options yet.)  **And is it normal to have the AMD retail heat sink fan stop running occasionally due to the Cool'N'Quite feature coupled with the Smart-Fan technology in the BIOS?**

---

### Post by IanW on 2007-11-13
[QUOTE=oxbadfood;3763928On a side note, anyone know of an app or widget that monitors CPU temps, fan speeds, etc?  (Maybe it is an option on one of the ones you or I found... I haven't looked at all the tabs and options yet.[/QUOTE]

Search these forums for "lm-sensors", and "sensors-applet". These will place all the info you could ever want about temps, fan speeds, and PSU voltages into your gnome panel.

---

### Post by John.Michael.Kane on 2007-11-13
This should get going with regards to monitoring.
[HOW TO: Install and configure lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors")
[Howto: Get a beautiful Conky setup]("http://ubuntuforums.org/showthread.php?t=205865&highlight=hddtemp")
[HowTo: Conky hddtemp]("http://ubuntuforums.org/showthread.php?t=282353&highlight=hddtemp")

These are the lines from my conky used with lm-sensors. you will have to adjust the cut numbers eg: -c13-16 to fit your cpu's
```
Core0..:: ${freq_dyn_g cpu0}Ghz ::: Usage: ${cpu cpu0}% ${cpubar cpu0 8,50} ${execi 8 sensors | grep -A 1 'Core0' | cut -c13-16 | sed '/^$/d'}C
```
```
Core1..:: ${freq_dyn_g cpu1}Ghz ::: Usage: ${cpu cpu1}% ${cpubar cpu1 8,50} ${execi 8 sensors | grep -A 1 'Core1' | cut -c13-16 | sed '/^$/d'}C
```

Hope it helps.

---

### Post by oxbadfood on 2007-11-13
Thanks guys!  Looking forward to checking out Conky... looks cool.  I also found in the main Ubuntu repo a package called "computertemp " that mimics the look of the processor frequency monitor.  (The frequency monitor is one of the default installed applets.)

I am still noticing that my heatsink fan, the default one provided in the retail box from AMD, seemingly stops running after a short while after boot-up.  It is a brand-new fan/heat pipe  heak sink with 4 pins on the connector.  Presumably, the 4 pin connection allows the BIOS to use Pulse Width Modulation (PWM) to spin the fan for more control over the fan speed... The three pin ones only use voltage to control the fan speed, but there is a minimum stall speed with a voltage fan.   Unfortunately, it seems like I have so much wind in the case via a bunch of 120 mm fans that all I see the heat sink fan doing is "breathing" by pulsing about 1Hz... not spinning mind you... but the temperature monitor still shows 35 C at idle and about 40 when under some load.

I will try ripping and transcoding a DVD or something processor intense to see if I can get the sucker to spin up the CPU fan!  (otherwise I will have to turn off the smart-fan feature in the BIOS!)

---

