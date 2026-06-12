---
title: "Dual Core CPU"
date: 2007-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jatox on 2007-03-31
I have recently installed Ununtu Linux 6.06 Dapper Drake. I have a dual core CPU, but for some reason when I got to SYSTEM>ADMINISTRATION>SYSTEM MONITOR and in the tab Resources it is saying i only am using one CPU, now i know that this should say CPU1 and CPU2 seeing as I have a Dual Core. Can anyone give me instructions on how to fix this, I think that my System is not recognizing my Second Core. Please help.

---

### Post by kevinsun on 2007-04-01
> **Jatox said:**
> I have recently installed Ununtu Linux 6.06 Dapper Drake. I have a dual core CPU, but for some reason when I got to SYSTEM>ADMINISTRATION>SYSTEM MONITOR and in the tab Resources it is saying i only am using one CPU, now i know that this should say CPU1 and CPU2 seeing as I have a Dual Core. Can anyone give me instructions on how to fix this, I think that my System is not recognizing my Second Core. Please help.

You only need to get the generic smp kernel from synaptic manager.  However, once you got that, some of your devices may not work, similar as me.

---

### Post by Pugwash on 2007-04-01
> **Jatox said:**
> I have recently installed Ununtu Linux 6.06 Dapper Drake. I have a dual core CPU, but for some reason when I got to SYSTEM>ADMINISTRATION>SYSTEM MONITOR and in the tab Resources it is saying i only am using one CPU, now i know that this should say CPU1 and CPU2 seeing as I have a Dual Core. Can anyone give me instructions on how to fix this, I think that my System is not recognizing my Second Core. Please help.

Hello, go to terminal and type this:

```
 sudo aptitude install linux-686-smp 
```

then reboot.

I have a core2duo and it worked fine for me.

---

### Post by Kilz on 2007-04-01
> **Pugwash said:**
> Hello, go to terminal and type this:

```
 sudo aptitude install linux-686-smp 
```

then reboot.

I have a core2duo and it worked fine for me.

The thing is, since he is in the 64bit section, its believed that he is running the 64bit version. You are suggesting to install a i686 or 32bit kernel. He wont be able to. Also unlike the 32bit kernels all 64bit kernels have smp already enabled. So there should be no need to look for a smp kernel.

---

### Post by Pugwash on 2007-04-01
> **Kilz said:**
> The thing is, since he is in the 64bit section, its believed that he is running the 64bit version. You are suggesting to install a i686 or 32bit kernel. He wont be able to. Also unlike the 32bit kernels all 64bit kernels have smp already enabled. So there should be no need to look for a smp kernel.

Ah, sorry didn't notice that. Sorry!

---

### Post by Kilz on 2007-04-01
> **Pugwash said:**
> Ah, sorry didn't notice that. Sorry!

We are all human  :)  the thought of helping is all that counts.

---

### Post by ronocdh on 2007-04-01
Kilz is such a swell character--I feel guilty for running the i386 build on my C2D! =D Kilz, any tips on how to get the Feisty live CD to launch X on my C2D 15" MBP? I just posted in the Apptel forums, just asking here, too...

I've double verified the discs and tried both i386 and 64-bit. I can't get the Feisty GUI to launch! I'm going to reboot and try it on cevesa (how dumb am I for not trying that earlier?). If there's an issue you guys know of, please mention it for me. =)

---

### Post by mikeymouse on 2007-04-01
I am running Feisty 64 bit on my dell 930 dual core as a live CD.
I have winxp and Xandros dual booting . ( not sure what that matters ) 
 Since i am running off the live cd I have made an internet connection (dialup)
 ***When i connect to download a page I notice the download is quite slow compared to when i am using an installed operating system.***
 Does anyone know if the download rate would be slower when running from a live CD?
 
Also If i installed Ubuntu 64 bit as a third operating system would it pick up my winxp and xandros in the boot loader??
 If anyone has any thoughts they would be appreciated.
 Thanks mikeymouse

---

### Post by prince_niceguy on 2007-04-02
> **mikeymouse said:**
> I am running Feisty 64 bit on my dell 930 dual core as a live CD.
I have winxp and Xandros dual booting . ( not sure what that matters ) 
 Since i am running off the live cd I have made an internet connection (dialup)
 ***When i connect to download a page I notice the download is quite slow compared to when i am using an installed operating system.***
 Does anyone know if the download rate would be slower when running from a live CD?
 
Also If i installed Ubuntu 64 bit as a third operating system would it pick up my winxp and xandros in the boot loader??
 If anyone has any thoughts they would be appreciated.
 Thanks mikeymouse

not sure of the internet connection speed but the overall speed will be definitely slower on live cd compared to a full fledged install. 

as for the boot loader, yes it will pick up.

---

