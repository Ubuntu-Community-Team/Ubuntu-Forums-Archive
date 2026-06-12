---
title: "Incorrect RAM info?"
date: 2008-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by ToySouljah on 2008-03-25
Hello, I was poking around in my system and ran free -k and got the following output:

```
             total       used       free     shared    buffers     cached
Mem:       4047012    3827504     219508          0     165500    3286764
-/+ buffers/cache:     375240    3671772
Swap:     11855928     173020   11682908

```

I looked in the System Monitor to see if my RAM was being Bogarted by some rogue app/process and everything seems fine.  User Memory is hovering around 370MB out of 3.9GB and my Swap is 
169MB out of 11.3GB.  So I was wondering why it shows that I have almost all my RAM used up in the terminal and it shows to be within normal ranges in the System Monitor.  

Thanks in advance...it's not a serious problem...more of a general question since the system doesn't seem to be slowed down at all.  In a couple of months I will hit my first year of being Windows free (except at work) and it has been a learning experience, but a fun one most of the time.  Minor headaches the first couple of months, but I did a hard switch by completely formatting my drive and putting Ubuntu on it since I wanted to force myself to learn it and not have the temptation to go back to Windows...lol. These forums have been a life saver on more than one occasion  =D>

---

### Post by insane_alien on 2008-03-25
most of it is cache, this is normal. unused RAM is wasted RAM so your system will cache applications and such. 

also, do you have a need for 11GB of swap? i've never used more than 1 myself.

---

### Post by ToySouljah on 2008-03-25
> **insane_alien said:**
> most of it is cache, this is normal. unused RAM is wasted RAM so your system will cache applications and such. 

also, do you have a need for 11GB of swap? i've never used more than 1 myself.

lol...sorry...not sure how to lower swap.  All of that was setup by the auto install in Ubuntu (use entire disc thing).  I'll look to see how to lower it.  Oh the cache would be the reason that like the first time after a reboot an app will take a little longer to load, but afterwards the special effects can't even keep up with the app reopening so fast?  Makes sense now that I think about it :-k  Thanks for the point in the right direction  :)

---

### Post by insane_alien on 2008-03-25
ah, you'd need to repartition the drive. if you are uncomfortable with that bit, which i'm assuming you are since you never done it origionally, and have plenty of space then leave it for now, it won't damage your system.

---

