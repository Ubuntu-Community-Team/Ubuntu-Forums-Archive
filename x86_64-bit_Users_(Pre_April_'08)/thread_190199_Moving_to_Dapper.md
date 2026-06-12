---
title: "Moving to Dapper"
date: 2006-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by aruckert on 2006-06-06
Hi!

I've been quite happily running Breezy for AMD64 for some time now and I was wondering if it is worth it to risk upgradeing to Dapper.

As far as I could read, Dapper has mostly Server improvements and I'm running Brezzy on my laptop.

So, can anyone tell me if there are many issues solved for AMD64 users in Dapper? What will I gain if I take the risk to push the Upgrade button?

Thanks in advance.

---

### Post by Flyn on 2006-06-06
First of all, I'm pretty sure you can run the normal x86 version of Dapper instead of the AMD64.
Second. Dapper is lightyears ahead of Breezy, in terms of speed, hardware support and general product quality.
I heartily reccomend that you upgrade or even better, reinstall completely.

---

### Post by aruckert on 2006-06-06
Thanks for your comments Flyn. You are right I could run the x86 version but I chose to use AMD64 as a way to promote the use of the platform. If nobody uses it, then operating systems will never support 64 bits.

On the other hand, I spent tons of time configuring my Ubuntu box and what I'm afraid of is that an unsuccessful upgrade would live it useless. With this in mind, a complete reinstall is not a posibility, either.

So, has anyone tried an AMD64 upgrade from Breezy to Dapper?

Thanks for your help... :)

---

### Post by glenn45 on 2006-06-06
[QUOTE=aruckert]Thanks for your comments Flyn. You are right I could run the x86 version but I chose to use AMD64 as a way to promote the use of the platform. If nobody uses it, then operating systems will never support 64 bits.

Amen to that!:D 

Also, im doing some fortran programming using the intel emt64 compiler in my 64 bit ubuntu breezy and its going swell....so i guess dapper is not yet worth the hassle.

---

### Post by aruckert on 2006-06-18
I'm gald to see that least some people feel the same way about 64bit platforms :)

There's an issue in AMD64 Breezy that, if it has been resolved in AMD64 Dapper, would make the risk of upgrading worthwhile: it's not possible to copy and paste from another application to Open Office. It's possible from Open Office to other applications, though.

It has been discussed here:
[http://ubuntuforums.org/showthread.php?t=94837](http://ubuntuforums.org/showthread.php?t=94837)

Does anyone know if this has been resolved in Dapper?

---

### Post by aruckert on 2006-09-19
Ok, I finally did it. I updated from AMD64 Breezy to AMD64 Dapper. This was my experience in case it is usefull to anyone else:

- Having a broad band connection and using the update tool the update was automatic and paniless. In a few hours I had AMD64 Dapper up and running.

- The issue I mentiond y the previuos posts ([http://ubuntuforums.org/showthread.php?t=94837](http://ubuntuforums.org/showthread.php?t=94837)) is solved.

- I had my Broadcom WiFi card working with ndiswrapper. It stopped working and I haven't been able to fix it yet.

- My touchpad configuration changed making it very difficult to use. As I'm writting I'm installing qsynaptics to see if can improve the configuration.

- At the end of every package installation from Synaptic I get the message: 
E: samba: subprocess post-installation script returned error exit status 102
I haven't been able to figure out what that means yet. I'm not really sure if Samba is working properly.

I haven't had any other problems yet. So, for a complete OS Upgrade I guess  it's not bad.

I'll try to keep posting as I solve this problems in case it is usefull to anyone else.

---

