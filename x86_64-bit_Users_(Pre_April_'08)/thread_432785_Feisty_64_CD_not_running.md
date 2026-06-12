---
title: "Feisty 64 CD not running?"
date: 2007-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by mario8723 on 2007-05-04
I just built a new computer centered around a  AMD Athlon 64 X2 3600+ Brisbane 1.9GHz. I'm also running a  WD 200GB SATA 3.0Gb/s Hard Drive. 
Since first turning the PC on I've tried installing Feisty, but just continue to see errors like fd0 not found? I installed XP as this is going to be a dual-boot machine and that went off without a hitch. Is there a problem with SATA 3.0 drives and Feisty? What else could be wrong?

---

### Post by ronocdh on 2007-05-04
> **mario8723 said:**
> I just built a new computer centered around a  AMD Athlon 64 X2 3600+ Brisbane 1.9GHz. I'm also running a  WD 200GB SATA 3.0Gb/s Hard Drive. 
Since first turning the PC on I've tried installing Feisty, but just continue to see errors like fd0 not found? I installed XP as this is going to be a dual-boot machine and that went off without a hitch. Is there a problem with SATA 3.0 drives and Feisty? What else could be wrong?
Have you verified the checksum on the CD? I know several people using SATA drives and they never mentioned jumping through any hoops getting Ubuntu to run on them. I personally like the alternate installer CDs, too, if that's something you'd consider.

Please try to post the exact error output you're getting; transcribe it when it appears, or even snap a digital picture of your monitor, as long as the text is all completely legible.

---

### Post by kuja on 2007-05-04
> **mario8723 said:**
> I just built a new computer centered around a  AMD Athlon 64 X2 3600+ Brisbane 1.9GHz. I'm also running a  WD 200GB SATA 3.0Gb/s Hard Drive. 
Since first turning the PC on I've tried installing Feisty, but just continue to see errors like fd0 not found? I installed XP as this is going to be a dual-boot machine and that went off without a hitch. Is there a problem with SATA 3.0 drives and Feisty? What else could be wrong?
with regards to /dev/fd0 not found, that doesn't matter much, that would be the floppy drive.

---

### Post by mario8723 on 2007-05-04
I don't have a floppy drive. Just a DVD/CD combo and the hard drive. Even still, wouldn't it run as a Live CD?

With regards to the checksum, I've downloaded and burned two different .iso's, both from different locations so I can't see it being that.

---

### Post by mario8723 on 2007-05-04
These are the errors:

193.135361 Buffer I/O error on device fd0, logical block 0
205.324249 had: error code: 0x70 sense_key: 0x05 asc:0xa8 ascq: 0x3

It just keeps alternating and repeating? I don't think it's hardware error as I was able to install XP just fine. For some reason, though, Feisty just does not like this machine.

---

### Post by ronocdh on 2007-05-04
> **mario8723 said:**
> These are the errors:

193.135361 Buffer I/O error on device fd0, logical block 0
205.324249 had: error code: 0x70 sense_key: 0x05 asc:0xa8 ascq: 0x3

It just keeps alternating and repeating? I don't think it's hardware error as I was able to install XP just fine. For some reason, though, Feisty just does not like this machine.
Maybe [this post]("http://www.linuxquestions.org/questions/showthread.php?t=502353") will help you regarding the first error; it's about using the GParted live CD, but it's spitting the identical error (I just googled the "Buffer I/O..." string you provided).

The second error is a bit more puzzling to me. Have you tried using the alternate CD to install? That to me is always more stable--and far less ostentatious. ;)

---

### Post by mario8723 on 2007-05-05
I tried installing with the alternate CD and had no success? :confused: Tried LinuxMint 2.2 and Backtrack 2 and nothing...The Backtrack install stopped when it couldn't find chroot? Does that make any sense?

---

### Post by jespdj on 2007-05-05
> **mario8723 said:**
> I don't have a floppy drive. Just a DVD/CD combo and the hard drive. Even still, wouldn't it run as a Live CD?

With regards to the checksum, I've downloaded and burned two different .iso's, both from different locations so I can't see it being that.

Have a look at the BIOS settings of your computer. I also don't have a floppy drive, but the BIOS has a setting named "Legacy Floppy Drive Support" or something like that. When I set that to Enabled, I will get to see a drive A: in Windows, even though there is no floppy drive. When I set it to Disabled, I don't get drive A: in Windows.

Maybe Ubuntu thinks there is a floppy drive connected because you have a similar setting set to Enabled in your BIOS.

---

### Post by ryan56 on 2007-05-05
I had a similar problem, but found an answer.
Do you use a DVD drive for your ubuntu live cd?
Than that's your problem.  Install a CD drive. and use that, Go to BOOT and put the CD drive at the first place (priority).
I also have another problem, after installing  a CD drive and loading the CD, i had an error message:
"Can't access tty: Job control turned off."

I've googled for some time but because this is my first time trying to use Linux i've got no clue of what they're talking about.
Does anyone know the answer for my problem?
I have a Mycom PC with Intel Core 2 CPU @ 2.13 Ghz
1015 MB of RAM
a 64-bit PC
and a Nvidia Geforce 7300 GS with 507 MB of memmory and 256 MB of some other kind of memory.
I also have an onboard Video Card: Intel 82945G Express Chipset Controller 0 (?) using a Windows Vista Home Premium (one of the reasons i want to switch to Ubuntu)
And By the way, i don't have a Floppy drive and recently installed a very old CD drive from my Packard Bell Imedia which I bought in 2003

---

### Post by mario8723 on 2007-05-05
Well, my BIOS has auto-detect floppy disabled and is not listed in the boot order. Still getting the same errors :( This is really frustrating. I'm going to try throwing a floppy in there from my other machine and see how that works out.

---

### Post by Cappy on 2007-05-05
It might be a motherboard problem? My feisty is running on a brisbane in a 500GB Sata HD (3.0). It might be worth trying to google your mobo and seeing if it has problems. You might need to turn APIC off in the BIOS and/or boot with the noapic option.

---

### Post by Jouke74 on 2007-05-07
Could you try posting your FSTAB file?

I do have a floppy drive, and with my it always got the mountpoint wrong... 
(and thus it was recognized as two floppy drives).

---

