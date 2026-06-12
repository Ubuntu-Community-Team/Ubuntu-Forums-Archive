---
title: "install problems on AMD 64 bit dual core"
date: 2006-09-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by dba_guy_2000 on 2006-09-26
Hello;

 I am trying to install version 6.01 server of Ubuntu and I get one of two problems, immediately following the Linux decompression.  When I try to do a normal install, it hangs following the decompression. If try for any install option I receive a stack trace with and a kernel panic, not syncing.

My hardware profile is on AMD Atholon 64 AMX X2, Dual core, with an Asus M2NSLI-D AM2 motherboard. 

I have tried to install other falvours of linux, and I receive the same problem. 
Please help
Thank you.

---

### Post by hajk on 2006-09-27
Not sure what your problem is... does the install CD boot OK?

---

### Post by j-strap2 on 2006-09-27
dba_guy_2000, I had just the same problem helping a friend install last night. We tried ubuntu 64, i386, 64-alternate and still the same problem. This was on a single core 64. I'll update with the exact system spec. later today. Very frustrating, as I am trying to wean him off windows.

Edit: looks like a hardware problem with my friend's system - won't install windows either. Back to the store tomorrow.

---

### Post by mardoq on 2006-09-27
My problem is not only installation, but even running the Live DVD AMD64. It freezes shortly after choosing to run Ubuntu. I'm choosing the language, press enter, and ... taht's it! Curiously, I've managed to run and install the i386 version, but it didn't support my Marvell net adapter and besides I wanted 64...
My hardware is a dual core AMD Athlon64X2 3800+ on Gigabyte GA-M55S-S3, RAM 1 GB, graph. nVidia GeForce 7300GT. 
I'm an absolute beginner in Linux and I'm trying to linuxize myself for the 5th time and this time I'm very much determined...

---

### Post by breuerp on 2006-09-27
Add "nomce" (minus the quotes) to your boot line immediately before "nosplash".

---

### Post by dba_guy_2000 on 2006-09-27
Hello and thank you.   The CD does start up, and Linux kernel decompresses and starts to run.  It prints on the screen the start of these first two steps. Then I get sync error and stack trace. I will try some of the stuff that was written above. I am also wondering if it is hardware problem. I have only tried to install different distributions of Linux.  The goal of this machine is web server with Sybase.

---

### Post by dba_guy_2000 on 2006-09-27
> **breuerp said:**
> Add "nomce" (minus the quotes) to your boot line immediately before "nosplash".

How exactly to I enter these? sorry, to be so basic. i think the my key board is not picking up when I press f6

---

### Post by breuerp on 2006-09-28
When booting the machine you should see a message that says something like "Starting Grub loading hit Esc to cancel" at which point you'll hit Esc.  Use the arrow keys to select the latest kernel you have loaded and then hit the 'e' key to edit the command line settings.  The longest line should have "nosplash" (minus the quotes), on that same line put "nomce" (minus the quotes) immiately before nosplash.

---

### Post by j-strap2 on 2006-09-29
My problem was hardware: swapped the RAM and installed without problem.

---

### Post by stefano67 on 2006-09-29
Same problem here with ASUS M2N-E and Athlon X2 3800+.

I was able to boot adding 'noapic' before 'nosplash'. The same happened with Fedora Core 5 on this board. Maybe some bios issues?

---

### Post by stewarma101 on 2006-09-30
I had this problem when installing I spent hours retrying and finally removed the ram and put one strip back, installed and put the ram back when it finish. It didn't matter though my hard drive crashed 2 days later](*,) . 
Try the ram thats what i was told. 
matt

---

### Post by abshnasko on 2006-10-03
Yep, trying to install Ubuntu Server 6.06 and I get "kernel panic" before I can even install. I, also, am running an Athlon X2 socket AM2. I tried to do the check cd option in the boot menu, same error.

---

### Post by RAOF on 2006-10-03
> **stefano67 said:**
> Same problem here with ASUS M2N-E and Athlon X2 3800+.

I was able to boot adding 'noapic' before 'nosplash'. The same happened with Fedora Core 5 on this board. Maybe some bios issues?

The number of motherboards with buggy APIC/ACPI/other four-letter-actronym implementations always amazes me :)

---

### Post by abshnasko on 2006-10-03
Hmm ok, I got mine working without having to add any of those commands; I switched my RAM setup to make it single channel...no switched modules, just changed the slots on the board and it works. Is this a problem with Linux or the board?

---

### Post by RAOF on 2006-10-03
> **abshnasko said:**
> Hmm ok, I got mine working without having to add any of those commands; I switched my RAM setup to make it single channel...no switched modules, just changed the slots on the board and it works. Is this a problem with Linux or the board?

I'd run a memtest.  It's possible that one of your sticks of ram is bad, and now it's placed after the good stick you can boot, but will have problems later, when the ram fills up.  It's also possible that the ram wasn't seated properly before, or that the slot that you had it in was broken.  I don't believe that the kernel can tell the difference between single-channel/dual-channel memory, so I'd say it's a problem with the board or the ram rather than with Linux.

---

### Post by Phloston on 2006-10-15
I had problems similar to what is described in the thread.
I have an ASUS M2N-E with an AMD64 2x 4200+. My problem was solved after upgrading the BIOS to 0304.

---

### Post by keithwill on 2006-10-15
Having a similar problem with M2N32 SLI AM2 with X24800+

Haven't found way around it yet.

---

### Post by diocles on 2006-10-25
same problem here with m2n-e and x2 3800... i have 2x512 dual channel ram. though im not switching dual channel of or anything, ill rather find a linux distro that works on x2 with dc ram. windows runs absolutely fine with all kinds of applications. of course windows is temporary.

---

### Post by Sanne on 2006-10-25
As some people already said, definitely check your ram. There's a memtest option at the boot screen of the install cd where you can start the test. Let it run for some time (hours), there must not be any errors. Preferably test your ram sticks seperately.

I had similar behaviour with one of our newly built systems, and we immediately got lots of errors in memtest with one of the ram sticks.

Good luck, Sanne

---

### Post by uga2 on 2006-12-07
:D 
AMD 64 X2 4200+, M2N-E, (single) 1GB DDR2 Kingston, GeForce 7950GT

I've just got openSUSE installer finally loading without kernel panic after BIOS update on the motherboard to 0304. I'm going to try installing Edgy tonight...

---

### Post by mandible on 2007-02-23
I also have issues installing on Ubuntu 64 bit
on M2N-SLI Deluxe Motherboard by ASUS
got the disable apic message and tried that but
ended up getting a blank screen before getting to the livecd
screen.

---

### Post by bpasham on 2007-04-05
I assembled  my first AMD64 system with M2A-VM mother board 4x1GB 667 RAM and Athlon 64 X2 420++ 65W processor and 2x300GB Seagate SATA2/300 disks. I was unable o install any version of Ubuntu on it. The maximum I reach is with 6.06LTS 64 server install .. and it cannot detect NIC device on the board . installation cannot continue after. 

Any solution to this problem?

Once I select Install to Hard Disk .. the screen goes blank after the starting vmlinuz .....

I even tried 7.04 beta editions .. same problem ..

Please Help me ....

---

### Post by nss0000 on 2007-04-05
BigS:

I had install issues with similar kit: AMD5400+ / ASUS-M2N ..... using mailed_from_factory_CDs Edgy would NOT install, while DDrakex64 dropped right in. I did need to use a SBlaster card and legacy NIC, but otherwise no problemo.

nss
******

---

### Post by mandible on 2007-04-05
with DDrake 64 where you able to upgrade to the Edgy with any issues afterwords.  and or fiesty.

---

### Post by Justin123 on 2007-04-05
> **dba_guy_2000 said:**
> Hello;

 I am trying to install version 6.01 server of Ubuntu and I get one of two problems, immediately following the Linux decompression.  When I try to do a normal install, it hangs following the decompression. If try for any install option I receive a stack trace with and a kernel panic, not syncing.

My hardware profile is on AMD Atholon 64 AMX X2, Dual core, with an Asus M2NSLI-D AM2 motherboard. 

I have tried to install other falvours of linux, and I receive the same problem. 
Please help
Thank you.

Hi, I have almost the exact same hardware as you in a computer that I just build and I am also running a amd 64bit dual core.  So what im getting at is that i dont think that it is your processor.  I installed the 6.10 version of ubuntu and it worked so maybe you should try that.  SEe yA

---

### Post by cuculus on 2007-05-18
It's not a Linux problem guys (girls) - I have the opposite problem with an M2N-E and a AMD X2 4400+, while trying to install Windows.  Fawn installed perfectly and runs like a champ but the board won't even think about installing windows.  I called Asus and they had me do some RAM gymnastics and then told me to RMA the board when that didn't work, but I tried to impress on the guy that Ubuntu was running fine so it's not the RAM or the board...  I know this is a Ubuntu board but if anyone knows any tips for getting XP to install on this board I would appreciate it.  I'm starting to GTA withdrawal...and my stats package SPSS won't run on Ubuntu.

Thanks

Greg

---

