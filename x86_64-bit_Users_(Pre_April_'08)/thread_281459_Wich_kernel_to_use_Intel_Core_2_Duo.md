---
title: "Wich kernel to use Intel Core 2 Duo?"
date: 2006-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bunro on 2006-10-21
I just bot a new laptop Asus F3JA series with an Intel Core 2 Duo (2 Ghz) processor.
 I installed Ubuntu 6.10 RC Desktop AMD64 version with LAMP.
 

 My question is how can I activate the 2 Cores, how can I check if they are working and are there any monitoring tools?
 

 The command uname -m gave me the following results: x86-64.
 

 Best Regards, Robert

---

### Post by Gillen on 2006-10-21
I have a Pentium D, I used the 686smp kernel to get dual core support in Dapper.

sudo apt-get install linux-686-smp

Hope this helps.

---

### Post by nyinge on 2006-10-21
Yep, Gillen's way.  Make sure about the "smp" for duel cores.  KsysGuard is one of many tools to check about it on KDE, but I forgot the name of the similar program on Gnome.

I think the following command should show you some info about your cpu:
```

cat /proc/cpuinfo

```

---

### Post by Bunro on 2006-10-21
Thanks Gillen for your replay.

But the command  sudo apt-get install linux-686-smp is not working?
Hopefully you can help me with the correct commands here.

Regards, Robert

---

### Post by louistan3 on 2006-10-21
i believe the generic kernel that comes with ubuntu 6.10 supports smp out of the box.. no need to install any other kernel.. :D

---

### Post by Bunro on 2006-10-21
Thanks for the replay!

How can I check if both cores are working?

Regards, Robert

---

### Post by Gillen on 2006-10-21
Bunro,

Menu /System /Administration /System Monitor - 
Resoures should show CPU1 and CPU2.

Yes understand there have been some changes to the Kernel in 6.10, the release notes do not say anything but a search on google indicates Louistan3 is corrrect.

Just out of interest the command for installing the 686smp Kernel in Dapper does nothing after you press enter it waits for you to put in your password.

Anyway this beats XP hands down, Ubuntu / Linux a top class OS.

Regards.

---

### Post by kuja on 2006-10-21
> **Bunro said:**
> Thanks Gillen for your replay.

But the command  sudo apt-get install linux-686-smp is not working?
Hopefully you can help me with the correct commands here.

Regards, Robert
Of course the linux-686-smp kernel wouldn't exist. You're running the 64-bit version, not the 32-bit version. If you're using Ubuntu 6.06, the linux-amd64-xeon or linux-amd64-generic kernels are your best bets. If you're using Edgy, there is only one kernel, a perfectly fine generic.

---

### Post by agentstewie on 2006-10-22
> **kuja said:**
> Of course the linux-686-smp kernel wouldn't exist. You're running the 64-bit version, not the 32-bit version. If you're using Ubuntu 6.06, the linux-amd64-xeon or linux-amd64-generic kernels are your best bets. If you're using Edgy, there is only one kernel, a perfectly fine generic.

i think that the linux-amd64-xeon would be your best bet. Reading the description of the xeon one, it seems that it targets all _Intel_ 64 bits.
im going to try it now.

---

### Post by Bunro on 2006-10-23
Thanks everybody for there information!! Relay great.

With Gillen info. I can see the two CPU's

Menu /System /Administration /System Monitor - 
Resources should show CPU1 and CPU2.

Thanks a gain :D

Best Regards, Robert

---

### Post by DonKyot on 2006-10-30
sorry to but in on your thread..

... i've also got a core 2 duo (Dell Dimension 9200)
I've installed the 2.6.17-10.33 kernal (not the whole of Edgy; because when I did, it wouldn't boot, so it's on top of the Dapper distribution; but this way, the network works).

I can only see 1 CPU; although the cpuinfo file says speed etc. is correct.
Something I'm missing?

cheers

---

### Post by Bunro on 2006-10-30
DonKyot

After the checks that are mentioned in this tread  
 Menu /System /Administration /System Monitor
 and cat /proc/cpuinfo.
 I sow that my system is running out of the box on two cpu's.
 I think the best to do is make a fresh installation 6.10 in that case you have a clean and clear system.
 

 Hopefully it si helping.
 

 Regards, Robert

---

### Post by DonKyot on 2006-10-30
> **Bunro said:**
> DonKyot

After the checks that are mentioned in this tread  
 Menu /System /Administration /System Monitor
 and cat /proc/cpuinfo.
 I sow that my system is running out of the box on two cpu's.
 I think the best to do is make a fresh installation 6.10 in that case you have a clean and clear system.
 

 Hopefully it si helping.
 

 Regards, Robert
Thanks; 
I'd like to; but the 6.10 bootCD doesn't see my wireless kb/mouse (when 6.06 did; but didn't see the network) & when I installed the whole thing off the Other CD, in command line - it wouldn't boot at all! :-?

Maybe I'll just wait till 6.10 has a few more updates...

---

### Post by DonKyot on 2006-10-31
woohoo - I can see both CPUs now.
I updated; system-monitor & powernowd.
Maybe the old monitor just couldn't see the 2nd CPU?

---

### Post by rocktorrentz on 2006-10-31
I am running Edgy with a Core 2 Duo and can confirm that it sees both cores with a normal install.

---

### Post by swistakers on 2006-11-03
On the other hand I can confirm that Dapper failed to detect Core Duo as 2 CPUs. That didn't change after update to Edgy and I had to install SMP kernel manually. Now everything is fine.

---

### Post by midorigin on 2006-12-04
I'm not very familiar with what different processor architectures mean. Does a Core 2 Duo require a 64-bit kernel to make use of its EM64T capabilities?

---

### Post by kuja on 2006-12-04
midorigin, yes, it does.

---

### Post by midorigin on 2006-12-04
> **kuja said:**
> midorigin, yes, it does.
Which one? Should I just reinstall using the desktop-amd64 cd, or is there a way to upgrade without reinstalling everything?

---

### Post by kuja on 2006-12-04
Yes, you'll need to do a full reinstall, there's no way of upgrading.

---

