---
title: "I have a problem with my amd turion 64"
date: 2005-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by lcharly on 2005-07-27
i have a laptop compaq presario v2312US

Amd turion 64
512 ram
60 Gb HD
ATI radeon xpress 200m 128mb
DVD-RW

I install ubuntu 64 and when login its freezy but i fixed it with change the xorg.conf and put the option no accell

and when i start a session its works fine but the proccesor its always used the 50 % and there is not process with that use and the computer is too slow what can i do??please help

---

### Post by DancingSun on 2005-07-27
You mean the System Monitor will say 50% of the cpu is being used, but the detailed process list does not have a total of 50% of the cpu time being used?

---

### Post by lcharly on 2005-07-28
yes that's my problem can you help me?

---

### Post by DancingSun on 2005-07-29
Unfortunately, this is beyond me, as I haven't encounter this kind of weirdness before.  The system monitor has been accurate for me so far, although the graph on the GNOME panel seems to be updated slower than the detailed list of processes.

If the cpu is constantly in use, then something must be running actively in the background.  Check and see if you have consistent HDD accesses when you don't do anything on the computer.

Could you post a screen shot of the System Monitor showing now process is using any cpu time while the cpu usage is 50%?  I'm thinking it might be some setting you have that's hiding some processes.  I remember that you can show only your processes or show processes for all users.

---

### Post by lcharly on 2005-07-29
15544 lcharly   15   0  127m  18m 8804 S  5.9  4.9   0:10.17 gnome-terminal
12624 root      16   0  191m  50m 8164 R  5.3 13.7 127:47.95 Xorg
12739 lcharly   15   0 12084 4120  524 S  1.3  1.1   2:46.42 esd
12905 lcharly   15   0  106m 9364 5324 S  1.3  2.5   3:07.82 xmms
19288 lcharly   15   0  224m  39m  21m S  1.0 10.8   0:09.38 epiphany
19391 lcharly   16   0  9448 1272  944 R  0.3  0.3   0:00.10 top
    1 root      16   0  2632  552  484 S  0.0  0.1   0:00.30 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.03 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.28 events/0
    4 root      11  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    5 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.93 kacpid
   95 root      10  -5     0    0    0 S  0.0  0.0   0:01.00 kblockd/0
   98 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
  128 root      15   0     0    0    0 S  0.0  0.0   0:00.07 pdflush
  129 root      15   0     0    0    0 S  0.0  0.0   0:00.21 pdflush
  131 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  130 root      15   0     0    0    0 S  0.0  0.0   0:01.07 kswapd0
  716 root      15   0     0    0    0 S  0.0  0.0   0:00.14 kseriod
 1015 root      15   0     0    0    0 S  0.0  0.0   0:00.68 kjournald
 1040 root      11  -5  2608  408  320 S  0.0  0.1   0:00.05 udevd
 2194 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 3025 root      15   0     0    0    0 S  0.0  0.0   0:01.05 kjournald
 4305 root      21   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 4371 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0
 4562 root      10  -5  4528 1044  580 S  0.0  0.3   0:00.00 dhclient3
 4925 root      16   0  2628  424  340 S  0.0  0.1   0:00.02 dd
 4927 klog      16   0  3940 1020  488 S  0.0  0.3   0:00.14 klogd
 5437 root      15   0  2884  992  576 S  0.0  0.3   0:00.38 acpid
 5448 messageb  16   0  8388 1096  908 S  0.0  0.3   0:00.08 dbus-daemon-1
 5460 hal       17   0 21056 3808 1608 S  0.0  1.0   0:21.74 hald
 5473 root      20   0  2620  460  396 S  0.0  0.1   0:00.00 inetd


i can see any process using 50 %

---

### Post by DancingSun on 2005-07-29
I'm pretty new to Linux, so I have to ask , is that a terminal output?  If so, what command is used and which column is used to indicate cpu usage?

The System Monitor that I was referring to is the one under the GNOME menu Applications --> System Tools --> System Monitor.  That one seems to work for me.

---

### Post by tseliot on 2005-07-30
Here's the SOLUTION.

Try my HOWTO:

[http://www.ubuntuforums.org/showthread.php?p=278589#post278589](http://www.ubuntuforums.org/showthread.php?p=278589#post278589)

---

### Post by UrbanFallout on 2005-08-02
Thought I'd add a quick 2 cents worth here for the beginning bit, in case you weren't sure how to change your repositories:

Do a:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo gedit /etc/apt/sources.list

you'll see a long list similar to this:

[SIZE=1]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) [COLOR=Red]hoary[/COLOR] main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) [COLOR=Red]hoary[/COLOR] main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[COLOR=Green]#[/COLOR] deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) [COLOR=Red]hoary[/COLOR] universe 
[COLOR=Green]#[/COLOR] deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) [COLOR=Red]hoary[/COLOR] universe
[COLOR=Blue]
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy multiverse
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy multiverse[/COLOR]

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

[COLOR=Green]#[/COLOR] deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
[COLOR=Green]#[/COLOR] deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
[/SIZE]

Change every [COLOR=Red]red[/COLOR] highlighted "hoary" to "breezy" using a search replace save, and uncomment the [COLOR=Green]green[/COLOR] highlighted #'s. Lastly, add the [COLOR=Blue]blue[/COLOR] highlighted multiverse lines if they're not already there.

Now run synaptic package manager and do an update. 
Next do a search for "linux-image" and install "linux-image-2.6.12-5-amd64-k8" from the list.

main universe and multiverse respectively indicate groups of packages with decreasing amounts of support from the ubuntu team.
breezy is simply the next version of ubuntu, which is not currently deemed stable. The kernel image is fine though!

Don't forget to put hoary back you're done.

Hope this helps
Nick

---

### Post by DancingSun on 2005-08-02
Nick....please fix the font size! It's waaay too big!

---

