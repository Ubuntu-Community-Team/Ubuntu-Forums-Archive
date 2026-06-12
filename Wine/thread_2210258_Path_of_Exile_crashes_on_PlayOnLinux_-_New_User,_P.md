---
title: "Path of Exile crashes on PlayOnLinux - New User, Please Help!"
date: 2014-03-09
forum: Wine
---

### Post by jwkparker on 2014-03-09
Hi,
I'm brand new to Ubuntu and using Linux in general. I made the switch 2 days ago. 
I'm trying to play Path of Exile on PlayOnLinux. I am using the version downloaded through PlayOnLinux, and my Ubuntu is v13.10.

I can boot up PoE, but after 5-10 minutes, it crashes. Here is the script error I get:

Unhandled exception: page fault on write access to 0xf632ce24 in 32-bit code (0xf67c4c47).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:f67c4c47 ESP:0032eb70 EBP:7c834098 EFLAGS:00210282(  R- --  I S - - - )
 EAX:f632ce10 EBX:f67fd000 ECX:f75e9454 EDX:7c8cbd28
 ESI:c381fffe EDI:e3a32310
Stack dump:
0x0032eb70:  00000000 e39e7c40 e3a32310 f67fd000
0x0032eb80:  7c811218 f67fd000 7c8248d8 f67b7bf9
0x0032eb90:  7c8cbd28 00000e40 e3a32310 e3a324f0
0x0032eba0:  0032ec38 0032ebe8 0032ebc8 7c810ee8
0x0032ebb0:  00000e40 00840458 000ffd00 e3a324f0
0x0032ebc0:  7c8a68cc 00000001 f67b73b9 f67fd000
Backtrace:
=>0 0xf67c4c47 nouveau_heap_free+0x27() in nouveau_dri.so (0x7c834098)

I'm not a computer wiz by any means, so please bear with me and my questions if you choose to help me (which I really hope you do).

Thank you thank you thank you,
JamesPath

---

### Post by jwkparker on 2014-03-09
Recorded another crash, here is the script:

exception: page fault on read access to 0x00000005 in 32-bit code (0xf685ec44).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:f685ec44 ESP:0032eb70 EBP:7d897030 EFLAGS:00210202(  R- --  I   - - - )
 EAX:00000001 EBX:f6897000 ECX:f7652450 EDX:d735b508
 ESI:d735eb60 EDI:d6ef3bf8
Stack dump:
0x0032eb70:  00000000 00000001 d6ef3bf8 f6897000
0x0032eb80:  7d8965f0 f6897000 d735eb60 f6851bf9
0x0032eb90:  d735b508 00000cc0 d6ef3bf8 d6ef3dd8
0x0032eba0:  00000000 d6dd6a3a 00000007 7d8962c0
0x0032ebb0:  00000cc0 00000007 000ffd00 d6ef3dd8
0x0032ebc0:  7d918acc 00000001 f68513b9 f6897000
Backtrace:
=>0 0xf685ec44 nouveau_heap_free+0x24() in nouveau_dri.so (0x7d897030)

---

### Post by jwkparker on 2014-03-10
bump. Please help

---

### Post by Mark Phelps on 2014-03-10
The linked page from the WineHQ website shows Path to have lots of  bugs:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=25078]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=25078")

---

