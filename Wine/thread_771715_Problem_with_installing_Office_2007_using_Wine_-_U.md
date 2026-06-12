---
title: "Problem with installing Office 2007 using Wine - Unhandled exception..!!"
date: 2008-04-27
forum: Wine
---

### Post by rtandon87 on 2008-04-27
Hi, 

I am using Ubuntu 8.04 and have Wine 0.9.60 installed.
I am trying to follow the instructions here to install Office 2007.
[http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/](http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/)

All goes well until I reach step 11 and type wine setup.exe

Here is what happens:

rajat@rajat-tablet:~$ wine /media/cdrom0/setup.exe
wine: Call from 0x7b844440 to unimplemented function mssip32.dll.CryptSIPGetSignedDataMsg, aborting
wine: Unimplemented function mssip32.dll.CryptSIPGetSignedDataMsg called at address 0x7b844440 (thread 0026), starting debugger...
WineDbg starting on pid 0025
Unhandled exception: unimplemented function mssip32.dll.CryptSIPGetSignedDataMsg called in 32-bit code (0x7b8444b6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b8444b6 ESP:0032f220 EBP:0032f284 EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82eac9 EBX:7b8b2888 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:00130d10
Stack dump:
0x0032f220:  0032f2ac 00000008 7bc33ce1 7bc90724
0x0032f230:  80000100 00000001 00000000 7b844440
0x0032f240:  00000002 7e200910 7e200962 00130d70
0x0032f250:  00130dc0 00110000 7bc88444 00130d08
0x0032f260:  00000050 0032f284 7bc4262e 00110000
0x0032f270:  00030000 00130d70 7bc33ce1 00130d08
Backtrace:
=>1 0x7b8444b6 in kernel32 (+0x244b6) (0x0032f284)
  2 0x7e2008b5 in mssip32 (+0x108b5) (0x0032f2b4)
  3 0x7e2005b0 in mssip32 (+0x105b0) (0x0032f304)
  4 0x7e8b09a8 SoftpubLoadMessage+0x428() in wintrust (0x0032f394)
  5 0x7e8b2448 in wintrust (+0x12448) (0x0032f3f4)
  6 0x7e8b2564 in wintrust (+0x12564) (0x0032f444)
  7 0x7e8b28b9 WinVerifyTrust+0x289() in wintrust (0x0032f4e4)
  8 0x3000c404 in setup (+0xc404) (0x0032f558)
  9 0x3000c2b7 in setup (+0xc2b7) (0x0032f568)
  10 0x300133a9 in setup (+0x133a9) (0x0032fd88)
  11 0x3000ca05 in setup (+0xca05) (0x0032fe70)
  12 0x3000f650 in setup (+0xf650) (0x0032ff08)
  13 0x7b875cc7 in kernel32 (+0x55cc7) (0x0032ffe8)
  14 0xb7e169f7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7b8444b6: movl	0xfffffffc(%ebp),%ebx
Wine-dbg>


PLEASE HELP.  I have got Office 2007 to work using these instructions on another machine before.  But, I don't know what's going on here.  I just started using LINUX 1 week ago and so, I am very new to everything.

PLEASE HELP.

---

### Post by Kinst on 2008-04-28
That's weird. Does it work if you set your version to Windows XP instead of Vista?

---

### Post by rtandon87 on 2008-04-28
I have tried to even switch to Windows XP.  Same thing happens.

---

### Post by hardyn on 2008-04-28
Version difference?

It looks like it is either calling an MS .dll, or an older wine .dll verions that does not yet have a function implimented.  Check your version numbers.

---

### Post by rtandon87 on 2008-04-28
rajat@rajat-tablet:~$ wine --version
wine-0.9.60

I had wine-0.9.59 earlier and I removed it using Synaptic Package Manager and installed 0.9.60.
Could that have been a problem?  How can I fix it?

PLEASE HELP.  I really want to get office 2007 working.

---

### Post by Ghost88 on 2008-04-28
Bump

I'm having the exact same issue in Ubuntu 8.04. The only difference is that I have a clean install of Wine version 0.9.59 rather than 0.9.60

---

