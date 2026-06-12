---
title: "computer works, but unstable when 2G+2G+1G+1G installed"
date: 2009-09-21
forum: x86 64-bit Users
---

### Post by aapo4 on 2009-09-21
I bought more memory and switched from 32bit to 64bit ubuntu. (I have dualboot now.)
64 bit ubuntu detects my 2G+2G+1G+1G and it almost works. I can use it many hours without problems, but sometimes it freezes (no messages. Keyboard/mouse doesn't work, it doesn't respond ping anymore).

I have way to always trigger that freeze. fsck -f. I can boot in 32bit and check all my partitions that they really are clean, then boot in 64bit and fsck -f freezes after couple of minutes in any of those partitions. (fsck is not only way to freeze computer, but it triggers it _every_ time)

Freeze happens with LIVE-cd too.

I have runned full memtest several times.
Now I removed 1G and 1G from computer and I can run fsck on 64bit without freeze!

Questions: Is my memory (those 1G+1G) broken, even memtest pass, or why they render my 64bit system very unstable? What more I can do than memtest?

---

### Post by darco on 2009-09-22
What type of memory is it? Were they matched (paired) when you purchased them?
Have you tried  installing the memory in different slots, have you tried possibly borrowing memory and swapping out the simms to see if in fact it is defective memory. Is the memory o/c? Bios setting 1T?

good luck

darco

---

### Post by aapo4 on 2009-09-22
> Is the memory o/c? 
I do not understand this. 

> Bios setting 1T?
I didn't find 1T in BIOS settings.

I have tested different slots.

They are DDR2 dimm (240pin). 1G+1G come from computer and they are pair. I do not have any info about them, this is what reads on top of chips M2U800-1GBJ PC2-6400 CL-5 UDIMM. 

2G+2G are pair. (I know very little about them, but dmidecode said they are 800 MHz).

My motherboard is P5B-VM and I have manual of it! It has four slots, and they are divided channel A and channel B. 
From manual: "You may install varying memory sizes in Channel A and Channel B." [...] "Always install DIMM's with the same CAS latency"

CAS latency == CL, Am I right? Is there software way to check CL?

Are speed of memorys relevant?

If this is something related to memory compatibility, is this normal that computer starts and works, but under 'special' use it freezes?

---

### Post by dcstar on 2009-09-23
> **aapo4 said:**
> I do not understand this. 


I didn't find 1T in BIOS settings.

I have tested different slots.

They are DDR2 dimm (240pin). 1G+1G come from computer and they are pair. I do not have any info about them, this is what reads on top of chips M2U800-1GBJ PC2-6400 CL-5 UDIMM. 

2G+2G are pair. (I know very little about them, but dmidecode said they are 800 MHz).

My motherboard is P5B-VM and I have manual of it! It has four slots, and they are divided channel A and channel B. 
From manual: "You may install varying memory sizes in Channel A and Channel B." [...] "Always install DIMM's with the same CAS latency"

CAS latency == CL, Am I right? Is there software way to check CL?

Are speed of memorys relevant?

If this is something related to memory compatibility, is this normal that computer starts and works, but under 'special' use it freezes?

You may be better to replace the original 1G RAM with the same type as your new 2G modules, it is possible that they are too different for the M/B to cope with correctly when mixed.

---

### Post by rhk on 2009-10-06
I got the same MB, same CPU and same 1G memories as aapo4 (we bough the computers together), I've been trying to make 1+1+1+1 run. It freezes on KDE login, can't get further.

Memories:
Buffalo Value 1GB DDR2-800 CL5 [M2U800-1GBJ]

CPU:Intel Core 2 Duo E6600

I updated the bios to version 1004 (dated 05/2008), from version 0405 (09/2006) but it does no good.

I run Kubuntu 9.04 64-bit.

Many people have had the same problem here: [http://vip.asus.com/forum/view.aspx?SLanguage=en-us&id=20070222154337155&board_id=1&model=P5B-VM&page=1&count=29](http://vip.asus.com/forum/view.aspx?SLanguage=en-us&id=20070222154337155&board_id=1&model=P5B-VM&page=1&count=29)

but no ultimate solution has been found. 

I'll run the memtest and try turning the memory mapping off.. 
Some users suggest to take the memory voltage to 1.9 - even up to 2.1 volts (sounds like a lot to me..)


r

---

### Post by rhk on 2009-10-07
> **rhk said:**
> 
I'll run the memtest and try turning the memory mapping off.. 
Some users suggest to take the memory voltage to 1.9 - even up to 2.1 volts (sounds like a lot to me..)


Tried 1.9V, didn't help.

memtest gave me a bunch of errors but I believe it's the configuration, not the memories.. don't know..

Should test the memories separately to make sure they all work..

r

---

### Post by rhk on 2009-10-07
ok, looks like on one of the memories is broken.. Left that one out, I get 3008MB recognized by BIOS, kubuntu shows me MemTotal:        2874640 kB     

(looks a little small to me that 28xx xxx KB ?)


r

---

### Post by falconindy on 2009-10-07
Historically, running with all 4 memory banks filled has required a 2T command rate instead of 1T. As long as you're not mixing memory sizes within the same channel, you should be able to run with this setup.

When you say one of the modules is "bad", do you mean that you tested it and found it bad in memtest? Are you just assuming its bad because the comp works when you take it out? I would retest with the slower command rate...

---

