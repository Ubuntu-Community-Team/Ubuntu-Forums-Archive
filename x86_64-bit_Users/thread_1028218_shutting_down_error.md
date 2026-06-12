---
title: "shutting down error"
date: 2009-01-02
forum: x86 64-bit Users
---

### Post by theemperor on 2009-01-02
Hi,

Ubuntu 7.10 on Intel 64 Bit, Mb Intel DP35DP

Shuting doen doesn't get completed. It shows "System is shuting down please wait..." in red colour.It doesn't proceed from there. 

However once it proceeded and stuck as follows.

================================================== ==
stoping gnome display manager [OK]
Stoping Avahi in DNS/DNS-SD Daemon avahi-daemon [OK]
stoping DHCP D-Bus daemon dhcpbd [OK]
stoping consolekit daemon console-kit-daemon [OK]
stoping the systemclock
shutting down ALSA
================================================== ==
It didn't proceed after that.

Pls help me on this

Thanks in Advance
Bijoy

---

### Post by nemilar on 2009-01-02
If you press your capslock/numlock/etc keys, do the keyboard lights flash on/off?

---

### Post by nemilar on 2009-01-02
Other questions (kinda shooting in the dark here):

What command are you using to shutdown? 'shutdown -h now' 'poweroff' 'halt' are all acceptable answers :D

can you post the output of:

```
ls -1 /etc/rc0.d/
```

---

### Post by theemperor on 2009-01-04
Hi,

Both Numlock and Capslock light turns on/off.

Since i am not familiar with gnu/linux, i was shutting down machine from Gnome window button. Now i tried 'poweroff'.The result as follows:-
-----------------------------------------------------------
Starting Powernowd...................................[OK]
Starting Consolekit daemon Console-kit-Daemon........[OK]
Starting DHCP D-Bus daemon dhcdbd....................[OK]
Starting Bluetooth Services..........................[OK]
Starting Gnome Display Manager.......................[OK]
Starting anac(h)ronistic cron anacron................[OK]
Starting deferred execution scheduler atd............[OK]
Starting periodic command scheduler Crond............[OK]
Checking battery state...............................[OK]
Running local boot scripts (/etc/rc.local)...........[OK]
-----------------------------------------------------------
Shutting down process stops there. It doesn't proceed further.

Pls find below the result of ls -1 /etc/rc0.d
-------------------------------------------------
K01gdm
K01usplash
k16avahi-daemon
K16dhcdbd
k18Consolekit
k20apport
K25hwclock.sh
K50alsa-utils
k59mountoverflowtmp
K99laptop-mode
README
S01linux-resticted-modules-common
S15wpa-ifupdown
S20sendsigs
S30urandom
S31umountnfs.sh
S40umountfs
S60umountroot
S90halt
-------------------------------------------------------

Thanks

Bijoy

---

### Post by theemperor on 2009-01-07
Hi,

Pls help me on this

Bijoy

---

### Post by Arup on 2009-01-08
In /etc/init.d/alsa-utils put ifconfig wlan0 down at the begining of stop.

---

### Post by theemperor on 2009-01-09
Hi,

I done that. But Still the problem persist. 

Thanks 

Bijoy

---

