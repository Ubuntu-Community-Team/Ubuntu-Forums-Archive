---
title: "Ethernet Not Starting at Boot"
date: 2006-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by shawnhcorey on 2006-04-03
I have a PowerBook G4 with Ubuntu installed as the only OS. When I boot, eth0 does not start and I can't find any error message in the logs. I can start it manually via `System -> Administration -> Networking`.

Also, I have to start `pon dsl-provider` by hand. This is not too bad but everytime I put my laptop to sleep, it takes many retries to get PPP and ethernet working again.

Can anyone get me suggestions on how to fix this or point to some documentation?

Thanks,
shc

---

### Post by calum on 2006-04-03
Have a look at /etc/networking/interfaces... you might be missing the line "auto eth0" in there, and possibly some other stuff too (haven't looked at it for a while to remember exactly what you need).  Try "man interfaces" for more info too.

---

### Post by shawnhcorey on 2006-04-03
Thanks, I think. At least I have something to investigate but do you know of any other `/etc/network/interfaces` file I can compare it to? It appears that mine is out of order, that is, the ordering of the commands is not correct but I'm not sure. I don't have any idea what would be the correct order. Does anyone know a web site that might have this information?

shc

---

### Post by shawnhcorey on 2006-04-06
Well, after much poking around in my system and some heavy thinking, it seems that my problem is that the loopback network is not started. I know that my ethernet network does not start at boot and I have to start it manually. So, now I have to fix the both of them. This could take several days (or weeks). I will post any followup on my wiki page [https://wiki.ubuntu.com/Shawnhcorey/ApacheAdventure](https://wiki.ubuntu.com/Shawnhcorey/ApacheAdventure)

shc

---

