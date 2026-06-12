---
title: "Ubuntu 9.04 amd64 uses only 4GB out of 8GB RAM"
date: 2009-10-08
forum: x86 64-bit Users
---

### Post by ljubomirjosifovski on 2009-10-08
System with CPU i7-860, mobo Asus P7P55D Pro, 8GB RAM (4 x 2GB modules). Problem is that Ubuntu 64 finds only 4GB (-ish; actually bit less). Have the latest Bios (ver 0711), bios memory remapping is turned on (after bios upgrade 0606 -> 0711 the setting can't be turned off). Searched the forums, all I found was people having 4GB getting a lot less then that, nothing seemed similar to my case. 

Some diags/info:

$ dmesg | grep BIOS
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  BIOS-e820: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==>
[0000000000 - 0000001000]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==>
[000009fc00 - 0000100000]
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    4.976733] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg01: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
reg03: base=0x0fffe0000 ( 4095MB), size=   64KB, count=1: write-protect

$ free
             total       used       free     shared    buffers     cached
Mem:       3979608    1038248    2941360          0     107796     442608
-/+ buffers/cache:     487844    3491764
Swap:     19824200          0   19824200

$ uname -a
Linux nugigul 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC
2009 x86_64 GNU/Linux

Running $ dmidecode (output attached) shows Bios reporting 4 x 2GB modules (also Vista  64bit finds the whole 8GB RAM fine), but the Bios setup thinks it's got only
4GB (-ish).

Help/ides what ot try most wellcome.

Thanks,
Ljubomir

---

### Post by Slim Odds on 2009-10-08
Does the machine recognize the 8G when you're in the BIOS?

I have 8.10 64 bit with 8G, no problems.

---

### Post by ljubomirjosifovski on 2009-10-08
BIOS reports System Memory, Usable size : 4088MB.

Btw upgraded to Ubuntu 9.10 beta, now 

$ free
             total       used       free     shared    buffers     cached
Mem:       4050264     418896    3631368          0      27568     177044
-/+ buffers/cache:     214284    3835980
Swap:     19824200          0   19824200

 but otherwise the rest is as before.

Thanks,

---

### Post by NoaHall on 2009-10-08
Then try either moving your modules around, or *danger warning* you could try flashing your bios.

---

### Post by ljubomirjosifovski on 2009-10-08
Thanks. Flushed the BIOS this morning with the latest/greatest from Asus, didn't help.

The dmidecode does report (that BIOS can see) 4 x 2GB RAM modules (report  log attached to the initial post). And Vista 64 reports using 8GB RAM - so unlikely to be loose modules (it is a new box though).

Other possibly relevant stuff from dmidecode does not seem bad, excerpts from dmidecode.log:

Handle 0x0008, DMI type 5, 24 bytes
**Memory Controller Information**
   Error Detecting Method: 64-bit ECC
   Error Correcting Capabilities:
      None
   Supported Interleave: One-way Interleave
   Current Interleave: One-way Interleave
[B]   Maximum Memory Module Size: 2048 MB
   Maximum Total Memory Size: 8192 MB
[/B]   Supported Speeds:
      Other
   Supported Memory Types:
      DIMM
      SDRAM
   Memory Module Voltage: 3.3 V
   Associated Memory Slots: 4
      0x0009
      0x000A
      0x000B
      0x000C
   Enabled Error Correcting Capabilities:
      None

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
   Socket Designation: DIMM0
   Bank Connections: 0 1
   Current Speed: Unknown
   Type: DIMM SDRAM
   Installed Size: 2048 MB (Double-bank Connection)
   Enabled Size: 2048 MB (Double-bank Connection)
   Error Status: OK

and likewise for the other slots A, B and C.

---

### Post by sanderj on 2009-10-08
Very interesting case!

@"Vista 64bit finds the whole 8GB RAM fine": *where* does Vista report the 8GB? In the control panel -> system? If so, that's only the physical installed RAM (like reported by Ubuntu's 'sudo dmidecode' / 'sudo lshw'), not the usable RAM.

What does memtest report: 4GB or 8GB? You can run memtest from the Ubuntu boot menu (both live CD and installed), or from a separate memtest-CD.

---

### Post by sanderj on 2009-10-08
[http://usa.asus.com/product.aspx?P_ID=j02KziJq95KbCQNm](http://usa.asus.com/product.aspx?P_ID=j02KziJq95KbCQNm) -> Specification gives this information:

> 

Memory	 

4 x DIMM, Max. 16 GB, DDR3 2200(O.C.)*/1600/1333/1066 Non-ECC,Un-buffered Memory
Dual Channel memory architecture
Supports Intel® Extreme Memory Profile (XMP)
*Hyper DIMM support is subject to the physical characteristics of individual CPUs. Some hyper DIMMs only support one DIMM per channel. Please refer to Memory QVL for details.
**Refer to [www.asus.com](www.asus.com) or this user manual for the Memory QVL(Qualified Vendors Lists). 

So max mem is 16 GB, so your 8 GB should not be a problem.


Have you checked your memory in the QVL?

---

### Post by sanderj on 2009-10-08
A bit like NoaHall suggested: what happens when you pull out one DIMM? And two DIMM pulled out?

---

### Post by ljubomirjosifovski on 2009-10-08
Thanks all.

I stand corrected: Vista 64 uses only 4GB (reported in taskmgr) even if it finds the 8GB (reported in System Information) - thanks sanderj. As you said, it is exactly as with Ubuntu dmidecode/lshw v.s. free/dmesg.

When I take 2 x 2GB dimms out, BIOS reports as before 4088MB, and Ubuntu's lshw/dmidecode report 2 banks with RAM only (and Vista System Information reports 4GB RAM only).

Memtest x86 (from the Grub boot menu) reports 4088MB as well. Memory tested fine.

Memory is CORSAIR TR3x6G1600C9 9-9-9-24 1600MHz 2048MB (x4 DIMMs). 
I see on the QVL DDR3-1600MHz capability for CPU at 2.8GHz (as per the i7-860) listing "CORSAIR TR3XG1600C9(XMP)Ver2.1". However "Size" is listed as "6144MB(Kit of 3)"? I obviously have 4 of those. Also not sure about the "(XMP)Ver2.1" sufix - didn't see that on the dimms?

Ljubomir

---

### Post by ljubomirjosifovski on 2009-10-08
As a sidenote: Asus info on why 4088MB instead of 4096MB is detected (8MB lost) -

[http://support.asus.com/faq/faq.aspx?no=89BB904F-C597-EE76-36CD-E0EDCD6CDD00&SLanguage=en-us](http://support.asus.com/faq/faq.aspx?no=89BB904F-C597-EE76-36CD-E0EDCD6CDD00&SLanguage=en-us)
[SIZE=1]
[/SIZE][SIZE=1][IMG]http://support.asus.com/images/arrow-001O.gif[/IMG]                                     **Problem**[/SIZE]                                                                                                                                                            [SIZE=1][IMG]http://support.asus.com/images/Spacer.gif[/IMG]                                                      [[IMG]http://support.asus.com/images/addshortcut.gif[/IMG]]("http://javascript%3Cb%3E%3C/b%3E:add_shortcut%28%29")                                                 [IMG]http://support.asus.com/images/Spacer.gif[/IMG]                                                      [[IMG]http://support.asus.com/images/addfavorite.gif[/IMG]]("http://javascript%3Cb%3E%3C/b%3E:add_favorite%28%29")                                              [/SIZE]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    [SIZE=1]My system always detect 8MB of RAM less than expected when operating under single channel or dual channel asymmetric mode, and 16MB less when operating under dual channel interleaved mode.
Why is that? Is there any ways to release them?[/SIZE]                                                                                                                                                                                                                                                                                  [SIZE=1][IMG]http://support.asus.com/images/Spacer.gif[/IMG]
[/SIZE]                                                                                                                                          [SIZE=1][IMG]http://support.asus.com/images/arrow-001O.gif[/IMG]                                     **Answer**[/SIZE]                                                                                                                                                                                                                                                                                                                                                    [SIZE=1]This is simply because this motherboard / system adopts the new Intel AFSC technology which occupies 8MB of RAM space at all times due to the need to use Intel ME technology. As dual channel interleaved mode requires both DIMMs to be in the same size, another 8MB of RAM will be taken from the second dimm on the other channel to balance the two channels. Hence, this is normal for this board.  Also, as this motherboard / system requires ME enabled to function, there is no way to release this memory space[/SIZE]

---

### Post by NoaHall on 2009-10-08
Hm, maybe your motherboard doesn't support 1600 MHz

---

### Post by AppleBonker on 2009-10-08
> **ljubomirjosifovski said:**
> 

Memory is CORSAIR TR3x6G1600C9 9-9-9-24 1600MHz 2048MB (x4 DIMMs). 
I see on the QVL DDR3-1600MHz capability for CPU at 2.8GHz (as per the i7-860) listing "CORSAIR TR3XG1600C9(XMP)Ver2.1". However "Size" is listed as "6144MB(Kit of 3)"? I obviously have 4 of those. Also not sure about the "(XMP)Ver2.1" sufix - didn't see that on the dimms?



I'm running almost the exact same setup (i7 860, same ram but I think the 4 stick pack has a different part number even though it is just an extra stick of the TR3X6G1600C9) but on an Asus P7P55D Deluxe.  I had the same problem out of the box with my setup.  Try cold booting (turn the PC off for a bit - like 15 minutes - then back on).  When I did this, I could get the bios and OS to recognize all 8 gigs.  However, on reboot I'd drop back down to 4 usable.  When all 8 gigs is recognized in the bios, I was able to run 3 passes of memtest without issue, so I swapped the mobo and continued to have the same problem.

The fix for me was swapping the ram.  I exchanged it for the exact same model, and I haven't reproduced the issue since.  I was fortunate enough to have purchased from Microcenter (somewhat small chain - local store), so exchanging was simple for me.  This is in the only thing I could get to work.  I originally tried every bios version I could find and nothing.  Your combination is certainly compatible.  I just hope you have the ability to swap the ram.  If you have any more specific questions about my configuration, let me know and I will gladly provide more details.

From scouring the web looking for a fix, this seems to be a somewhat common issue with the P55 boards (no matter the manufacturer).

---

### Post by ljubomirjosifovski on 2009-10-08
Thanks AppleBonker, most helpful info. 

Will try swapping the modules arround a few times, and also use mobo's built-in memory compatibility tester called "MemOK!" :-) (ex: [http://www.hardwaresecrets.com/printpage/806](http://www.hardwaresecrets.com/printpage/806)) to see if it comes up with anything when I gain access to the box tomorrow.

Thank you all for your help.

---

### Post by AppleBonker on 2009-10-08
All the memOK! feature will do is test various configurations to find one that is stable for boot.  If the bios does not show all 8 gigs on power up, memOK! will not enable them, at least in my experience.  It took me about a week to correct this issue on my box, during which time I probably rebooted, removed ram, reseated ram or ran memtest upwards of 500 times - no joke.  I ran memtest on each individual stick, on at a time, and all tested ok.  I was absolutely convinced that the memory was ok.  Once I swapped the motherboard, I didn't really know where to turn.  In fact, I was so convinced that the issue wasn't with the mobo or the ram (read reviews of other users running the same ram and mobo but with the i5 750) that I was trying to exchange the cpu.  I figured since the memory controller is on cpu that my processor was bad.  Before getting to this, I tried swapping the ram just because it would be far easier than trying to return a processor.  I rebooted probably 10 times and never lost out on all 8 gigs.

After that, I probably checked the bios on boot the next hundred or two times I launched to ensure that I was recognizing all the ram.  By that point, I stopped monitoring it as closely.  However, I've got conky running on my desktop displaying free/used ram, so I find myself glancing at it occasionally to see if I'm still ok.  It is somewhat worrisome that other people are experiencing the same issue, but I guess that's the price of being on the cutting edge of technology.  Good luck, and like I said I will assist in any way possible so that you can get up and running.  I'm sure you'll be happy once your up and running (this PC has handled everything I've thrown at it so far).

---

### Post by P.KO on 2009-10-09
I have build a lot of systems in the past. My advice, when it comes to memory, is to buy recommended modules by the mobo manufacturer or from a branded memory manufacturer. I settled for Kingston and had never had any issues on more than 300 systems of which many of them at that time were high performance.

Never buy cheap noname memory modules. It will give you issues like you have and even hanging systems.

---

### Post by ljubomirjosifovski on 2009-10-09
AppleBunker, I understand your memory was 1600MHz as well, correct? 
Asking because in the P7P55D Pro manual on page 2-11 I see: "Due to Intel Spec X.M.P.DIMMs and DDR-1600 are supported for one DIMM per channel only". I'd interpret that as being out of luck with my 4x 2GB 1600MHz sticks (two channels, 1 per channel => 2 max supported)? Thanks,

---

### Post by AppleBonker on 2009-10-09
> **ljubomirjosifovski said:**
> AppleBunker, I understand your memory was 1600MHz as well, correct? 
Asking because in the P7P55D Pro manual on page 2-11 I see: "Due to Intel Spec X.M.P.DIMMs and DDR-1600 are supported for one DIMM per channel only". I'd interpret that as being out of luck with my 4x 2GB 1600MHz sticks (two channels, 1 per channel => 2 max supported)? Thanks,

Yes, it is 1600 MHz ram.  When I first got the computer running stable, I had the bios detecting the ram with default (auto) settings.  The auto detection runs the ram at 1333 MHz.  However, I then set the voltage and frequency manually and have been running 8 gigs (the 4x2 gig sticks) at 1600 MHz completely stable.

As for that comment, I think that is just a conservative Intel recommendation.  I read that as Intel saying they can't guarantee it will work.  But you cannot interpret that to mean that it definitely wont work either.  I'm fairly certain that this restriction holds true for tri-channel LGA 1366 boards as well, though there have been vast numbers of reports of people running two DIMMs per channel on those as well.  This is merely my interpretation of the info I found while researching this build, however.  Hopefully someone more knowledgeable can chime in...

---

### Post by ljubomirjosifovski on 2009-10-12
Thanks. Recommendation inerpretation makes sense. Waiting on the vendor to send me replacement RAM to try with.

---

### Post by AppleBonker on 2009-10-12
> **ljubomirjosifovski said:**
> Thanks. Recommendation inerpretation makes sense. Waiting on the vendor to send me replacement RAM to try with.

I certainly hope that works for you.  Please let us know the outcome.  New egg has a review of this board where the poster has essentially the same ram (cas latency 8, not 9 like you and I have) and it works there without issue.  I'm fairly certain that particular model ram autodetects at 1600 MHz, so that is another vote of compatibility.  Hopefully it holds true for you as well!

---

### Post by iTrascurato on 2009-10-13
I have an Asus P6T, Core i7 920, and 8gb (3x 2gb) of OCZ Gold DDR31600.

System monitor is showing 1.3gb of 3.8gb used, right now.

It was a PITA to get this to finally work right.  It times the memory incorrectly out of the box, and would restart before I could get to the point in bios to set it to a stable 9-9-9-24-auto*.

I'm not that worried about having an extra 2GB as this is sufficing, but it would be nice to get what I've paid for.

Any ideas guys?

---

### Post by ljubomirjosifovski on 2009-10-16
> **AppleBonker said:**
> I certainly hope that works for you.  Please let us know the outcome.

Thanks, it worked out, problem solved. 

The new RAM sticks are labelled "CORSAIR CM3x2G1600C9DHX XMS3-1600 2048MB 1600MHz 9-9-9-24 1.80V ver9.1" and they worked out of the box. BIOS setup reported the whole 8GB the very first time. Ubuntu happily found them as well, etc.

So it was RAM - motherboard incompatibility it seems.

Thanks to all posters to this thread, you've been most helpful.

Regards,

---

### Post by ljubomirjosifovski on 2009-10-16
> **iTrascurato said:**
> I have an Asus P6T, Core i7 920, and **8gb (3x 2gb)** of OCZ Gold DDR31600.

I take the 8GB above is a typo and you have 6GB RAM?

> **iTrascurato said:**
> I System monitor is showing 1.3gb of 3.8gb used, right now.

It was a PITA to get this to finally work right.  It times the memory incorrectly out of the box, and would restart before I could get to the point in bios to set it to a stable 9-9-9-24-auto*.

I'm not that worried about having an extra 2GB as this is sufficing, but it would be nice to get what I've paid for.

Any ideas guys?

Easy things to check:
  1) Memory remapping in the BIOS setup enabled?
  2) BIOS system info shows 6GB RAM?
  3) Ubuntu is 64bit version?

---

### Post by gktaylor on 2009-10-17
I have the same problem with my system with a different motherboard. How likely is it that future BIOS versions will solve the problem and correctly recognize my other two memory modules? I am still within the return period for my RAM and am wondering if I should just be patient or return the RAM immediately.

motherboard: Gigabyte GA p55M UD2
ram: 4x Kingston DDR3 2000 MHz

---

### Post by iTrascurato on 2009-10-18
> **ljubomirjosifovski said:**
> I take the 8GB above is a typo and you have 6GB RAM?



Easy things to check:
  1) Memory remapping in the BIOS setup enabled?
  2) BIOS system info shows 6GB RAM?
  3) Ubuntu is 64bit version?

It is 6gb, yes, my bad.  Typo.

64-bit Ubuntu.  Memory remapping?  Are you referring to auto timing?  I had to change *from* auto timing in order to get the system to run for more then 20 seconds, otherwise -- I am not sure.

Bios shows 6Gb, yes.

---

### Post by khal03 on 2009-10-29
I too have had this problem. As in "not any more!"

I am not a programmer, so it has to be easy, Right?

My cooler will not let me even run a live cd with 8gb installed, I have to start with 2gb. So I have to do all of my configurations and then open the box and add the other 3 sticks, however, it works flawlessly.

1. Install with 8.04 or newer from a live cd

2. Reboot and install firestarter and envyng-qt

3. sudo firestarter, (I open preferences and click minimize to taskbar and I click ICMP filtering and I enable ICMP but I don't click any of the individual boxes, and then I save and test at shields up website.)

4. With working firewall I search in google the term "ubuntu 8gb PAE" The 4th link takes me to [http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

5. I follow instructions for the second solution (as I cannot make any Ubuntu distro use 8gb any other way no matter who claims what) and then I reboot

6. I go to Applications>System Tools>Envyng (in my case I have nVidia so I select nVidia) and then I use the reccomended automatic install and let it fly

7. After a reboot I instal my games and codecs and everything else.

Flawless, easy.

Let me know if it works for you.

Now you can get what you paid for. It isn't the ram chips usually. On my MSI board I found that I had to turn off the auto select in the bios for the ram and set it at 677mhz as it could not and would not run 8gb at 800mhz. However, I do video editing with two 1gb nVidia SLi bridged PCIe cards and I really notice no difference in performance with 2gb ram, so I accept this. Actually, I was able to spend about 800 dollars on awesome hardware after a year or two of Ubuntu only computing since solutions like this were free, from free software. Don't get frustrated Ubuntu rocks, its the people with the most posts I find that suck, well and my old OS.

Chow

---

