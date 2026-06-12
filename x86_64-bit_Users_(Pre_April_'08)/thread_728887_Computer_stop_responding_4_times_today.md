---
title: "Computer stop responding 4 times today"
date: 2008-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by wangrui on 2008-03-19
Hi

It never happens before. But today two computers stop responding while I'm using them.

One computer has 2GB memory and running ubuntu AMD64 with a lot of applications. It stop responding three times today while I'm using eclipse. Every hardware has stop responding so I have to power off the computer and start again.

I thought it's hardware problem at first. But it happened again on another computer which has 8GB memory. And I'm only running eclipse with a simple java application. When the java application run up to 5.1GB memory, the whole system stop responding. 

It never happened before. I do remember there is an important security update today. Not sure which one is causing the problem. Does anyone has the same problem today? Does anyone know how to find out the reason if such thing happens?

Thanks

---

### Post by sowelie on 2008-03-19
Holy mackeral, 5.1GB of memory?  Are you sure it's not your program that is causing the system to hang?  I would start there.

---

### Post by wangrui on 2008-03-19
> **sowelie said:**
> Holy mackeral, 5.1GB of memory?  Are you sure it's not your program that is causing the system to hang?  I would start there.

No, it's just a very simple program. I have some data need to be transformed inside memory.  But I'm not sure whether the memory can hold all data so I'm watching it all the time. When 20% data is processed, the JVM already used up to 4GB memory. So I realized it's impossible and just about the kill the process and do some split work. Then I found the screen is already freezed and mouse keyboard is not responding. The program is very simple, but there are a lot of data.

But this is not the point. The other computer I'm using is not running any memory consuming program at all. It only has 2GB memory but stop responding three times today. Because this never happened before. So I highly suspect the newly installed update. The interesting thing is, my second computer is running on a flash plus memory. So I lost all hard disk changes after the crash. Now the same update has poped up again:

Version 1.6.dfsg.1-7ubuntu0.1: 

  * SECURITY UPDATE: arbitrary code execution via freed pointer and memory
    overflows.
  * src/kdc/{kerberos_v4,dispatch,network}.c: upstream fixes patched inline
    (MITKRB5-SA-2008-001: CVE-2008-0062, CVE-2008-0063).
  * src/lib/rpc/{svc,svc_tcp}.c: upstream fixed patched inline
    (MITKRB5-SA-2008-002: CVE-2008-0947)

But I don't dare to install it this time. It seems it's the only thing I installed on both computer today.

---

### Post by wangrui on 2008-03-19
> **sowelie said:**
> Holy mackeral, 5.1GB of memory?  Are you sure it's not your program that is causing the system to hang?  I would start there.

A second thought, maybe it is caused by the memory. Because the memory value I saw is print out by the program and it's a value return by JVM. The actually memory used by JVM is always much higher than it. Maybe the JVM already used up to 7G memory when the system freeze.  But it's still weired. I start the java program with the parameter -Xmx7200m, if JVM can't reserve 7200m memory, it shouldn't even started. And even there is memory leak. The whole system shouldn't freeze.

I thought Linux will never freeze. It's the first day I saw it. And for so many times.

---

### Post by wangrui on 2008-03-19
There is another thing I want to mention about crash.

My root partition is on a 4GB USB flash disk. I didn't use SSD because USB is much cheaper. There are 6 pairs of USB port on the motherboard. I found one thing after a lot of system failures. If I plug another USB disk into the same pair of USB port which the root partition USB disk is in. Then the whole system will crash. I can't lauch any application, and can't login. I can still use keyboard and mouse. But any command will return an IO error.

This is not a serious problem. But kind hope it's fixed in Ubuntu 8

---

