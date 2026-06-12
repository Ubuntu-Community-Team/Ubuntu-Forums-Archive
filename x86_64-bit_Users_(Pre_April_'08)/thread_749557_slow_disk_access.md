---
title: "slow disk access?"
date: 2008-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by uwevoelker on 2008-04-08
Hello,

my system: Intel Q6600, 8 GB RAM, MSI P965 Platinum (ICH-8R) with 3 SATA drives Samsung HD501LJ, Samsung HD753LJ, Hitachi HDS725050KLA360 and Ubuntu 7.10 installed (upgraded from 7.04) with newest updates.

The 750 GB Samsung drive is quite new and it seems since then my system really slowed down. How can I diagnose this?

I have long runnings apps and can not simply shut the system down and remove disks in trial and error.

Here is the output of hdparm:

```

uwe@quad:/var/log$ sudo hddtemp /dev/sd[a-c]
/dev/sda: SAMSUNG HD501LJ: 39°C
/dev/sdb: SAMSUNG HD753LJ: 33°C
/dev/sdc: HDS725050KLA360: 44°C

uwe@quad:/var/log$ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:   60 MB in  3.31 seconds =  18.13 MB/sec
uwe@quad:/var/log$ sudo hdparm -t /dev/sdb

/dev/sdb:
 Timing buffered disk reads:   82 MB in  3.10 seconds =  26.45 MB/sec
uwe@quad:/var/log$ sudo hdparm -t /dev/sdc

/dev/sdc:
 Timing buffered disk reads:  160 MB in  3.02 seconds =  52.95 MB/sec
```

So the both Samsung drives seem to be very slow. What can I do further?

Thank you.

---

### Post by tamoneya on 2008-04-08
do some testing on the drives with the ultimate boot cd: [http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html).  You should do speed and integrity testing.  If you get the same results in UBCD as in ubuntu it is probably the drives.  Otherwise it is something in ubuntu and we will debug it from there.

---

### Post by fjgaude on 2008-04-08
It's hard to say... are the disks near full, the Samsungs?

The last two generations of hard drives clocked out at 50MB/sec and 70MB/sec, respectively, using the hdparm program.

You are on the controllers on your motherboard?

Are you saying the two Samsungs slowed down when you added the 750G Hitachi drive?

---

### Post by uwevoelker on 2008-04-08
They used to be near 100% full (the 500 GB Samsung and the 500 GB Hitachi) but then I bought the 750 GB Samsung and now it looks like this:
```

uwe@quad:~$ df -h
Dateisystem            Größe Benut  Verf Ben% Eingehängt auf
/dev/sda1             440G  340G   78G  82% /
varrun                4,0G  140K  4,0G   1% /var/run
varlock               4,0G     0  4,0G   0% /var/lock
udev                  4,0G  100K  4,0G   1% /dev
devshm                4,0G     0  4,0G   0% /dev/shm
lrm                   4,0G   38M  3,9G   1% /lib/modules/2.6.22-14-generic/volatile
/dev/sdc1             459G  423G   13G  98% /data1
/dev/sdb1             688G  337G  317G  52% /data2

```

So the fastest disk (/dev/sdc1 - Hitachi) is the fullest. And my system partion on the Samsung 500 GB is at 82%.

It might possible, that things slowed down when adding the third disk (750 GB Samsung), but I'm not 100% sure. I was feeling my system was a bit slow for its power (quad core, enough RAM).

One interesting thing: When adding the third drive I installed Sharkoon Vibe-Fixer for every disk. The disks are now in a 5,25" slot with rubber bands. I have heard that this slows the access time down, but could this really have such a tremendous effect?

Yes, all disks (and my DVD-ROM if that matters) are on the onboard SATA controller (Intel ICH-8R).


I can not test with a boot CD right now, because I can not power down at the moment. Please lets try other diagnostic methods first.


When starting a terminal or Firefox it takes quite a while. Also Postgres is unusually slow.

Thanks.

---

### Post by uwevoelker on 2008-04-08
I tried [seeker]("http://www.linuxinsight.com/how_fast_is_your_disk.html"):

```

uwe@quad:~/Desktop$ sudo ./seeker /dev/sda
Benchmarking /dev/sda [476940MB], wait 30 seconds..............................
Results: 50 seeks/second, 19.93 ms random access time

uwe@quad:~/Desktop$ sudo ./seeker /dev/sdb
Benchmarking /dev/sdb [715404MB], wait 30 seconds.............................
Results: 56 seeks/second, 17.74 ms random access time

uwe@quad:~/Desktop$ sudo ./seeker /dev/sdc
Benchmarking /dev/sdc [476940MB], wait 30 seconds.............................
Results: 69 seeks/second, 14.46 ms random access time

```

So this corresponds to the MB/s rate from hdparm -t.

---

### Post by Jouke74 on 2008-04-08
The rubber won't make that much difference.

Did you try to add Harddisk tuning to the services settings under administration? 

Did you put the cables of the discs back at the right SATA controller point?  That Ubuntu is not looking for disk 1 at SATA connection point 1, while it is actually on 2 (and vice versa for the other disc)?

I am afraid in the end you do need a reboot :-) btw.

---

### Post by uwevoelker on 2008-04-08
No, harddisk tuning was not enabled (but now is).

I rebooted the machine a few times since then, so a reboot does not solve my problem.

Wow! The results from hdparm -t are there:

```

/dev/sda:
 Timing buffered disk reads:  208 MB in  3.00 seconds =  69.22 MB/sec

/dev/sdb:
 Timing buffered disk reads:  192 MB in  3.00 seconds =  63.97 MB/sec

```

And now the final test: my Postgres monster query...

... still slow (71 seconds).

So the numbers have improved but the applications seem to be still slow. Random access with seeker seems to be better on sdb, but worse on sda. But this might be caused by background programs (I have 3 VMs running, two of the doing intense work and Postgres is also working).

So thanks a lot, things improved a bit. What can I further do to diagnose this. Starting applications feels so slow. And sometimes the systems stucks (freezes) for a moment. I think when the hard disk is hit.

---

### Post by fjgaude on 2008-04-08
If you are accessing a drive while testing another with hdparm you will not get the maximum from the drive being tested. The values you are getting are alright for two-generation back drives, about 50MB/sec.

If you test the same drive with hdparm, three times in a row, you will get different values. Such tests are not that accurate, but good for relative comparisons.

The quad processor likely does little for many programs, for few see more than two cores if that many.

Here is my hdparm for what I have:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=24C; under max load, temp=41C, fan=1167 RPM; VCore=1.39/1.38v:
**/dev/md32:**
 Timing cached reads:   18948 MB in  2.00 seconds = 9487.52 MB/sec
 Timing buffered disk reads:  644 MB in  3.00 seconds = 214.42 MB/sec
root@sunshine:/home/frank# hdparm -tT /dev/md32

You can see what raid can do for drives, here I have four in raid5 with an overclocked duo E8400 at speed.

---

### Post by Jouke74 on 2008-04-09
After you are done tuning your HD's you can put it of again. Once tuning is done, you don't have to keep doing it. It's just like a car. :lolflag: The settings are stored, and now it will actually probably decrease your performance a bit. 

About 60 MB/s seems normal for these disks. My Raptor does about 70 MB/s. 
It's a bit low for the new Samsung. 

Are you sure your local host config is ok as well? (That's another causer of slowness)
Is there a difference when connected to the internet or not?
Is CPU frequency scaling on?
And are there any error messages in dmesg?
Cable question is still unanswered...
(Big list of questions I know).

I told you that you needed at least 1 reboot, for the tuning service to start, not multiple :-)

---

