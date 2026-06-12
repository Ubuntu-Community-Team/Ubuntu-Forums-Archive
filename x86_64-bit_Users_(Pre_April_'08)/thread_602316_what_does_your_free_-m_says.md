---
title: "what does your free -m says?"
date: 2007-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by nanbudh on 2007-11-04
please run free -m command on your terminals and paste the output. lets see if gutsy freeze-ups are memory things. here is mine:

this is with single instance of firefox running and nothing else:

shavin@ubuntu7:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           468        461          7          0         17        199
-/+ buffers/cache:        243        225
Swap:         1968          0       1968

my Machine: AMD Athlon 64 2800+, 512 MB RAM, 80 GB SATA SAMSUNG HArd Disk, LG 700E monitor, no extra graphics card, ASUS K8S-MX-UAYKZ motherboard,

---

### Post by Buffalo Soldier on 2007-11-04
Here's mine:
```

~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2006        829       1177          0         28        341
-/+ buffers/cache:        458       1547
Swap:         2094          0       2094

```

---

### Post by Yellow Pasque on 2007-11-04
```
             total       used       free     shared    buffers     cached
Mem:          1888        864       1024          0         80        445
-/+ buffers/cache:        338       1550
Swap:         5530          0       5530

```

EDIT: NOTE that the system only shows 1.8GB of RAM because 128MB is reserved for integrated video.

My Machine: AthlonX2 4800 Brisbane; 2 * 1GB DDR2-667; MSI K9AGNeo2 690G, 320GB HD w//512MB swap partition

---

### Post by HankB on 2007-11-04
```

hbarta@baobab:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1888       1792         95          0        239        917
-/+ buffers/cache:        636       1251
Swap:          815          0        815

```

HP L2000 laptop with 2GB RAM which is also shared with video.

-hank

---

### Post by yellowbread on 2007-11-04
It would be interesting to see how this is affected over time by various activities. 

This is a freshly booted system reflecting only a bit of web browsing. Swiftweasel and a terminal are the only applications running:

```
filbert@filbert-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1951        681       1269          0         55        263
-/+ buffers/cache:        362       1589
Swap:         4769          0       4769
```

I then played a 45 Mb wav file in XMMS, closed it down and got this:

```
filbert@filbert-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1951        810       1140          0        108        319
-/+ buffers/cache:        382       1568
Swap:         4769          0       4769
```

---

### Post by snkmad on 2007-11-04
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:           879        809         69          0         71        365
-/+ buffers/cache:        372        506
Swap:          988          0        988

```

1GB ram, with 128MB reserved for integraded video.

---

### Post by ansicplusplus on 2007-11-04
```
             total       used       free     shared    buffers     cached
Mem:          3959       3933         26          0         24       3190
-/+ buffers/cache:        718       3241
Swap:            0          0          0

```
I have 4G but 137M are missing. My graphics card has 256M.

Greetings, ansicplusplus

---

### Post by Quikee on 2007-11-04
```
             total       used       free     shared    buffers     cached
Mem:          3277       2352        924          0         70       1544
-/+ buffers/cache:        737       2539
Swap:         2870         38       2832

```

Because of a bug I have currently only 3.2 GB of total 4 GB of RAM. This is a state after 10 hours of "work". ;)

---

### Post by netbandit on 2007-11-04
```
             total       used       free     shared    buffers     cached
Mem:          8002        659       7342          0         18        229
-/+ buffers/cache:        412       7589
Swap:         7938          0       7938

```

---

### Post by Unspeakable Horror on 2007-11-04
```
             total       used       free     shared    buffers     cached
Mem:          2014       1999         14          0         43       1066
-/+ buffers/cache:        888       1125
Swap:         5890         22       5868

```

I'm running firefox, Basket, amule, boinc, tunapie and xmms.
By the way I don't have any crashes or problems after several days of running Ubuntu.

My machine: Core 2 6700, gtx8800, 2Gb RAM, P5N32-E SLI

---

### Post by Rhubarb on 2007-11-04
Same story here Quikee, have got 4GB of RAM, it's only detected as 3.2GB (on my 64bit gutsy install).

After lots of "work" and some memory hungry apps:-
```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3276       2720        556          0         38       2190
-/+ buffers/cache:        491       2785
Swap:         9593         37       9556
```

---

### Post by Sockerdrickan on 2007-11-05
robin@PC:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2026       1974         51          0         69       1620
-/+ buffers/cache:        284       1741
Swap:         4110          0       4110

---

### Post by santiagoward2000 on 2007-11-05
```
             total       used       free     shared    buffers     cached
Mem:           185        182          3          0          0         25
-/+ buffers/cache:        156         28
Swap:          541        486         54

```

Maybe running Compiz-Fusion, Kiba-Dock and Screenlets with 198MB RAM is not such a good idea, but it's working faster than my XP, so why should I argue? ;)
I have a Toshiba laptop with a 1,4GHz Celeron, 192MB RAM, and a 64MB ATI Radeon Xpress 200m video card.

_***Edit:***_ Reading that all you guys have from 2GB to 8GB RAM really deppresses me and my laptop... :(

---

### Post by jaybombalous on 2007-11-05
```
jasin@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1003        891        112          0        185        367
-/+ buffers/cache:        338        664
Swap:         2941          0       2941
```

I have a ton of crap open, swappiness is set to 0 so everything is loaded into memory by default and kept there if possible.

---

### Post by jaybombalous on 2007-11-05
> **santiagoward2000 said:**
> ```
             total       used       free     shared    buffers     cached
Mem:           185        182          **3**          0          0         25
-/+ buffers/cache:        156         28
Swap:          541        **486**         54

```

Maybe running Compiz-Fusion, Kiba-Dock and Screenlets with 198MB RAM is not such a good idea, but it's working faster than my XP, so why should I argue? ;)
I have a Toshiba laptop with a 1,4GHz Celeron, 192MB RAM, and a 64MB ATI Radeon Xpress 200m video card.

_***Edit:***_ Reading that all you guys have from 2GB to 8GB RAM really deppresses me and my laptop... :(

look at the ones I highlighted in **bold**. Thats how much u have left in your resource tank, in other words its empty.

---

### Post by nanbudh on 2007-11-05
Here is memory with firefox and a terminal running:
```
shavin@ubuntu7:~$ free -m
                    total       used       free     shared    buffers     cached
Mem:             468        462          6          0         28        186
-/+ buffers/cache:        247        221
Swap:           1968          0       1968

```
**********here is after starting pidgeon as well:***********************
```

             total       used       free     shared    buffers     cached
Mem:           468        463          5          0         50        150
-/+ buffers/cache:        263        205
Swap:         1968          0       1968

```**********only 1 MB difference in RAM and a change of 247 to 263 in buffers/cache***************

****************Now here is starting OO Writer as well:****************

```
             total       used       free     shared    buffers     cached
Mem:           468        463          5          0          6        156
-/+ buffers/cache:        300        168
Swap:         1968         37       1931

```***************************
Question:
 Is gutsy eating more RAM than windows XP? 
Is free RAM of 5/6 MB okay for smooth running?

---

### Post by Luke Davis on 2007-11-05
Here is mine
free -m
             total       used       free     shared    buffers     cached
Mem:          1005        995          9          0          3        206
-/+ buffers/cache:        785        220
Swap:         5898        280       5617

uptime ~10 hours firefox, email, deluge and amarok running.

Machine is AMD 3500+. 1GB ddr400

---

### Post by yellowbread on 2007-11-05
> Question:
Is gutsy eating more RAM than windows XP?
Is free RAM of 5/6 MB okay for smooth running?

As I understand it, the 5/6 mb of free memory in the first line is a good thing. it means that little of your memory is sitting idle. The free memory on the second line is how much you have left before the system will be forced to swap out. It may start swapping out before that amount gets used, depending on which value your swapiness is set to.

At the risk of hijacking the thread (my profuse apologies to the OP), what I would like to see is comparisons of memory use of the macines in similar states-- the same processes running, but before and after "work" has been done. On my machine, there is a slow but steady rise in the used (-buffers/cache) memory. Starting at 283mb after a fresh boot, in one day on use it is now up to 424mb. AT this rate it would take about 8 more days to start swapping out, and even longer to start bogging down, but I'm going to put off rebooting as long as possible to see how far the pattern continues.

---

### Post by santiagoward2000 on 2007-11-05
> **jaybombalous said:**
> look at the ones I highlighted in **bold**. Thats how much u have left in your resource tank, in other words its empty.

Yes, I know! But unless I open Firefox I have no problem...

---

### Post by califman831 on 2007-11-05
total       used       free     shared    buffers     cached
Mem:           503        497          6          0          7        207
-/+ buffers/cache:        282        220
Swap:         1466         33       1433



I need an upgrade or maybe DSLinux

---

### Post by orthopod on 2007-11-05
My computer, has been up and running for a week or two already.
  I'm running Gnome, and have Compiz in the background.

7.10 64 bit 
free -m
             total       used       free     shared    buffers     cached
Mem:          3957       2957        999          0        365       1988
-/+ buffers/cache:        603       3353
Swap:         7852          0       7851

---

### Post by jaybombalous on 2007-11-05
> **santiagoward2000 said:**
> Yes, I know! But unless I open Firefox I have no problem...


firefox is a resource hog... But u have barely any free mem space or swap space. If u are gonna run that low density memory then at least increase your swap size and set vm.swappiness accordingly. It should easy up the problems when u use firefox.

---

### Post by santiagoward2000 on 2007-11-05
> **jaybombalous said:**
> firefox is a resource hog... But u have barely any free mem space or swap space. If u are gonna run that low density memory then at least increase your swap size and set vm.swappiness accordingly. It should easy up the problems when u use firefox.

I've turned to some lighter options. I'm using Opera for browsing normally, but I'm starting to like w3m (it's so cool! :guitar: )

---

### Post by david_2001 on 2007-11-05
```
             total       used       free     shared    buffers     cached
Mem:          1003        993         10          0        146        437
-/+ buffers/cache:        408        594
Swap:         2055          0       2055
```

Arch64 with compiz-fusion, firefox, a terminal and gkrellm running.

EDIT: Now with addition of OpenOffice.org writer, kaffeine playing BBC 2, rhythmbox playing Miles Davis and a photograph opened for editing in GIMP:
```
             total       used       free     shared    buffers     cached
Mem:          1003        993          9          0         71        326
-/+ buffers/cache:        595        407
Swap:         2055          0       2055
```

---

### Post by cml21 on 2007-11-09
Here is mine:  (Dell 1505N, 2 GB RAM)

```
totalused       free     shared    buffers     cached
Mem:          2026       1944         82          0         18       1422
-/+ buffers/cache:        503       1522
Swap:         4690         20       4670
```

---

### Post by x0as on 2007-11-09
```

             total       used       free     shared    buffers     cached
Mem:           440        387         53          0          8        147
-/+ buffers/cache:        231        209
Swap:         1906        147       1758

```

Firefox, vlc & pidgin running.

---

### Post by dewey on 2007-11-09
```
aaron@MyRoom:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1005        882        123          0         64        298
-/+ buffers/cache:        518        486
Swap:         1953         45       1907

```
THat's with firefox, gnome-terminal, AWN, compiz-fusion, pidgin, and it's been running for a day or two.

---

### Post by Fir3chi3f on 2007-11-10
```
fir3chi3f@travelpain:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           877        870          6          0         10        226
-/+ buffers/cache:        633        244
Swap:         2572        199       2373

```

^its a laptop^

---

### Post by scradock on 2007-11-10
Would anyone be kind enough to explain what vm.swappiness is? And how do I set it?

Thanks

---

### Post by karvec on 2007-11-10
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2017       1534        483          0         22       1113
-/+ buffers/cache:        398       1619
Swap:         5906          0       5906

```

Oddly enough, system monitor reports only 400 mb being used...

Uptime is only 2:16, but this is a laptop.  rTorrent + Firefox running, and 1 more terminal.

*shrugs*

Seems like alot...  o_O

---

### Post by leona on 2007-11-11
Mine
```

             total       used       free     shared    buffers     cached
Mem:          1004        994          9          0         46        320
-/+ buffers/cache:        627        376
Swap:         2000         12       1988

```

---

### Post by Scott-271 on 2007-11-11
scott@funkbunk:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           122        120          2          0          0         26
-/+ buffers/cache:         93         29
Swap:          996        151        845

This is with just FF and Pidgin running. After running htop, I have anywhere from 2 to 4 or 5 /usr/lib/firefox/firefox-bin taking around 29% mem each, and throw in xorg hovering around 13%.
Just installed Xubuntu 7.10.

Scott

---

### Post by mozetti on 2007-11-29
```
             total       used       free     shared    buffers     cached
Mem:          3043       1213       1829          0        163        594
-/+ buffers/cache:        454       2588
Swap:         1027          0       1027

```

---

### Post by saru411 on 2007-11-29
```
saru@LAIN:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2011        361       1650          0         10        162
-/+ buffers/cache:        188       1823
Swap:         5725          0       5725

```

this is after a fresh reboot

---

### Post by bazzbc on 2007-11-29
[HTML]:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3963       3006        957          0        149        984
-/+ buffers/cache:       1871       2091
Swap:         2047          0       2047
[/HTML]

Running  Firefox, Swiftdove, Banshee, Deluge, Skype and XP with 1Gb allocated in Virtualbox.

---

### Post by Brindled on 2007-11-29
6 days up time (no reboot):


```
             total       used       free     shared    buffers     cached
Mem:          1519       1417        101          0         59        330
-/+ buffers/cache:       1027        492
Swap:         5757       2367       3390

```

maybe someone could explain exactly what we're looking for. i haven't a clue. :confused:

---

### Post by eisle89 on 2007-12-14
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3960        974       2985          0         85        489
-/+ buffers/cache:        399       3561
Swap:         1027          0       1027

---

### Post by SafirXP on 2007-12-14
```
             total       used       free     shared    buffers     cached
Mem:          2015        492       1522          0          9        249
-/+ buffers/cache:        234       1780
Swap:          235          0        235

```

---

### Post by ian dobson on 2007-12-14
free -m
             total       used       free     shared    buffers     cached
Mem:          3956       1402       2553          0        341        374
-/+ buffers/cache:        687       3268
Swap:         2941          0       2941

My main server. Q6600, 4Gb ram, 4x500Gb in RAID 5 array.

Running Apache2,Xmail email server,Munin,SMTP folding.

Stability good.

Regards
Ian Dobson

---

### Post by JoseReyes on 2008-03-26
free -m
             total       used       free     shared    buffers     cached
Mem:          2014       1165        849          0         42        642
-/+ buffers/cache:        479       1534
Swap:         5898          0       5898

---

### Post by martin saint martin on 2008-03-26
martin@martin-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1887        809       1078          0         65        433
-/+ buffers/cache:        310       1577
Swap:         5530          0       5530

athlon 64 X2 4600+  gskill 2-gig(1gigx2) ddr2 800 gigabyte ga-ma69gm-s2h amd 690g chipset
i'm using the onboard ATI radeon graphics

---

### Post by CyrusTR on 2008-03-26
from guild.the-reincarnation.com .. been running 3 days since i re-configured stuff ... 

runs Apache 2.2 / Mod_Perl2 with MySQL 5.0

```
top - 01:26:32 up 3 days,  8:23,  1 user,  load average: 0.59, 0.59, 0.55
```

```
             total       used       free     shared    buffers     cached
Mem:          3931       1721       2209          0        173        713
-/+ buffers/cache:        834       3097
Swap:         2055          0       2055

```

---

### Post by jhnphm on 2008-03-27
From my desktop, currently doing nothing useful except having firefox32 and opera32 open, running Hardy:
```
             total       used       free     shared    buffers     cached
Mem:          3941       3828        113          0         83        805
-/+ buffers/cache:       2939       1002
Swap:         2499       2267        232

```
Apparently Acrobat Reader is leaking memory and went up to 1.7 gigs @_@. After killing it, 
```
             total       used       free     shared    buffers     cached
Mem:          3941       2122       1819          0         83        811
-/+ buffers/cache:       1227       2714
Swap:         2499         67       2432

```
No idea why 1 entire gigabyte is still in use, but eh, 3/4ths of the memory is still free, so whatever.

---

### Post by lime4x4 on 2008-03-27
john@john-hardy:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3948       3919         29          0         79       2274
-/+ buffers/cache:       1564       2383
Swap:        10464         42      10421

---

### Post by GTengineer on 2008-03-28
my results

>              total       used       free     shared    buffers     cached
Mem:          7999        729       7269          0        124        420
-/+ buffers/cache:        184       7814
Swap:            0          0          0


---

### Post by stefangr1 on 2008-03-28
I really envy those with 8GiB RAM!

             total       used       free     shared    buffers     cached
Mem:          2026       1971         55          0          7       1596
-/+ buffers/cache:        368       1658
Swap:          996        219        776


I see that some have a lot of swap space, like >8GiB, does anyone know if that's really useful?

---

### Post by GTengineer on 2008-03-31
> **stefangr1 said:**
> I really envy those with 8GiB RAM!

             total       used       free     shared    buffers     cached
Mem:          2026       1971         55          0          7       1596
-/+ buffers/cache:        368       1658
Swap:          996        219        776


I see that some have a lot of swap space, like >8GiB, does anyone know if that's really useful?

Stefan to be honest for normal desktop use, I don't see much sense for more than 4GB especially with Linux in general. I need 8GB because I do some memory heavy number crunching and even then it is a bit of overkill. Now if there was an easy way to load my entire OS into RAM then we would be talking :D

---

