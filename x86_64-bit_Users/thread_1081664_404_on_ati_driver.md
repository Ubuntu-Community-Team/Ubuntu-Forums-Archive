---
title: "404 on ati driver?"
date: 2009-02-26
forum: x86 64-bit Users
---

### Post by Reeman on 2009-02-26
I tried the ati 9.2 driver a few days ago ..it installed something accepted the aticonfig --intial -f then pouch my system to the point where dpkg-reconfigure would not even work. Now I go back with a different kernel to download the same new ati driver and presto no linux download. Any gnews on wtf is going on. I hope they decided to pull it because it definately can cause headaches. Better a 404 than a piece of crapware!

---

### Post by michael37 on 2009-02-28
> **Reeman said:**
> I tried the ati 9.2 driver a few days ago ..it installed something accepted the aticonfig --intial -f then pouch my system to the point where dpkg-reconfigure would not even work. Now I go back with a different kernel to download the same new ati driver and presto no linux download. Any gnews on wtf is going on. I hope they decided to pull it because it definately can cause headaches. Better a 404 than a piece of crapware!

I have had more problems with binary ATI drivers than 

I'd recommend to use the supplied Ubuntu kernel and the packaged "restricted driver".  If it works at all, just use it. 

What card are you using and why are trying to break your system with potentially broken drivers?

---

### Post by Reeman on 2009-03-01
> **michael37 said:**
> I have had more problems with binary ATI drivers than 

I'd recommend to use the supplied Ubuntu kernel and the packaged "restricted driver".  If it works at all, just use it. 

What card are you using and why are trying to break your system with potentially broken drivers?
I have it working with the Ubuntu supplied ones now. It seems that the ati 9.2 breaks on an integrated Radeon X1250. Installs a module then just does not work. Samething with BlueWhite 64 ( a slackware based distro ). I am trying to get a realtime audio setup working but cannot get the any realtime kernel to work with the ATI drivers. The Ubuntu supplied does not work either with a realtime kernel.

I have to use the Xorg vesa driver to get a compiled realtime kernel working at all.
Anyone else having the same trouble?

---

