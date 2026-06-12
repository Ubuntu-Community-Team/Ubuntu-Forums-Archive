---
title: "Help! Ubuntu 64 bit 9.04 keeps messing up my PC's system clock!"
date: 2009-07-23
forum: x86 64-bit Users
---

### Post by bhanja_Trinanjan on 2009-07-23
Hello,
	Ubuntu just keeps on messing the time on my PC. The login screen shows a different time from what I see after log-on on the GNOME desktop. This is becoming an annoyance as the system clock is being set wrongly on random occasions. Interestingly, the time is correct once I see the GNOME desktop. However, the system clock is wrong and remains so when I boot to Vista. Time zone is set correctly.

---

### Post by philcamlin on 2009-07-23
1 timezone is incorrect but you say it isnt

2 cmos battery is dying ? 

is your windows and ubuntu on different clocks?

---

### Post by tuxxy on 2009-07-23
Did you select UTC at installation by any chance? Try and edit the file /etc/default/rcS and change the line reading UTC=yes or UTC= to UTC=no. Reboot and adjust the time.

---

### Post by NightwishFan on 2009-07-23
I believe the issue is with the time format, I think it is called UTC? Windows uses some kind of localtime. I believe the only option is to set ubuntu to not use UTC. I will look up how.

Make Linux use 'Local' time

To make your Ubuntu system read the hardware clock as 'local'

   1. edit /etc/default/rcS
   2. add or change the following section

      # Set UTC=yes if your system clock is set to UTC (GMT)
      UTC=no

Edit - Already answered

---

### Post by bhanja_Trinanjan on 2009-07-23
> **philcamlin said:**
> 1 timezone is incorrect but you say it isnt

2 cmos battery is dying ? 

is your windows and ubuntu on different clocks?

No, CMOS battery ok, issue started after installing Ubuntu.

Timezone in both Vista and Ubuntu set to GMT + 5.5 (IST)

> **tuxxy said:**
> Did you select UTC at installation by any chance? Try and edit the file /etc/default/rcS and change the line reading UTC=yes or UTC= to UTC=no. Reboot and adjust the time.

What's this UTC and what problem does it cause?

---

### Post by tuxxy on 2009-07-23
> What's this UTC and what problem does it cause?

[http://en.wikipedia.org/wiki/Coordinated_Universal_Time](http://en.wikipedia.org/wiki/Coordinated_Universal_Time)

---

### Post by grege on 2009-07-23
Both systems being on the correct time zone means nothing if Ubuntu thinks the hardware clock is set to UTC and Vista thinks it is set to local.

See above to reset Ubuntu to use local time from the hardware so both OSs are using the same data.

---

