---
title: "Harddisk activity on 7.10 server"
date: 2007-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ubimad on 2007-11-06
installed 64bit 7.10 server edition and now the harddisk is active continuosly, very anoying....
there is no Tracker installed, has anyone a idea.

---

### Post by netbandit on 2007-11-06
Are you doing software RAID?  If you created a RAID1 (mirror) the disks will run continuously until both drives are in sync.  Reboots may restart this process, so let it finish.

To check the status of a RAID:
```
cat /proc/mdstat
```

-nb

---

### Post by Ubimad on 2007-11-06
yes there is raid1 but it had not that much activity on dapper as it has now with gusty.

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda5[0] sdb5[1]
      3004032 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      77409088 blocks [2/2] [UU]
      
unused devices: <none>
the server runs since a couple of days, but still this constant harddisk activity

also the websites running on that server, take longer to build up then before with 6.06

---

### Post by netbandit on 2007-11-06
OK,

I noticed something similar as well, but wasn't sure what it was.

I installed gkrellm and see little spikes of activity every few seconds... is this what you see as well?

-nb

---

### Post by Ubimad on 2007-11-06
yes also on my gkrellm the harddisk peaks out regularly

---

### Post by netbandit on 2007-11-06
Mine don't actually peak, but they show about 30%.

Odd.. I hasn't bothered me enough to do anything about it, but I don't remember 7.04 doing this either.

I'm not sure how to prioritize this one for now... its kindof on the back burner.
-nb

---

### Post by Ubimad on 2007-11-06
I agree with that BB :)
only read about this if on desktop machine, tracker is installed, but here nothing like that is runing.
guess have to downgrade to 7.04 or just forget about all ubuntu and switch the server as well to arch linux, it's a great distro, clean an simple, but one has to have some faith in his linux skills to run arch.
not for newbies:guitar:
so far so good, europe has midnight i will poke in in a couple hours again.

thanks

---

