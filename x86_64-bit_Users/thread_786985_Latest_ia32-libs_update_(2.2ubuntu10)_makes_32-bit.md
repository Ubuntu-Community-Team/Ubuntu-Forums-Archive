---
title: "Latest ia32-libs update (2.2ubuntu10) makes 32-bit Java unable to resolve hosts"
date: 2008-05-08
forum: x86 64-bit Users
---

### Post by navtej on 2008-05-08
Long story short, because of what appears to be a bug in Sun's 64-bit JDK (NPEs inside ArrayList, among other things :confused:), I'm forced to use the 32-bit JDK. After the update manager updated ia32-libs from 2.2ubuntu9 to 2.2ubuntu10, the 32-bit JVM can no longer resolve hostnames unless I explicitly put the into the hosts file. I was able to find the old version in my apt cache and downgrade and while that fixed the problem, I'm wondering what's going on. Is this a bug in ia32-libs that I should file?

Also, is anyone else experiencing problems with the 64-bit JDK that don't occur with the 32-bit one?

---

### Post by navtej on 2008-05-09
I fixed this by installing lib32nss-mdns which was apparently removed by default:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/220377](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/220377)

---

### Post by leifj on 2008-05-12
I had the problem with firefox 32bit, which I need for various reasons, and I couldn´t make it resolve. Your hint made the trick, thanks a lot. :KS

  Any idea why this isn´t loaded by default anymore ? Anyone ?

 Leif

---

### Post by gsmanners on 2008-05-12
It looks like the devs prefer the "Recommends" option.

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/218097](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/218097)

---

