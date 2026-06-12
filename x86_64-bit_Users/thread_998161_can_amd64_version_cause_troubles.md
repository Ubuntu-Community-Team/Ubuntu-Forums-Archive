---
title: "can amd64 version cause troubles ?"
date: 2008-11-30
forum: x86 64-bit Users
---

### Post by aboud on 2008-11-30
i had ubuntu 8.04 32bit on my Sony/2d cpu1.5/2GB , and it worked pretty good with all compiz, but when i switched yesterday to 8.10 64 things got worse. 
often heavy cub rotation, 2 times the system logged out.

i installed few new packges, and updated the system. 
memory never went over 1200 MB, swap under 20 mb. 
cpu usage is fine.

do you thing i should switch to 8.10 32, or 8.04 64? 
in other word is the problem in 8.10 or 64 based ?

---

### Post by cariboo on 2008-11-30
You probably have some sort of misconfiguration. I would check to make sure the video drivers are installed correctly.

Jim

---

### Post by Bataille23 on 2008-12-01
Personally, I'm very loathe to upgrade unless I'm having truly serious issues with my current configuration.  I'm fine with Hardy right now, and haven't had any trouble beyond the inevitable killing of my wireless connection.  :x  I gave Intrepid a chance, and was pretty disappointed.  That, however, is probably just due to the fact that it's new and there are going to be plenty of bugs for a while.

That's a matter of taste, however.  I'm just not very adventurous in that aspect.  As far as 64-bit editions causing problems; well, you can do most everything in 64-bit that you could in 32-bit, but oftentimes you have to find a workaround -- like chroot, for example.  That would give you a virtual 32-bit environment (just google it).  It's very handy for running apps that are 32-bit only.

But all things considered, I'd go with the 32-bit if you can.  The 64-bit edition doesn't add all that much (it might be a little faster, but not enough to make up for its limitations), and it subtracts a lot.  Plus, it's infinitely more difficult to get your wireless connection up and running with a 64-bit edition.  :(

---

### Post by cariboo on 2008-12-01
I've been running 64bit versions for the last 4 releases, and it keeps getting better all the time. Adobe just released a 64bit Flash plugin (linux only so far). The only problem I have is that once in a while I see a rpogram I would like to try, and it's only available as a 32bit program, but that's not Ubuntu's fault, it is the fault of the author still living in the stone age. :)

Jim

---

### Post by Yellow Pasque on 2008-12-01
> The 64-bit edition doesn't add all that much (it might be a little faster, but not enough to make up for its limitations)
And what "limitations" would those be?

> It's infinitely more difficult to get your wireless connection up and running with a 64-bit edition.
I (and several others) haven't had any problem. Some hardware may require ndiswrapper, which can be problematic if the manufacturer doesn't have Windows XP-64 drivers. Other than that, there shouldn't be any difference between setting up wireless on a 32-bit and 64-bit system.

---

### Post by Arup on 2008-12-01
Its about overall stability and using a x32 OS on a x64 CPU is a waste of resources IMHO. Another irony is that Linux provides far more x64 software than Windows currently and so its a shame not to harness their power. Encoding etc. is a breeze on a dual quad core, x32 cant' come close to that, also if you have more than 4GB, you have no choice but to run x64.

---

### Post by aboud on 2008-12-02
> **Bataille23 said:**
> Personally, I'm very loathe to upgrade unless I'm having truly serious issues with my current configuration.  I'm fine with Hardy right now, and haven't had any trouble beyond the inevitable killing of my wireless connection.  :x  I gave Intrepid a chance, and was pretty disappointed.  That, however, is probably just due to the fact that it's new and there are going to be plenty of bugs for a while.

That's a matter of taste, however.  I'm just not very adventurous in that aspect.  As far as 64-bit editions causing problems; well, you can do most everything in 64-bit that you could in 32-bit, but oftentimes you have to find a workaround -- like chroot, for example.  That would give you a virtual 32-bit environment (just google it).  It's very handy for running apps that are 32-bit only.

But all things considered, I'd go with the 32-bit if you can.  The 64-bit edition doesn't add all that much (it might be a little faster, but not enough to make up for its limitations), and it subtracts a lot.  Plus, it's infinitely more difficult to get your wireless connection up and running with a 64-bit edition.  :(

what is your hardware ? i had such problem with my wireless, and i solved on my vaio.

---

### Post by aboud on 2008-12-02
> **Bataille23 said:**
> Personally, I'm very loathe to upgrade unless I'm having truly serious issues with my current configuration.  I'm fine with Hardy right now, and haven't had any trouble beyond the inevitable killing of my wireless connection.  :x  I gave Intrepid a chance, and was pretty disappointed.  That, however, is probably just due to the fact that it's new and there are going to be plenty of bugs for a while.

That's a matter of taste, however.  I'm just not very adventurous in that aspect.  As far as 64-bit editions causing problems; well, you can do most everything in 64-bit that you could in 32-bit, but oftentimes you have to find a workaround -- like chroot, for example.  That would give you a virtual 32-bit environment (just google it).  It's very handy for running apps that are 32-bit only.

But all things considered, I'd go with the 32-bit if you can.  The 64-bit edition doesn't add all that much (it might be a little faster, but not enough to make up for its limitations), and it subtracts a lot.  Plus, it's infinitely more difficult to get your wireless connection up and running with a 64-bit edition.  :(


i had such problem and i think it's working little better, now, i wrote simple script that check connection every minute, and reconnect if the line drop down. i think it need a little modification to work on wireless connection, i can posted if needed.

---

