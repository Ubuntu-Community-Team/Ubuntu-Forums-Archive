---
title: "Centrino Duo and 8.04 64bit"
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by Nico0020 on 2008-04-24
In an attempt to finally switch over to 64bit I put in the live AMD 64 CD.  When I try to check the disk, install, or just go to the live part of the CD it tells me I need a different kernel as it only sees i686.  I have a Intel Centrino Duo.  Anyone have any idea why?

---

### Post by renim on 2008-04-24
Centrino Duo is the name for the platform, not the cpu. If the CD is giving you that message then you have a Core Duo based on the Yonah core which only capable of supporting 32bit software. In order to run 64bit software you'll need atleast a Core 2 Duo or newer processor which are capable of supporting both 32/64bit software.

If you still have Windows installed on the system, then check under system properties menu or you can use a utility like CPU-Z([http://www.cpuid.com/cpuz.php](http://www.cpuid.com/cpuz.php) which will let you know some of the basic information on the cpu/motherboard etc..

---

### Post by Nico0020 on 2008-04-25
Here is the information I obtained from the program.  So I can't ever use the 64bit version of Ubuntu?  So what exactly is the purpose of me having two seperate 32 bit CPUS's if I cannot run a 64bit Operating system.  

> Processors Information
------------------------------------------------------------------------------------

Processor 1 (ID = 0)
Number of cores		2 (max 2)
Number of threads	2 (max 2)
Name			Intel Core Duo T2300E
Codename		Yonah
Specification		Genuine Intel(R) CPU           T2300  @ 1.66GHz
Package			Socket 479 mPGA (platform ID = 5h)
CPUID			6.E.8
Extended CPUID		6.E
Core Stepping		C0
Technology		65 nm
Core Speed		1664.6 MHz (10.0 x 166.5 MHz)
Rated Bus speed		665.8 MHz
Stock frequency		1666 MHz
Instructions sets	MMX, SSE, SSE2, SSE3
L1 Data cache		2 x 32 KBytes, 8-way set associative, 64-byte line size
L1 Instruction cache	2 x 32 KBytes, 8-way set associative, 64-byte line size
L2 cache		2048 KBytes, 8-way set associative, 64-byte line size
FID/VID Control		yes
FID range		6.0x - 10.0x
max VID			1.263 V
Features		XD


---

### Post by Nico0020 on 2008-04-25
Here is the information I obtained from the program.  So I can't ever use the 64bit version of Ubuntu?  So what exactly is the purpose of me having two seperate 32 bit CPUS's if I cannot run a 64bit Operating system.  

> Processors Information
------------------------------------------------------------------------------------

Processor 1 (ID = 0)
Number of cores		2 (max 2)
Number of threads	2 (max 2)
Name			Intel Core Duo T2300E
Codename		Yonah
Specification		Genuine Intel(R) CPU           T2300  @ 1.66GHz
Package			Socket 479 mPGA (platform ID = 5h)
CPUID			6.E.8
Extended CPUID		6.E
Core Stepping		C0
Technology		65 nm
Core Speed		1664.6 MHz (10.0 x 166.5 MHz)
Rated Bus speed		665.8 MHz
Stock frequency		1666 MHz
Instructions sets	MMX, SSE, SSE2, SSE3
L1 Data cache		2 x 32 KBytes, 8-way set associative, 64-byte line size
L1 Instruction cache	2 x 32 KBytes, 8-way set associative, 64-byte line size
L2 cache		2048 KBytes, 8-way set associative, 64-byte line size
FID/VID Control		yes
FID range		6.0x - 10.0x
max VID			1.263 V
Features		XD


---

### Post by jespdj on 2008-04-25
> **Nico0020 said:**
> Here is the information I obtained from the program.  So I can't ever use the 64bit version of Ubuntu?  So what exactly is the purpose of me having two seperate 32 bit CPUS's if I cannot run a 64bit Operating system.
Your processor is an Intel Core Duo (not Core 2 Duo), which does not support 64-bit mode. So no, there is no way you can ever run 64-bit Ubuntu on that processor.

The Core Duo is a 32-bit dual-core processor. Note that the fact that it's dual-core does not have anything to do with 32-bit or 64-bit. It's not "2 x 32 = 64 bit".

---

### Post by Nico0020 on 2008-04-25
thanks for teh info.  So what is the purpose of having a dual core CPU then?

---

### Post by Patsoe on 2008-04-25
Very briefly: a dual core can do two tasks at the same time. A 64bit core can eat numbers that are twice as long (in bits) as those a 32bit core can handle.

---

### Post by Joeb454 on 2008-04-25
I'm not sure whether Centrino Duo's are 64 bit capable. I do know that the Celeron D in my Desktop supports Intel's 64 bit system, though I've yet to try installing a 64 bit OS on it :)

---

