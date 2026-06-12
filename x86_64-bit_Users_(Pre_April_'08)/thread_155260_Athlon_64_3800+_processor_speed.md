---
title: "Athlon 64 3800+ processor speed"
date: 2006-04-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by dajashby on 2006-04-04
I bought a new PC with the Athlon 64 3800+ processor.  It has 2 GB RAM, a 200GB SATA disk and a PCI Express graphics card (256 MB) , so it should be pretty brisk.  I bought the machine with the intention of running Linux with a VMWare virtual machine for Windows XP.  I started out with 32 bit Kubuntu, but then decided to switch to 64 bit,l so I've built the machine from scratch twice in the last month.  The second time I decided to also dual boot between Kubuntu and Windows.  My problem is that the native install of Windows tells me that the CPU is running at 2.4 Ghz, but Kubuntu, via cpuinfo, tells me that I'm running at only 1 Ghz!

I'm a member of CPDN (Climate Prediction), and their benchmarking also shows the Windows install running twice as fast as the Kubuntu install.  My one clue at the moment is that I'm running with a Vesa graphics driver, because X wouldn't run otherwise, but surely that wouldn't slow the machine down to that extent?](*,)

---

### Post by Sonicred on 2006-04-14
Kubuntu uses Powernowd to dynamically scale the CPU frequency based on load. My Athlon 3200+ system is running at 1Ghz now for example as all that I'm doing is writing a simple post. As soon as I start doing something that demands more power (such as encoding some audio files) Powernowd scales my processor to full speed.

So that is the issue that you're seeing. I'm not familiar with CPDN but I do occasionally run Folding@Home on my system and I'm guessing it's a similar idea. The issue with these programs and power scaling is that by default they run at such a low priority level that Powernowd never scales up. Folding@Home has a configuration switch to adjust this and perhaps CPDN does as well.

But, if not, here is what you can do:

1. Start running CPDN
2. Open a terminal window
3. Type "top" and press enter. This will show you a list of processes organized by their CPU usage (as an aside it is worth mentioning that the top command is far more complicated than this and can sort by tons of variables). CPDN should be the top process in the list.
4. Look for the PID or process ID of the CPDN executable which will be used in step 6
5. Press q to exit top
6. Type "renice 0 -p <pid>"

Powernowd should then recognize the new priority and scale your CPU up to the maximum level. Then you won't notice a difference between Linux and Windows anymore and the benchmarks should be very similar.

Power scaling is a wonderful thing. In practice it means that your CPU will be running at a lower temperature when maximum processing power isn't necessary. This can mean reduced noise as your fans won't be spinning as quickly as well as electrical savings. Brute force, distributed computing style applications are the only programs that I've ever had to adjust in this manner.

Hope this helps!

---

### Post by patrickfromspain on 2006-04-15
sudo apt-get install emifreq-applet

with that you should be able to manually change de cpu speed.

---

### Post by tonyisntcreative on 2006-04-16
All this is is AMD's "Cool&Quiet" working.  It ups your clock speed when you need it.  I personally love it and think it's a great feature.  Most of the time my CPU isn't even running over 30 degrees celcius lately!

Ex: 
Just using firefox
[[IMG]http://img159.imageshack.us/img159/4817/screenshottonyubuntu2xv.th.png[/IMG]](http://img159.imageshack.us/my.php?image=screenshottonyubuntu2xv.png)

In the middle of converting an mp3
[[IMG]http://img159.imageshack.us/img159/6837/screenshottonyubuntu13hs.th.png[/IMG]](http://img159.imageshack.us/my.php?image=screenshottonyubuntu13hs.png)

If you had the software installed to do this in windows you'd see it'd be the same way.

---

