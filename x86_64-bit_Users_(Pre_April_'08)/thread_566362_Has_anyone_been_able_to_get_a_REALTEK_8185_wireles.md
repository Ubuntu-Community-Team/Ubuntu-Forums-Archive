---
title: "Has anyone been able to get a REALTEK 8185 wireless card working in 64-bit?"
date: 2007-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by KenMac on 2007-10-03
Hi all.  I am running 64-bit Feisty on a Gateway MT3423 (AMD 64x2).  It runs like a dream for the most part.  However, I have not been able to get the REALTEK 8185 wireless card working.  It seems to be straight forward to get it working in 32-bit using ndiswrapper but my attempts at wrapping a 64bit Windows driver have failed.  Has anyone had success with the 8185 in 64?

lspci:
06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

Any help would be greatly appreciated.

P.S. I was getting some help in another forum:
[http://ubuntuforums.org/showthread.php?t=555008&page=2](http://ubuntuforums.org/showthread.php?t=555008&page=2)
but this does seem to be a 64-bit issue.
Thanks!

---

### Post by rlbryan on 2007-10-05
I'd like to say I had, but I've been struggling with the same scenario for the past few days. At least you've narrowed it down to a 64-bit issue. Thanks for posting the question and hopefully someone can help.

---

### Post by slacker9876 on 2007-10-22
As I did in the 32-bit, I shut off my WEP and used the MAC Filter in my router. It worked for me. I did a clean install, not an upgrade.

---

