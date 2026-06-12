---
title: "SECURITY UPDATE: honor expired and revoked key signatures?"
date: 2009-04-22
forum: x86 64-bit Users
---

### Post by bart1452 on 2009-04-22
I just got the Apt update for April 21, 2009 and it wants to honor expired and revoked key signatures. Why would I want to accept an update like that?

* SECURITY UPDATE: honor expired and revoked key signatures
    - adjust methods/gpgv.cc to mark a signature as valid only if GOODSIG
      is set by gpgv
    - CVE-XXXX-XXXX
    - Patch from Michael Vogt
  * SECURITY UPDATE: ensure automatic updates are not permanently disabled
    in certain situations when the timezone's DST starts at midnight
    - adjust debian/apt.cron.daily to check the return code of date
    - CVE-XXXX-XXXX

---

### Post by hansdown on 2009-04-22
Hi bart1452.

Have you disabled your automatic updates?

---

### Post by bart1452 on 2009-04-23
Yes, the update manager requires that I accept the updates before they are applied. I went ahead with applying two 686 kernel updates sent to my 386 system with some question and decided to become more choosey after that. I think I might need to try to roll back the 686 kernel updates somehow. But especially the idea of honoring revoked key signatures sounds wrong. I don't know the reasons for revoking key signatures but it doesn't sound good.

---

### Post by hansdown on 2009-04-23
I wish I had something more helpful than this.

[https://launchpad.net/ubuntu/+source/apt](https://launchpad.net/ubuntu/+source/apt)

I believe it is safe. Michael Vogt has been around for some time.

[http://www.google.ca/search?q=Patch+from+Michael+Vogt&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=Patch+from+Michael+Vogt&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by bart1452 on 2009-04-23
OK, thanks. I had no idea who Micheal Vogt is. I am learning to not simply accept without question every update that's offered. Even a Microsoft Technician once advised me against taking everything that MS offered in it's updates for Windows.

It doesn't appear the community has a problem with that update.

---

