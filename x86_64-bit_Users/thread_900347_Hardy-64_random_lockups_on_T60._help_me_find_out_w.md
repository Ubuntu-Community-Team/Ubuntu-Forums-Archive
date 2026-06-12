---
title: "Hardy-64 random lockups on T60. help me find out why"
date: 2008-08-25
forum: x86 64-bit Users
---

### Post by xSauronx on 2008-08-25
Running Ubuntu Hardy 64-bit on a T60. I get random lockups. not in X, but the whole system freezes entirely. The only guess I have is that maybe its the fglrx drivers for the ati card? should I just try 32-bit? id rather not re-install :(

to be clear: when i say the system locks, i mean it. i cant get alternate terminals, cant restart X, cant even soft restart with ctrl+alt+delete. 

specs:

C2d 2ghz, 3gb ram, 100gb hd, intel 3945 wifi, ati x1400

problem: random lockups. var/log/syslog doesnt help much:
> Aug 25 05:17:02 pergamum /USR/SBIN/CRON[5158]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 25 05:37:27 pergamum -- MARK --
Aug 25 05:57:27 pergamum -- MARK --
Aug 25 07:26:01 pergamum syslogd 1.5.0#1ubuntu1: restart.

thats it. every time theres a hard lock and i reboot, thats where the data stops, then starts again as i boot back up. nothing before that shows any problem signs or anything interesting as far as i can tell.  

where else can i look to narrow down the problem? 

thanks

---

### Post by elmoosecapitan on 2008-08-25
I ran into a similar situation with my T61, see if this sounds at all familiar: [http://ubuntuforums.org/showthread.php?t=859471](http://ubuntuforums.org/showthread.php?t=859471)

If it does, get 'sensors-applet 2.2.1' for the panel and be sure to display cpu[0], cpu[1], HDD, fan, and graphics card temperatures.

If you see a spike at the of failure, you might have some clue. Also, a flashing scroll/caps lock light indicated hardware issue.


cheers

---

### Post by xSauronx on 2008-08-25
> **elmoosecapitan said:**
> I ran into a similar situation with my T61, see if this sounds at all familiar: [http://ubuntuforums.org/showthread.php?t=859471](http://ubuntuforums.org/showthread.php?t=859471)

If it does, get 'sensors-applet 2.2.1' for the panel and be sure to display cpu[0], cpu[1], HDD, fan, and graphics card temperatures.

If you see a spike at the of failure, you might have some clue. Also, a flashing scroll/caps lock light indicated hardware issue.


cheers

that doesnt mimic what im experiencing. i get random crashes 2-3 times a day (or sometimes when i leave my laptop on overnight). at first i thought it was video related but it has since happened without any sort of serious video use going on. 

the suggestion for trying a live cd from that thread is a good idea, though, and may help me narrow things down somewhat. i have 2 or 3 around here so ill try that tonight and see how it acts. 

also, i have no flashing lights when it dies. the screen freezes and the system locks completely. 

anyone else have any ideas?

---

