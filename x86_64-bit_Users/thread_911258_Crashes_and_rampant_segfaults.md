---
title: "Crashes and rampant segfaults"
date: 2008-09-05
forum: x86 64-bit Users
---

### Post by placement80 on 2008-09-05
This is my system:

Asus P5E-V HDMI
Intel Core 2, 3.0GHz (E8400, Wolfdale)
8GB DDR2 (4 x Crucial Ballistix Tracer PC-6400 2GB)
Cooler Master Realpower 850W PSU
320GB Hitachi Deskstar (root, home, swap)
750GB Hitachi Deskstar
Ubuntu 8.04 64-bit (Hardy Heron)

I assembled the system about two weeks ago. My system seems to work fine when I first boot up, but after running for 12-24 hours, some programs freeze or quit unexpectedly. I've been running Opera in a console, and it seems to switch between quitting with a segmentation fault and quitting with a bus error. After a program has quit, it will usually refuse to start again, segfaulting at launch. Also, the errors seem to be "contagious," i.e., after one program has quit, other programs will start doing the same. Earlier today, Firefox, Konqueror, Opera, Pan, and Evolution all refused to launch (they would segfault as soon as I tried to start them). A reboot has fixed it, at least for a few hours.

It seems to be the same programs that segfault every time, so I'm thinking maybe it's something in some common library. I've yet to experience a segfault in XMMS, for example.

I've also experienced several system-wide lock ups. The system has gone to black twice (once while watching a movie in Xine, and once while clicking a link in Firefox), the screen has frozen completely six times (four times while using a browser, and twice while transferring a file from a DVD-R), and one time the system appeared to freeze, but I could still move my mouse about (just not click on anything), the clock continued to update, and the title marquee on XMMS continued to move. That last one happened when I tried to extract a RAR archive. I've had the system monitor open for several of the freezes, and for most of them, nothing out of the ordinary appeared to be happening, but for the one where the system froze, but I could still move (but not use) my mouse, cpu1 shot up to 100% just a few seconds before the freeze, while cpu2 remained at 2%.

One thing I've noticed is that both the unexpected quits and the system lock ups tend to occur when I'm inputting. E.g., when I move my mouse or when a browser is reacting to a shortcut. Also, most of the errors seem to occur when I'm using a browser.

---

### Post by Thelasko on 2008-09-05
Did you run a memtest?

---

### Post by placement80 on 2008-09-06
I left Memtest86+ running overnight. This is what was on the screen when I got up:

```
Memtest86+ v2.01
Inten Core 2 3006 MHz
L1 Cache:   64K 21018 MB/s
L2 Cache: 6144K 13358 MB/s
Memory  : 8183M  4197 MB/s
Chipset :

WallTime 13:31:50
Cache    8183M
RsvdMem  572K
MemMap   e820-Std
Cache    on
ECC      off
Test     Std
Pass     10
Errors   7936
ECC Errs 0

Tst Pass Failing Address          Good      Bad       Err-Bits  Count  Chan
6   1    001cff838f4 -  7423.1MB  00001000  00021000  00020000  7912
6   1    001cff13a5c -  7423.1MB  00000040  00100040  00100000  7913
6   1    001cff83854 -  7423.1MB  00000080  00040080  00040000  7922
6   1    001cff13a5c -  7423.1MB  00000200  00100200  00100000  7923
6   1    001cff838f4 -  7423.1MB  00080000  000a0000  00020000  7928
6   1    001cff13a5c -  7423.1MB  00004000  00104000  00100000  7929
6   1    001cff83854 -  7423.1MB  00008000  00048000  00040000  7933
6   1    001cff13a5c -  7423.1MB  00020000  00120000  00100000  7934
7   1    001cf8ef9e4 -  7416.9MB  bfb35140  bfb15140  00020000  7941
3   2    00028dfa354 -   653.6MB  80808080  80808084  00000004  7942
```

I don't know what these results mean, but you just know the four-digit figure in front of *Errors* can't be good.

---

### Post by Yellow Pasque on 2008-09-06
You have a bad memory stick (unless you have the memory timings/voltage misconfigured).

---

### Post by placement80 on 2008-09-06
Thanks, I'll have to test each of the sticks then.

Could something like this be caused by a pooly mounted motherboard? When I was putting the system together, I couldn't get the motherboard to power on, but after a little messing around with it, I found that I had tightened the screws too much, so I had to loosen them a little.

---

### Post by Lerxst on 2008-09-12
Hmmm, I have the same problem, and I have even replaced all memory sticks!
On my system, it seems that Evolution is somehow causing memory corruption.
I've had several hard lockups and this night it happened again.
Shortly before, Evolution crashes:
Sep 11 23:49:25 superunknown -- MARK --
Sep 12 00:00:00 superunknown kernel: [1403486.305711] evolution-excha[7100]: segfault at 7fd91c95d648 rip 7fd93293abf0 rsp 7fff3bdd2078 error 4
Sep 12 00:29:25 superunknown -- MARK --
Sep 12 00:49:25 superunknown -- MARK --
Sep 12 01:09:25 superunknown -- MARK --
Sep 12 01:29:25 superunknown -- MARK --
Sep 12 01:49:25 superunknown -- MARK --
Sep 12 02:09:25 superunknown -- MARK --
Sep 12 02:29:25 superunknown -- MARK --
Sep 12 08:09:13 superunknown syslogd 1.5.0#1ubuntu1: restart.
Sep 12 08:09:13 superunknown kernel: Inspecting /boot/System.map-2.6.24-21-generic
Sep 12 08:09:14 superunknown kernel: Loaded 28506 symbols from /boot/System.map-2.6.24-21-generic.
Sep 12 08:09:14 superunknown kernel: Symbols match kernel version 2.6.24.

Notice that it's alive for some hours then it dies with nothing.
When I reboot, it always segfaults during boot. This morning I did a memtest and it got literally thousands of memory errors right away.
When I **coldboot**, it's completely fine and memtest runs with no errors.

I am perfectly aware of that I can have either received new, faulty mem sticks or a faulty motherboard, but this doesn't seem like **the** culprit to me.
What I believe happens is that evolution completely corrupts the memory, the PC goes down hard, and a soft reset doesn't clear the corrupted memory, that's why I need a cold boot to get it up and running again.

Before I replaced the memory sticks I had the same problem, evolution, opera, firefox - you name it, would segfault all the time untill a reboot took place.

Also notice that evolution segfaults at 00:00:00 - an odd time. Even though there's no cronjobs or anything that starts at that time...

---

