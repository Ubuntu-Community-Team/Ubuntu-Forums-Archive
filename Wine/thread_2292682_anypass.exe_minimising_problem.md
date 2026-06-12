---
title: "anypass.exe minimising problem"
date: 2015-08-30
forum: Wine
---

### Post by Robbyx on 2015-08-30
I have used this windows program  in ubuntu for at least 5 years. I recently changed to AMD 64. Anypass usually when minimised to the dock, does not re-open. It has a right click option to open but in that state it does not work. 

I think the problem comes after another ubuntu program is loaded or used. Usually Anypass wil expand and minise with no problem until another program is used and anypass  is in the  minimised state..

My system is Ubuntu 14.04. Wine version: 1:1.7.50-0ubuntu1; q4wine 1.1-r2-1
I am using the AMD grahpics accelerator from fglrx-updates (proprietary)
Do you need any logs to be submitted?

---

### Post by Robbyx on 2015-08-30
I also have what is described as a serious problem the first time I start anypass. I usually ignore it and it causes no further problems but I would like not to have the program error messages and wonder if it is connected with the failure to re-open after minimising to the dock. It only happens the first time I open anypass. If I close it and restart the program the error does not appear. This is the begining of the fault report:

> Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:0034fe0c EBP:0034fe60 EFLAGS:00010216(  R- --  I   -A-P- )
 EAX:0034fe3c EBX:7b8b5000 ECX:00240000 EDX:7ba59e70
 ESI:7ffdf000 EDI:00000000

---

### Post by Robbyx on 2015-09-02
Would someone please give me the benefit of their experience to solve my problem, because I am finding it very hard to have the password manager remain useful when it locks down and will not open. This is a new problem, seen only since the upgrade to UbuntuGnome 14.04 AMD 64.

I have just changed the wine emulator to win 2008 and it seems to be much better. It will probably give the error on startup but at the moment it is expanding up from minimise ok.

---

