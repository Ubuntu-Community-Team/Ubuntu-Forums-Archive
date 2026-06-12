---
title: "memory problem"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by stockster on 2008-05-15
Using ubuntu 8.04 64 bit.

System physical memory: 2GB


there appears to be a problem with how the os handles situations where the used memory is bigger than the physical memory.

Example:

I open 5 or 6 apps, total memory used: 3 GB.   1 GB stored in swap file.

Now if I close all apps, I expect the swap usage to go down to zero, but it's doesn't.



Anyone else has this problem?

---

### Post by yomaoni on 2008-05-15
I have seen this before when I was using kmail and saving several attachments.  The memory usage would go up and fill the swap.  When the swap and ram where full then bam the whole system would freak out and lockup.  Many times when I close the app it would not clear out the memory that it was using.  So to answer your question, it is possible that it is a memory leak of somekind or something to do with how the memory is handled in the 64-bit version.

one question for you.  Does it make any differnce as to which programs you use or does it happen with any progam that you open?

---

### Post by tighem on 2008-05-15
How are checking swap usage?

It simply could be that space is being marked as "available" but not actually freed until it is needed...

---

### Post by Aurorion on 2008-05-15
I don't think it's related to the 64-bit kernel. I am currently using Edgy 32-bit; and currently (according to System Monitor) my user memory used is 387 MB (out of 1 GB) and swap space is 17.3 MB (out of 2 GB). I have seen my swap space being used even when the physical memory is not full several times. I think it's just because the OS does not bring page frames from the disc swap to the main memory until they are requested.

---

### Post by Sam Lars on 2008-05-16
When you use a lot of RAM with applications like that, it doesn't all clear out when you close the applications.  It keeps some of the information cached.  Also, some programs such as Xorg or Firefox use more and more RAM as they are running.
I agree that there is a problem if you fill up all of your RAM and swap.  If you wait a while (maybe 5 or 10 minutes, depends on what you're doing and how fast your hard drive is), it will close out the application(s) that are using the most memory.
Rather than wait, it's usually better to just hard reboot, or add more swap.

---

### Post by Yellow Pasque on 2008-05-16
```
free -m
```

---

### Post by slowtrain on 2008-10-28
Just saw this.  One thing that seems to help on my system is running the following two commands to clear the swap and then turn it back on:


sudo swapoff -a -v
sudo swapon -a -e -v


Have heard, though, that these can bring some people's computers down.  Seems fine on mine.

---

