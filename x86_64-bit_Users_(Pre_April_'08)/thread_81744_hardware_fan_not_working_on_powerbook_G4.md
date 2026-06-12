---
title: "hardware fan not working on powerbook G4"
date: 2005-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by tr333 on 2005-10-25
anyone know how to get the internal fan to work on a powerbook G4?

---

### Post by craks on 2005-10-25
apt-get install powernowd

---

### Post by emax on 2005-10-25
[QUOTE=tr333]anyone know how to get the internal fan to work on a powerbook G4?[/QUOTE]

Mine doesn't seem to be working properly today either... (it has before).

I have powernowd installed and running:

euan@rmac:~$ ps -ef | grep power
root      4926     1  0 11:42 ?        00:00:00 /usr/sbin/powernowd -q
euan@rmac:~$

euan@rmac:~$ dmesg | grep fan
[   40.071502] adt746x: Thermostat bus: 1, address: 0x2e, limit_adjust: 0, fan_speed: -1
[   40.128535] adt746x: Setting speed to 0 for CPU TOPSIDE fan.
[   40.129579] adt746x: Setting speed to 0 for GPU ON DIE fan.
[   42.486472] adt746x: setting fans speed to 64 (limit exceeded by 1 on CPU TOPSIDE)
[   42.486482] adt746x: Setting speed to 64 for CPU TOPSIDE fan.
[   42.487544] adt746x: Setting speed to 64 for GPU ON DIE fan.
[  124.655857] adt746x: Stopping fans.
[  124.655870] adt746x: Setting speed to 0 for CPU TOPSIDE fan.
[  124.656907] adt746x: Setting speed to 0 for GPU ON DIE fan.
euan@rmac:~$

Machine is very hot to the touch, especially to the left of the trackpad.  If I boot into OS X, the fan goes mad for the first few mins until the machine cools down.  Can the temps that the fans kick in at be adjusted?

I'm tempted to avoid using ubuntu until I can get this resolved in case I fry my machine!!!

For info, this is a clean install of 5.10 (about 10 days old)...

---

### Post by hobbestec on 2005-12-23
I found a message on the debian mailing list that said you can edit the file: /sys/devices/temperatures/limit_adjust - in there I put a "-2" number and the fan came on.  This lowers the threshhold for the fan to turn itself on.

---

### Post by lorne_kun on 2005-12-26
[QUOTE=hobbestec]I found a message on the debian mailing list that said you can edit the file: /sys/devices/temperatures/limit_adjust - in there I put a "-2" number and the fan came on.  This lowers the threshhold for the fan to turn itself on.[/QUOTE]


So how do i go about editing it? I can only open it as read only...

---

### Post by urza on 2006-01-03
sudo vi /sys/devices/temperatures/limit_adjust

---

### Post by jlgoolsbee on 2006-02-08
I tried that (*sudo vi /sys/devices/temperatures/limit_adjust*) and I got an "E667 fsync failed" error from vi when I tried to save - multiple times, and no amount of sudo or "w!" will do it.  help?

---

### Post by fungi on 2006-02-09
Im running Drapper and am getting same the same real hot, no fan thing on my powerbook 12".

There is no "temperatures" directory in /sys/devices/

Also no sound and battery dies real quick, but wi-fi works a treat :)

---

### Post by ssam on 2006-02-09
if you are having problems with vi i suggest you try

```
gnome-sudo gedit /sys/devices/temperatures/limit_adjust
```

that lets you use the gnome text editor

---

### Post by jlgoolsbee on 2006-02-09
[QUOTE=ssam]if you are having problems with vi i suggest you try

```
gnome-sudo gedit /sys/devices/temperatures/limit_adjust
```

that lets you use the gnome text editor[/QUOTE]

I did that, and got this error:

(gedit:4067): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Ugh.

---

### Post by ssam on 2006-02-10
thats odd. maybe

```
sudo gedit /sys/devices/temperatures/limit_adjust
```

if not then nano is a simpler editor command line than vi. try

```
sudo nano /sys/devices/temperatures/limit_adjust
```

---

### Post by jlgoolsbee on 2006-02-11
that did it.

though i still found the errors i had with all the other text editors very strange...

****EDIT:** i spoke too soon.  nano let me change the value (from 0 to -2) without any vocal system error, and even looking at the file from other editors from that point forward showed the change, but as soon as i rebooted the machine, it was reset to 0.

i'm really worried about running ubuntu on my PB if it's not going to be cooling itself the way it needs to be.

---

### Post by tr333 on 2006-02-17
[QUOTE=jlgoolsbee]that did it.

though i still found the errors i had with all the other text editors very strange...

****EDIT:** i spoke too soon.  nano let me change the value (from 0 to -2) without any vocal system error, and even looking at the file from other editors from that point forward showed the change, but as soon as i rebooted the machine, it was reset to 0.

i'm really worried about running ubuntu on my PB if it's not going to be cooling itself the way it needs to be.[/QUOTE]
i have had the same problems with the number reverting back to "0" after a reboot.

---

### Post by tr333 on 2006-02-17
is this value read once on startup, or can it be set during logon?

EDIT:    i just changed the value to -10 and the fan suddenly roared into action :D

---

### Post by tr333 on 2006-02-17
there is a solution to your problem in [http://www.ubuntuforums.org/showthread.php?t=132164]("http://www.ubuntuforums.org/showthread.php?t=132164")

hope that solves your problem.  (it worked for me).

---

### Post by gatiba on 2006-07-01
[QUOTE=fungi]Im running Drapper and am getting same the same real hot, no fan thing on my powerbook 12".

There is no "temperatures" directory in /sys/devices/

Also no sound and battery dies real quick, but wi-fi works a treat :)[/QUOTE]

I have a G4 iBook and i have the same hot problem and NO "temperatures" in /sys/devices (on Dapper). Have you found a solution?
How can i activate the fan before my laptop goes to hell?! :D

---

### Post by gatiba on 2006-07-01
Ok just found the solution: the correct fan's module was not used by default in Dapper.
After adding **therm_adt746x** in **/etc/modules**, it started working just right :D :D

---

