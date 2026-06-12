---
title: "beid-tool and beidgui segfault on x86_64"
date: 2008-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by peterdm on 2008-02-08
I want to start using my Belgian eID card with some apps.
So I installed SmartCard reader & drivers, as well as eid applications.
pscpd daemon running, the ACR38U reader is up and running.
When I insert the eId card, all still goes well, until I want to access the card.
Both beid-tool and beidgui segfault.

Note that I encountered the same problem once entered with OpenSUSE 10.2 in July (I switched to Ubuntu a couple of months ago). It was fixed in an unofficial package.

In case it's any help, here is the bug I originally entered in July:

[http://devzilla.novell.com/eID-belgium/show_bug.cgi?id=2](http://devzilla.novell.com/eID-belgium/show_bug.cgi?id=2)

Peter

---

### Post by peterdm on 2008-02-08
/var/log/messages contains

Feb  8 20:26:11 cheetah kernel: [ 1729.933056] beid-tool[6856]: segfault at ffffffffaaae7e50 rip ffffffffaaae7e50 rsp 00007fff6c8aee88 error 14
Feb  8 20:26:28 cheetah kernel: [ 1747.228863] beidgui[6863]: segfault at ffffffffb2530e50 rip ffffffffb2530e50 rsp 00007fff03baa0f8 error 14

---

