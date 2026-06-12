---
title: "error occur during shut down"
date: 2009-01-12
forum: x86 64-bit Users
---

### Post by theemperor on 2009-01-12
Hi 

I have been trying to rectify an error, which occur during shut down.Various ubuntu forum postings helped me to atleast state the error properly now.The error is as follows

I am using Ubuntu 7.10 on Intel 64 Bit, Motherboard Intel DP35DP

The issue is "Shuting down doesn't get completed. It shows "System is shutting down please wait..." in red colour.It doesn't proceed from there." 

However when pressed Alt+F7, following message shows.

================================================== ==
stoping gnome display manager [OK]
Stoping Avahi in DNS/DNS-SD Daemon avahi-daemon [OK]
stoping DHCP D-Bus daemon dhcpbd [OK]
stoping consolekit daemon console-kit-daemon [OK]
stoping the systemclock
shutting down ALSA
================================================== ==
It doesn't proceed after that.

When i tried 'poweroff'on terminal instead of GUI, following was the result:-
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

Also I tried adding ifconfig eth0 down in alsa-utils. There was No difference on the messages..

Pls help me on this.

Thanks in advance

Bijoy

---

### Post by briandu on 2009-01-12
Might be a dumb question,but...... why are u using 7.10 perhaps u  should move to 8.10? Much better believe me.

I run 64 bit 8.10 and magic.

Just a suggestion.

---

### Post by theemperor on 2009-01-14
Hi ,

I wish to upgrade. But i am little bit skeptical as I am not an expert in Linux. All i know is click "ok" while OS getting installed.I cannot afford an error while upgrade happens.

I will take the risk to upgrade for probably the next Ubuntu Release

Thanks

Bijoy

---

