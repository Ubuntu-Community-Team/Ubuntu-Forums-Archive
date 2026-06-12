---
title: "Is it just me or is Ubuntu REALLY slow???"
date: 2008-11-24
forum: x86 64-bit Users
---

### Post by Predtech on 2008-11-24
Ok guys, i need some help understanding something here.
I have been running ubuntu 8.10 64bit for a while now but i can't understand why i get such shitty performance when trying to multitask, such as...... opening a .rar file or 2 while listening to banshee and burning 2 dual layer dvd's, and then when i try to open up firefox it takes FOREVER!!!!!
Just so you don't think i'm imagining things, my pc has a Q6600 quad core cpu and that's water cooled and also i have 8GB of DDR2 800 MHz Patriot ram running under the hood, so i know my pc is up to spec.
It just seems like when i ran Windows that i didn't have these slowdown problems, although it was considerably slower booting up than Ubuntu is.

Please, some help me understand what is going on???

---

### Post by Predtech on 2008-11-24
Bump!
Anyone???????

---

### Post by tuxxy on 2008-11-24
Firefox should load instantly all browsers should, maybe its a hardware issue is this a clean install or an update of Hardy?

Have you ever ran Hardy and was that the same? Do you have effects enabled? if so does it still act slow without them enabled? without effects it should be super fast

---

### Post by Predtech on 2008-11-24
It's a clean install. I used to run hardy but it was 32 bit. I didn't notice any difference between then and now. I don't see how it could be a hardware issue because my hardware is definitely capable of handling these tasks

---

### Post by fjgaude on 2008-11-24
What does this command show from Terminal:

```
sudo hdparm -tT /dev/sda1
```

Use the name of your best drive instead of the /dev/sda1. Run the code three times and let us see all three runs. Thank you.

The program **hdparm** is in the repository if you don't have it already.

---

### Post by and.duncan on 2008-11-24
> **fjgaude said:**
> What does this command show from Terminal:

```
sudo hdparm -tT /dev/sda1
```


Hey that's neat :) Didn't know about that.

And I agree, sounds like doing all that you're doing too many disk accesses at once. That or maybe the unrar is working over all the cpu's and not leaving any for anything else.

---

### Post by Predtech on 2008-11-24
> **fjgaude said:**
> What does this command show from Terminal:

```
sudo hdparm -tT /dev/sda1
```

Use the name of your best drive instead of the /dev/sda1. Run the code three times and let us see all three runs. Thank you.

The program **hdparm** is in the repository if you don't have it already.

sda1 is my best drive, it's my SATA drive. I got this result
first:

/dev/sda1:
 Timing cached reads:   6114 MB in  2.00 seconds = 3058.22 MB/sec
 Timing buffered disk reads:  206 MB in  3.02 seconds =  68.20 MB/sec

second:
/dev/sda1:
 Timing cached reads:   6620 MB in  2.00 seconds = 3313.32 MB/sec
 Timing buffered disk reads:  202 MB in  3.02 seconds =  66.93 MB/sec

Third:
/dev/sda1:
 Timing cached reads:   6376 MB in  2.00 seconds = 3192.20 MB/sec
 Timing buffered disk reads:  192 MB in  3.02 seconds =  63.57 MB/sec

---

### Post by cariboo on 2008-11-24
It looks like you've got a disk I/O problem i've got an older AMD64 3800+ dual core with 2Mb ram and my sata numbers look like this:

```
/dev/sda:
 Timing cached reads:   1668 MB in  2.00 seconds = 834.16 MB/sec
 Timing buffered disk reads:  236 MB in  3.00 seconds =  78.61 MB/sec
```

Running it three times I only see .07MB difference from first to last.

Jim

---

### Post by Predtech on 2008-11-24
I don't know man, i never had these kinds of problems in windows. 
But it is a strange problem i do admit.

---

### Post by Cracauer on 2008-11-24
It's either that crazy urlcalssifier Firefox problem.

Or you have the DVD drives on the same bus as a harddrive.

What buses do you have the harddrives and DVD burners on, exactly?

---

### Post by Predtech on 2008-11-24
Each dvd drive is SATA and so is the HDD so they all have their own individual SATA ports.
how can i check if they are on the same bus?

---

### Post by Arup on 2008-11-24
Sata are meant to be daisy chained like SCSI and all share the same bus, there is ID given to the drives and there is no master/slave issue here like IDE.

---

### Post by Cracauer on 2008-11-25
> **Predtech said:**
> Each dvd drive is SATA and so is the HDD so they all have their own individual SATA ports.
how can i check if they are on the same bus?

dmesg | egrep '^(scsi|ata|sd|ha|ide)'

In general, two sata ports share parts of a controller. CD/DVD are bus hogs. I wouldn't rule out one can block the other.

Post the above, maybe we can suggest some swapping around.

Please post one cut'n'paste of `top` that looks typical during this slowdown (press q, then cut).

---

### Post by offroad64 on 2008-11-25
What kind os sata drives are they?  I had some Seagate drives that came shipped with the jumper set to Sata 1 not Sata 2. When I changed them what a difference.

---

### Post by fjgaude on 2008-11-25
> **Predtech said:**
> sda1 is my best drive, it's my SATA drive. I got this result
first:

/dev/sda1:
 Timing cached reads:   6114 MB in  2.00 seconds = 3058.22 MB/sec
 Timing buffered disk reads:  206 MB in  3.02 seconds =  68.20 MB/sec

second:
/dev/sda1:
 Timing cached reads:   6620 MB in  2.00 seconds = 3313.32 MB/sec
 Timing buffered disk reads:  202 MB in  3.02 seconds =  66.93 MB/sec

Third:
/dev/sda1:
 Timing cached reads:   6376 MB in  2.00 seconds = 3192.20 MB/sec
 Timing buffered disk reads:  192 MB in  3.02 seconds =  63.57 MB/sec

Okay, all looks fine there. Now you likely have an I/O wait situation with what you are doing. You can see this with the System Monitor, noticing the IOWait portition of the Processor panel. This monitor is part of Add to Panel of Gnome. I change the color of the I/OWait to yellow so I can easily see it. SATA is not SCSI and I think much of the wait is caused by the electronics in SATA drives.

---

### Post by Predtech on 2008-11-25
Ok, I decided to reinstall just to get a fresh start. I'll post with the results tomorrow.

---

### Post by Funnnny on 2008-11-25
Hope that your computer will run fine. Like me

---

### Post by nss0000 on 2008-11-26
CBoo:

YIKES! I get a variation of ~100 MB/s in a series of "Timing cached reads". From about 1500 to 2000 MB/s over 2.0 sec.

---

### Post by paulisdead on 2008-11-26
> **nss0000 said:**
> CBoo:

YIKES! I get a variation of ~100 MB/s in a series of "Timing cached reads". From about 1500 to 2000 MB/s over 2.0 sec.

That's nothing to worry about, cache reads can be very erratic.

I've been experiencing a similiar problem with Ubuntu 8.04 and 8.10.  I can't remember if the problem was around in 7.10, but I know it wasn't in 7.04.

It definitely seems to be disk related, and my hdparm results are perfectly normal.  I've tried turning NCQ on and off in the kernel, and that's not helped.  Say I'm copying a large file(s) from my desktop to my file server, or to another local drive or partition, most apps, especially firefox, get really unresponsive.  Also, my copy speeds seem to seldom do over 20MB/s, whereas I know I should be able to copy at 40-60MB/s via NFS to my fileserver.  It used to work quite well under gentoo and older versions of Ubuntu.  Running copies from the command line produces the same result.  Maybe I should try it with X stopped completely for the hell of it.

My 32bit install on my box at work doesn't have any of the speed issues.  It's also definitely not as good of hardware.

I think it was phoronix that did an article on how Ubuntu's been slowing down, and it really seemed to apply to this situation.  They didn't offer any solution, but seemed to theorize it was the more recent kernels causing the problems.

---

### Post by CholericKoala on 2008-11-26
If you have a nice system like the original poster's, the hardware cant be the problem.  Something is either eating the RAM or CPU.

Memory leak?  Process thrashing?

---

### Post by paulisdead on 2008-11-26
> **CholericKoala said:**
> If you have a nice system like the original poster's, the hardware cant be the problem.  Something is either eating the RAM or CPU.

Memory leak?  Process thrashing?

Nope, RAM usage in top and gkrellm show I've got plenty free.  I'm on 64bit in order to get the full 4GBs of RAM after all.  CPU usage in top and GKRELLM is low too.  Everything seems to be waiting on I/O.  All I have to do is run a large file copy to drag my system to a crawl.  I can do the same on my work box, and it continues to chug along nicely and allow me to keep working while the copy runs.

---

### Post by CholericKoala on 2008-11-26
In your system monitor, try enabling all the other "information fields" in preferences.  See if there is any hog on any of the categories.

---

### Post by fjgaude on 2008-11-26
> **paulisdead said:**
> Nope, RAM usage in top and gkrellm show I've got plenty free.  I'm on 64bit in order to get the full 4GBs of RAM after all.  CPU usage in top and GKRELLM is low too.  Everything seems to be waiting on I/O.  All I have to do is run a large file copy to drag my system to a crawl.  I can do the same on my work box, and it continues to chug along nicely and allow me to keep working while the copy runs.

Everything is waiting on I/O. Now what is I/O other than drives, RAM? My experience with fast memory and CPUs is that drive I/O is the bottleneck. Thus I have all programs on one drive and all data on another (usually raid5). That setup helps!

If you really want thru-put SCSI is indicated with its parallel processing built-in to each drive and long command queues. There a reason why they are so expensive! Multi-core is one thing but it is not the whole thing, eh?

---

### Post by CholericKoala on 2008-11-26
There is no reason why anyone should ever have to have RAID.  RAID is nice if you want a little extra boost or if you are in a business and need backups.  One single drive should do just fine.  There is a more important problem at hand.  If it is a process that is causing it, nothing else would help that.

---

### Post by paulisdead on 2008-11-26
> **fjgaude said:**
> Everything is waiting on I/O. Now what is I/O other than drives, RAM? My experience with fast memory and CPUs is that drive I/O is the bottleneck. Thus I have all programs on one drive and all data on another (usually raid5). That setup helps!

If you really want thru-put SCSI is indicated with its parallel processing built-in to each drive and long command queues. There a reason why they are so expensive! Multi-core is one thing but it is not the whole thing, eh?

The point is, I'm not getting anywhere near the performance I should be getting from this hardware.  The OS drive is a 10,000 RPM Raptor X 150GB, and I have /home on a 200GB seagate 7200.8 SATA drive.  CPU is a 3.2ghz Core2 duo, and I've got 4GBs of ddr2 1066mhz RAM.  Ya SCSI's great, and SAS is too, but not affordable.  I do have 2 RAID 5 arrays in my file server, but that's only to protect against a drive failure, and not so much for speed gains.  I really don't need RAID on my desktop.

Like I was saying, when I used to run gentoo or Ubuntu 7.04 on this box, it was a lot faster.  I don't recall if 7.10 had the issue or not, for me.

I will take a look at the sys mon to see if I can nail anything down when I get home, but I am thinking I agree with phoronix and that it could be the kernel.  I should probably try grabbing some vanilla kernels or older kernels, maybe, and see how that goes.

I found a link to the Phoronix article that talks about this issue, and seems like it maybe applicable.  [http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1)

I'm not saying this applies to everyone and all hardware setups, but I do think there's something going on with certain configs under Ubuntu.

---

### Post by fjgaude on 2008-11-26
Okay I think there is something to what you are saying, pointing to, with **7.10**:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = **9622.09** MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = **212.01** MB/sec
```

With **8.10**:

```
/dev/md32:
 Timing cached reads:   18182 MB in  2.00 seconds = **9103.61** MB/sec
 Timing buffered disk reads:  540 MB in  3.00 seconds = **179.75** MB/sec
```

I can't really say if it the OS or not, but this is what I get, same CPU, same memory, same individual drive thruput.

I know there are bug reports already about this. We wait and see what happens along the journey to **9.04**, which is supposed to be the fastest OS ever.

---

### Post by paulisdead on 2008-11-26
> **fjgaude said:**
> Okay I think there is something to what you are saying, pointing to, with **7.10**:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = **9622.09** MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = **212.01** MB/sec
```

With **8.10**:

```
/dev/md32:
 Timing cached reads:   18182 MB in  2.00 seconds = **9103.61** MB/sec
 Timing buffered disk reads:  540 MB in  3.00 seconds = **179.75** MB/sec
```

I can't really say if it the OS or not, but this is what I get, same CPU, same memory, same individual drive thruput.

I know there are bug reports already about this. We wait and see what happens along the journey to **9.04**, which is supposed to be the fastest OS ever.

My hdparm's have decreased a little bit since 7.04 (maybe 7.10 as well), but I'm not entirely sure that's where the problem is.  The numbers I'm getting should definitely still be able to produce a responsive system.

I'm not really seeing much from system monitor that top didn't already tell me.

---

### Post by fjgaude on 2008-11-26
Can you see the I/OWait aspect of the panel? It shows as one of five in the Monitored Resources, Processor. Change the color of IOWait to yellow and it shows in the panel clearly.

You get to this all by right clicking the icon in the panel and then going to Preferences. top doesn't show i/o wait at all. Does show load average, which could be useful if you are doing heavy multitasking.

---

### Post by fjgaude on 2008-11-26
Can you see the I/OWait aspect of the panel? It shows as one of five in the Monitored Resources, Processor. Change the color of IOWait to yellow and it shows in the panel clearly.

You get to this all by right clicking the icon in the panel and then going to Preferences. **top** doesn't show i/o wait at all. Does show load average, which could be useful if you are doing heavy multitasking.

You might be able to get some info that is useful from **iotop**, which is available in the respository.

---

### Post by paulisdead on 2008-11-26
> **fjgaude said:**
> Can you see the I/OWait aspect of the panel? It shows as one of five in the Monitored Resources, Processor. Change the color of IOWait to yellow and it shows in the panel clearly.

You get to this all by right clicking the icon in the panel and then going to Preferences. **top** doesn't show i/o wait at all. Does show load average, which could be useful if you are doing heavy multitasking.

You might be able to get some info that is useful from **iotop**, which is available in the respository.

I have a waiting channel, is that it?  I need to wait until DVD::RIPs done with some stuff, and I will try a file copy to see what's going on.  I'm not sure what I'm really looking for in that column, though.

Frequently Firefox will be loading a bunch of sites, and it just goes gray while it's unresponsive.  Sometimes Nautilus will do the same with file copies, especially if I try to just browse files in another Nautilus window while the copy runs.

The 2.2ghz AMD X2 with 2GBs of RAM runs much better, but it's a 32bit ubuntu box I run at work.  I don't think I've ever had Firefox just go gray and unresponsive on that machine before.

---

### Post by fjgaude on 2008-11-26
You get to the IOWait panel to change its color by right-clicking the icon in the little panel for System Monitor. Click then Preferences. From there you see the options: Processor, Memory, Network, Swap Space, Load, Harddisk. It should default to Processor. See the IOWait icon, second from right. Click it, click the eye dropper. Move it to yellow on the triangle. Click OK, Close.

From then on you can see how the I/O Waiting is doing in the Gnome panel for System Monitor.

The graying of windows started with 8.04. It indicates a wait caused by system I/O load.

---

### Post by Cracauer on 2008-11-26
> **paulisdead said:**
> Nope, RAM usage in top and gkrellm show I've got plenty free.  I'm on 64bit in order to get the full 4GBs of RAM after all.  CPU usage in top and GKRELLM is low too.  Everything seems to be waiting on I/O.  All I have to do is run a large file copy to drag my system to a crawl.  I can do the same on my work box, and it continues to chug along nicely and allow me to keep working while the copy runs.

As I said before, I need to see a full top output, including the iowait and idle numbers, from a point in time where the two copies plus two DVD burns are going on.

Don't forget to press "1" to get per-CPU stats.

---

### Post by gatecrasher on 2009-01-23
I hate to say it but truth be told, XP AND Vista outperform the default Ubuntu 32bit installation on newer Dell Laptops. I'm really disgusted with the path that Linux distros in general have gone. 

/gc

---

### Post by steveneddy on 2009-01-23
My only answer without reading the entire thread is that you may have upgraded instead of a complete reinstall going from 8.04 to 8.10.

I would suggest backing up /home and doing a total reinstall.

---

### Post by xoros on 2009-01-24
Yes a plain ubuntu installation has become very slow.  Ubuntu has unfortunately made the move toward being bloat-ware.  

That is why I run Xubuntu with Openbox as the window manager. 

The only good thing left about Ubuntu is it's repositories and support of the community. 

This of course is all MHO... other may view things differently, I like to feel _we all_ have a right to express our opinions.

---

### Post by theotherphil on 2009-01-30
It certainly looks like the OP has a disk I/O problem. With a "non performance" 300Gb SATA drive I get HDParm results twice as fast on a fresh Ubuntu 8.10 x64 install:

```
/dev/sda1:
 Timing cached reads:   15656 MB in  2.00 seconds = 7838.37 MB/sec
 Timing buffered disk reads:  314 MB in  3.02 seconds = 104.12 MB/sec
phil@Chaos:~$ sudo hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   15564 MB in  2.00 seconds = 7792.59 MB/sec
 Timing buffered disk reads:  318 MB in  3.01 seconds = 105.63 MB/sec
phil@Chaos:~$ sudo hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   15374 MB in  2.00 seconds = 7696.64 MB/sec
 Timing buffered disk reads:  316 MB in  3.00 seconds = 105.29 MB/sec
```

---

### Post by Noo on 2009-01-30
I seem to have a similar problem (also with 8.10).

I have three SATA drives in my system, when I copy files around between them in Vista it avarages around 90MB/s transfer rate. In ubuntu I only get 50MB/s. I've set the IOWait in System Monitor to yellow and when copying a huge file (8 GB) in Ubuntu the yellow bars average around 50%.

I think it's strange direct disk to disk transfer speeds are only half in Ubuntu compared to Vista. Otherwise I have no performance issues.

I also ran some hdparm tests:

```

---------------------------------------------------------------------
/dev/sda: Samsung Spinpoint F1 1 TB
---------------------------------------------------------------------
noob@Ubuntu-PC:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   3236 MB in  2.00 seconds = 1617.72 MB/sec
 Timing buffered disk reads:  346 MB in  3.01 seconds = 115.05 MB/sec
noob@Ubuntu-PC:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   3230 MB in  2.00 seconds = 1615.21 MB/sec
 Timing buffered disk reads:  346 MB in  3.01 seconds = 114.88 MB/sec
noob@Ubuntu-PC:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   3246 MB in  2.00 seconds = 1622.66 MB/sec
 Timing buffered disk reads:  348 MB in  3.02 seconds = 115.36 MB/sec

---------------------------------------------------------------------
/dev/sdb: WD Raptor 74 GB
---------------------------------------------------------------------
noob@Ubuntu-PC:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   3250 MB in  2.00 seconds = 1624.92 MB/sec
 Timing buffered disk reads:  238 MB in  3.01 seconds =  79.15 MB/sec
noob@Ubuntu-PC:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   3162 MB in  2.00 seconds = 1581.18 MB/sec
 Timing buffered disk reads:  240 MB in  3.02 seconds =  79.56 MB/sec
noob@Ubuntu-PC:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   3256 MB in  2.00 seconds = 1627.96 MB/sec
 Timing buffered disk reads:  238 MB in  3.02 seconds =  78.80 MB/sec
noob@Ubuntu-PC:~$ sudo hdparm -tT /dev/sdc

---------------------------------------------------------------------
/dev/sdc: WD My Book Studio Edition II 2 TB (eSATA, 2 * 1 TB, RAID0)
---------------------------------------------------------------------

/dev/sdc:
 Timing cached reads:   3216 MB in  2.00 seconds = 1608.19 MB/sec
 Timing buffered disk reads:  336 MB in  3.02 seconds = 111.33 MB/sec
noob@Ubuntu-PC:~$ sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   3200 MB in  2.00 seconds = 1599.91 MB/sec
 Timing buffered disk reads:  336 MB in  3.01 seconds = 111.79 MB/sec
noob@Ubuntu-PC:~$ sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   3232 MB in  2.00 seconds = 1616.53 MB/sec
 Timing buffered disk reads:  336 MB in  3.02 seconds = 111.37 MB/sec

```

---

### Post by r m h on 2009-02-02
Ubuntu 8.10 is very capable of high performance.  You must have something configured to be limiting your throughput....

Note that I'm running Ubuntu 8.10 Desktop x86_64.
sda is a RAID1 SATA II array (2x250GB off of an ASUS Rampage II Extreme)
sdb is a RAID5 SATA II array (6x250GB off of a 3Ware 9650SE PCI-Extreme)

```
~# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   16058 MB in  2.00 seconds = 8037.71 MB/sec
 Timing buffered disk reads:  282 MB in  3.02 seconds =  93.53 MB/sec
root@iceage:~# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   15332 MB in  2.00 seconds = 7673.95 MB/sec
 Timing buffered disk reads:  482 MB in  3.01 seconds = 160.13 MB/sec

~# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   17856 MB in  2.00 seconds = 8938.65 MB/sec
 Timing buffered disk reads:  280 MB in  3.02 seconds =  92.72 MB/sec
root@iceage:~# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   17456 MB in  2.00 seconds = 8737.55 MB/sec
 Timing buffered disk reads:  474 MB in  3.01 seconds = 157.68 MB/sec

~# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   16846 MB in  2.00 seconds = 8432.70 MB/sec
 Timing buffered disk reads:  282 MB in  3.00 seconds =  93.91 MB/sec
root@iceage:~# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   15828 MB in  2.00 seconds = 7921.85 MB/sec
 Timing buffered disk reads:  470 MB in  3.00 seconds = 156.46 MB/sec


```

---

### Post by jrusso2 on 2009-02-02
> **Predtech said:**
> Ok guys, i need some help understanding something here.
I have been running ubuntu 8.10 64bit for a while now but i can't understand why i get such shitty performance when trying to multitask, such as...... opening a .rar file or 2 while listening to banshee and burning 2 dual layer dvd's, and then when i try to open up firefox it takes FOREVER!!!!!
Just so you don't think i'm imagining things, my pc has a Q6600 quad core cpu and that's water cooled and also i have 8GB of DDR2 800 MHz Patriot ram running under the hood, so i know my pc is up to spec.
It just seems like when i ran Windows that i didn't have these slowdown problems, although it was considerably slower booting up than Ubuntu is.

Please, some help me understand what is going on???

While its true that Ubuntu is a bit slower then many other Linux its not slower then Vista.  You have plenty of PC it should run very fast therefore I am thinking something is not right.  Some hardware or something is not installed or configured right.

Opening a large rar is a lot of cpu so doing that plus the other things your doing would use a lot of power on Windows too.

---

### Post by Yellow Pasque on 2009-02-02
Ubuntu isn't the fastest Linux distro because it doesn't try to be. Ubuntu's focus is on compatibility, not performance. You can optimize Ubuntu to a certain extent, but it will never be the fastest distro on the menu.

I love Ubuntu, and still use it regularly for experimental tasks, but most of the time, I use Sidux or Arch Linux for my daily computing needs.

---

### Post by johnjohn2 on 2009-02-04
This outpur is from a two year old drive WD Caviar

/> dev/sda:
 Timing cached reads:   1552 MB in  2.00 seconds = 776.11 MB/sec
 Timing buffered disk reads:  294 MB in  3.01 seconds =  97.78 MB/sec


regards john

:popcorn:

---

### Post by joey-elijah on 2009-02-04
Whilst my ubuntu isn't overly slow, it's certainly not as fast as it once was, nor as fast as 32 bit felt. 

Firefox takes an age to open, as well. but i think that's firefox...

---

### Post by philinux on 2009-02-04
```
sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1258 MB in  2.00 seconds = 629.25 MB/sec
 Timing buffered disk reads:  262 MB in  3.00 seconds =  87.32 MB/sec

```

One year old 250gig drive.

---

### Post by banana989 on 2009-02-04
```

desktop:~$ sudo hdparm -Tt /dev/sdb1

/dev/sdb1:
 Timing cached reads:   1416 MB in  2.00 seconds = 708.25 MB/sec
 Timing buffered disk reads:  316 MB in  3.00 seconds = 105.27 MB/sec
desktop:~$ sudo hdparm -Tt /dev/sdb1

/dev/sdb1:
 Timing cached reads:   1278 MB in  2.00 seconds = 638.70 MB/sec
 Timing buffered disk reads:  318 MB in  3.00 seconds = 105.90 MB/sec

```

This is a brand new Western Digital WD3200KSRTL Caviar 320 GB SATA; are these normal numbers? 

Additionally when moving files from a disk that gets similar numbers, Gnome reports transfer rates as low as 3MB/s.

---

### Post by Throne777 on 2009-02-04
> **joey-elijah said:**
> Whilst my ubuntu isn't overly slow, it's certainly not as fast as it once was, nor as fast as 32 bit felt. 

Firefox takes an age to open, as well. but i think that's firefox...

I've found Firefox takes a very long time to open. At times I've had about 3 tabs up and it nearly destroyed my system (and I have a AMD x64 4200, 1 gig RAM, 128MB GeForce 6600, 10,000rpm hard drive). Banshee at times slows my system to a crawl, as well. It's ridiculous. Especially as I run virtually no desktop effects.
Feels very sluggish with no good reason for it to be so. Frustrating times.

---

### Post by DeMus on 2009-02-04
> **and.duncan said:**
> Hey that's neat :) Didn't know about that.

And I agree, sounds like doing all that you're doing too many disk accesses at once. That or maybe the unrar is working over all the cpu's and not leaving any for anything else.

Yes, Unrar really slows you down. When I use it, the System Monitor hardly shows any activity, but never the less the pc is terribly slow.
When not using Unrar I may not complain. And I also do several things at the time. Maybe not all CPU consuming things but a lot of them at the same time.
It's just that Unrar does something strange with the CPU.

---

### Post by DeMus on 2009-02-04
> **banana989 said:**
> ```

desktop:~$ sudo hdparm -Tt /dev/sdb1

/dev/sdb1:
 Timing cached reads:   1416 MB in  2.00 seconds = 708.25 MB/sec
 Timing buffered disk reads:  316 MB in  3.00 seconds = 105.27 MB/sec
desktop:~$ sudo hdparm -Tt /dev/sdb1

/dev/sdb1:
 Timing cached reads:   1278 MB in  2.00 seconds = 638.70 MB/sec
 Timing buffered disk reads:  318 MB in  3.00 seconds = 105.90 MB/sec

```

This is a brand new Western Digital WD3200KSRTL Caviar 320 GB SATA; are these normal numbers? 

Additionally when moving files from a disk that gets similar numbers, Gnome reports transfer rates as low as 3MB/s.


My outcome to the hdparm -Tt instruction:

/dev/sda:
 Timing cached reads:   10208 MB in  2.00 seconds = 5108.70 MB/sec
 Timing buffered disk reads:  228 MB in  3.01 seconds =  75.72 MB/sec
jan@2-Quad:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   10896 MB in  2.00 seconds = 5453.45 MB/sec
 Timing buffered disk reads:  232 MB in  3.01 seconds =  77.18 MB/sec

sda is my Windows XP-64 disk with a C and a D partition
sdb is Ubuntu 64 with a /, a usr, a var and a /home partition

---

### Post by paulisdead on 2009-02-04
Wow, I forgot about this thread after getting busy, and then having my hard drive in the system die on me.  I replaced it with a 1TB seagate, and still see the slowness under I/O.  When I set the gnome sysmon to monitor I/O as yellow, whenever there was slowness the whole chart was filled with yellow, so it's definitely waiting on I/O.  Doing just about anything with firefox seems to cause a lot of I/O activity.

I did see an article awhile back, that I unfortunately don't have a link to, but it talks about a problem with firefox and ext3.  It was something about the way firefox did writes to the drive, and did a ridiculous amount of them that didn't play well ext3 in some situations.  I'm thinking this could be the issue.  If I ever have time, I should try a clean boot, and do a bunch of file copies and other I/O heavy activity without even opening firefox.  I don't know when I'll be able to reboot this box, since I keep a lot of stuff running on it all the time.

I'm anxiously awaiting 9.04 so I can reinstall with ext4, and see how things are with that.  Plus, Western Digital replaced my old raptor 150 with a new velociraptor 150, so that seems like a good time to reload windows and ubuntu on here.

Ubuntu may not be the fastest distro, but when I first started using it on this box, it was nearly as fast as my Gentoo install.  It definitely performs worse today than it used to.  I understand there's some bloat going on, but come on, this isn't windows, we shouldn't be seeing drops like this.  When I was using gentoo, and the first versions of ubuntu I ran on this box, I could copy a file from this box, to my file server and pull a pretty consistent 40-50MB/s with NFS.  Now I'm lucky to get 12-15MB/s.  Weird thing is, If I leave out the hard drive, and say burn a DVD of files from the server, it goes blazing fast.  I have no problems burning over the network even when the DVD ramps up to over 18x.

---

### Post by Cracauer on 2009-02-04
Check the urlclassifier stuff in the profiles of your firefox.

That has been the reason for most Ubuntu systems that appeared slow lately.

---

### Post by paulisdead on 2009-02-05
> **Cracauer said:**
> Check the urlclassifier stuff in the profiles of your firefox.

That has been the reason for most Ubuntu systems that appeared slow lately.

I gave this a go, and it doesn't seem to have had any impact.

---

### Post by philinux on 2009-02-05
I've just tried this in Jaunty 64 bit and the results are similar to my previous post. (Intrepid 32 bit)

---

### Post by japju on 2009-02-05
> **paulisdead said:**
> 
I did see an article awhile back, that I unfortunately don't have a link to, but it talks about a problem with firefox and ext3.

Indeed, simple Google for "firefox ext3 filesystem issues" gives a clear account of the problem and fix to it:

[http://www.dslreports.com/forum/r20655561-Firefox-30-uses-fsync-excessively-ext3](http://www.dslreports.com/forum/r20655561-Firefox-30-uses-fsync-excessively-ext3)

Really silly Firefox issue......

---

### Post by paulisdead on 2009-02-06
> **japju said:**
> Indeed, simple Google for "firefox ext3 filesystem issues" gives a clear account of the problem and fix to it:

[http://www.dslreports.com/forum/r20655561-Firefox-30-uses-fsync-excessively-ext3](http://www.dslreports.com/forum/r20655561-Firefox-30-uses-fsync-excessively-ext3)

Really silly Firefox issue......

I gave some of the recommendations a go, and that still didn't seem to help.  It dawned on me, I forgot to disable NCQ again after I reinstalled, and doing that has actually improved things a lot.  I know I had it disabled when I had my old drive in the machine, but that drive did explode, so I guess it could have been slow because of hardware failure.  Either that, or all the tweaks I've done to firefox, plus disabling NCQ helped.

It still at times seems slow when I do heavy network uploads.  I'm starting to wonder if it's the NIC, or NIC driver causing issues there.  Heavier I/O seems to slow things down a lot less now that I have NCQ off.  At least my bursts coming off the drive are where they should be, according to gkrellm, it just seems like it's stalling waiting on the NIC to transfer now.  Before I disabled NCQ, it would be a much lower speed transfer.  I've noticed when I'm doing a big copy, and getting maybe 15MB/s or so to a local box, other apps connected to the outside internet slow down.

I'm going to have to poke around work, and see if I find a Gig-E nic to test this theory.  Maybe I should swipe a switch, too, just to make sure.  I'm still excited for ext4, and since I've got that velociraptor drive, I might as well reinstall 9.04.

---

### Post by darco on 2009-02-06
Even though Linux Mint is based on Ubuntu, it wouldnt hurt to try it. I just installed the latest x64 build and its rock solid and extremely fast.
I have a single Sata 500 gig hdd w/4 gigs of memory with a swap file of 256mb and this OS is smooth as silk...

darco

---

### Post by fart_flower on 2009-02-28
For what little it's worth, the following bugzilla thread seems to be discussing this exact same i/o problem.  Doesn't look to be Ubuntu specific.

[http://bugzilla.kernel.org/show_bug.cgi?id=12309](http://bugzilla.kernel.org/show_bug.cgi?id=12309)

---

