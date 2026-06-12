---
title: "New system has begun spontaneously turning itself off"
date: 2009-09-29
forum: x86 64-bit Users
---

### Post by n8hfi on 2009-09-29
[I]Edit 10/2/2009 2200Z:
This problem has been resolved.  It's apparently a flaky power switch in a nearly new case.  The test that lead me to believe it might be a software problem (up for 12 hours with booted from 32-bit live CD, repeatedly turns off booted from 64-bit install on HD) was a fluke.  Read postings below for more details, if you're interested.[/I]

I have a new system that had been working fine, and stayed up, for about three weeks since I finished the installation.  Last Thursday I found the machine off.  Turned it back on, booted up and logged back in, everything was working fine until about 30 minutes later, when the machine turned off.  Rebooted again, this time about 10 minutes before it turned off.

When I say "turn off", I mean it literally.  It's exactly as if I pressed the front panel power button, except it doesn't count down 60 seconds before doing it.  The shutdown dialog box even appears ("the system will shutdown in 60 seconds") except it doesn't wait--it shuts down immediately.  When I've been sitting at the computer as it happens, I have just enough time to click the cancel button, if I'm very quick--but it doesn't stop, it shuts down anyway.  It happens anywhere from a few minutes to a couple of hours after booting.  (Once--just after I unplugged the USB cable to the UPS--it lasted about 5 hours.  I thought I was onto something for a while there.)

I've suspected hardware, of course, except that it stayed up more than twelve hours when I booted the Ubuntu live CD (although the live CD I had handy was 32-bit, and the install is 64-bit [I installed from the alternate disk, which doesn't have the live boot option].  Also, the live CD couldn't mount any of the HD partitions, as they're all encrypted volumes and it apparently doesn't have the drivers in the live boot image.)  *[Update: it later appeared that this was a fluke, as a second trial of this experiment had the machine spontaneous turn off after about 4 hours.]*

Thermally, the system seems fine.  There are many large fans in the case.  I've never seen the CPU temperature above 38 C, the GPU runs about 44 C, both well below any alarm threshold.  The hardware is all new (which doesn't mean it's not broken, of course...)  I can't find anything in any of the logs that indicates any fault the kernel or drivers are detecting.  I've run memtest from the install CD and found no problems with the RAM.

I'd still believe it was hardware, except that it seems stable when booted from the CD.  I'm going to try the 64-bit live CD overnight, to test that again.

I can find no pattern that would point to a software issue--no error message in the logs, no common thread.  It's shut itself off when I've had a dozen apps open, or none.  Once it shut off before it finished booting, while it was running fsck on a 1 TB volume (as many times as I've rebooted in the past 4 days, I've had to wait through several of those.)  There was an update not long before the symptoms appeared, but I looked at dkpg's log and libnewt and python-newt hardly seem likely to trigger massive system instability, even if the updates were buggy.

I've searched the forums and google and found nothing resembling these symptoms.  Any clues as to whether it's a hardware or software problem, or where else to look for symptoms, or what to replace first, would be greatly appreciated.

The system is 
Ubuntu 9.04 64-bit, ext3 in encrypted volumes on top of software RAID 1 (everything except a small boot partition is encrypted)
Dual core Pentium (E8500) CPU, aftermarket Zalman CPU fan
Gigabyte EP45C-UD3C motherboard
4 GB DDR3 RAM
Nvidia 9500GT (EVGA card, 512 MB)
WD Caviar Black SATA hard drives, 2x 640GB (RAID 1), 3x 1TB (w/o RAID)
2 DVD drives on IDE
550W power supply (Purepower)
APC UPS (USB control cable no longer connected to PC)

---

### Post by brian mcgee on 2009-09-29
hmm, could you post the output of the following 3 commands:

```
cat /var/log/syslog
cat /var/log/syslog.0
cat /var/log/messages
```

Output of dmesg might suffice.

---

### Post by n8hfi on 2009-09-29
> **brian mcgee said:**
> hmm, could you post the output of the following 3 commands:

```
cat /var/log/syslog
cat /var/log/syslog.0
cat /var/log/messages
```

Output of dmesg might suffice.

Well, no, not here, they're too long.  But I can post them elsewhere and put links here:
[LIST]
[*][cat /var/log/syslog]("http://cardfaq.org/tmp/syslog.txt")
[*][cat /var/log/syslog.0]("http://cardfaq.org/tmp/syslog.0.txt")
[*][cat /var/log/messages]("http://cardfaq.org/tmp/messages.txt")
[*][dmesg output]("http://cardfaq.org/tmp/dmesg.txt")
[/LIST]

The history prior to these logs was (most recent first)
- shutdown while sitting at login prompt (gdm), had been up about half or three quarters of an hour
- shutdown while running fsck during boot
- shutdown while logged in, but no application started

---

### Post by Yellow Pasque on 2009-09-29
Double-check the exact model of your motherboard and see if you're running the latest BIOS. [http://www.gigabyte.com.tw/Support/Motherboard/BIOS_List.aspx?CPUType=Socket+775](http://www.gigabyte.com.tw/Support/Motherboard/BIOS_List.aspx?CPUType=Socket+775)

---

### Post by n8hfi on 2009-09-29
> **Temüjin said:**
> Double-check the exact model of your motherboard and see if you're running the latest BIOS. [http://www.gigabyte.com.tw/Support/Motherboard/BIOS_List.aspx?CPUType=Socket+775](http://www.gigabyte.com.tw/Support/Motherboard/BIOS_List.aspx?CPUType=Socket+775)

I'm running BIOS F4, the latest non-beta BIOS available.  According to Gigabyte, this CPU has been supported since F2.

---

### Post by Arup on 2009-09-29
Try turning off power management in BIOS if its On and then see if the issue goes away. Something is putting your system to sleep or giving the shut down command. Usually thermal management does that in BIOS if temps are exceeded beyond safety threshold. However in your case, all the temps look fine to me.

---

### Post by n8hfi on 2009-09-29
> **Arup said:**
> Try turning off power management in BIOS if its On and then see if the issue goes away. 

A good suggestion, but I've already tried that.  Made no difference in the symptoms.

I ran another experiment today, with the machine booted on the 64-bit live CD (previously, I tried the running the 32-bit version and the machine had stayed up overnight.)  But it shut down sometime during the day (don't know when, I was at work...)  Maybe running the 32-bit live CD overnight was a fluke.  I'm trying that one again now, to see.

But I'm really running out of reasons to believe this is software related (and if it's not, this whole thread's probably in the wrong category.)  I do wish I could pick up some clue from the logs about which piece of hardware might be acting up.  I guess the next step is to start disconnecting pieces...

---

### Post by bford16 on 2009-09-29
The thing that doesn't fit is that you see a shutdown prompt.  But what if you had a bad power switch, or somehow had the wires connected wrong in the case. In other words, I am suggesting that the power button is somehow pressing itself, causing a shutown...

---

### Post by brian mcgee on 2009-09-29
> **bford16 said:**
> The thing that doesn't fit is that you see a shutdown prompt.  But what if you had a bad power switch, or somehow had the wires connected wrong in the case. In other words, I am suggesting that the power button is somehow pressing itself, causing a shutown...

I've seen this once, and it would explain why syslog is silent about shutdowns (power button held down for 4 seconds usually immediately powers off the machine, so no chance for the OS to do anything gracefully). Perhaps try telling the BIOS to do nothing when the power button is held down. Or, disconnect the front panel power switch from the mainboard.

---

### Post by n8hfi on 2009-09-30
> **brian mcgee said:**
> I've seen this once, and it would explain why syslog is silent about shutdowns (power button held down for 4 seconds usually immediately powers off the machine, so no chance for the OS to do anything gracefully). Perhaps try telling the BIOS to do nothing when the power button is held down. Or, disconnect the front panel power switch from the mainboard.

A bad power switch occurred to me, although it didn't seem likely--a switch is hardly the most complicated part in the computer, and this kind of intermittent flakiness didn't seem a likely failure mode for this switch.  But the BIOS has two settings for power switch behaviour: turn off immediately, or hold down for 4 seconds to turn off (there's no BIOS setting to ignore it completely.)  I've already tried both of these (I was think the 4 second option might "de-bounce" a flaky switch) with no effect.  I hadn't tried disconnecting it, because the system won't turn on without it--the motherboard's looking for a momentary short across those pins to turn on.

But you've inspired me, so my current experiment is to turn the system on normally, then pull the power switch connector off the motherboard (and the reset switch also.)  So I currently have the system running with the power switch and the reset switch not connected to the motherboard, and we'll see what happens...

*Edit, 20 hours later: The machine hasn't shut down yet.  Given the intermittent nature of the problem, I'm not ready to call it proven, but it certaionly seems likely at this point that the power switch is indeed the culprit.*

---

### Post by Arup on 2009-09-30
Also try swapping the PSU.

---

### Post by brian mcgee on 2009-10-01
> **n8hfi said:**
> I hadn't tried disconnecting it, because the system won't turn on without it--the motherboard's looking for a momentary short across those pins to turn on.
...
*Edit, 20 hours later: The machine hasn't shut down yet.  Given the intermittent nature of the problem, I'm not ready to call it proven, but it certaionly seems likely at this point that the power switch is indeed the culprit.*

Glad to hear it's going well so far. On a fun note, you can boot your computer with a screwdriver or anything else that's metal. Basically, just make sure the two power switch pins connect for a moment. :)

I almost suggested the same as Arup (to replace the PSU), but did not since you see the shutdown dialog...

---

### Post by bcschmerker on 2009-10-01
I see that ye were able to solve this problem in less time than it took me.  From May to August 2009, I ran an Elitegroup GeForce6100SM-M system board with all-nVIDIA hardware (nForce405 chipset) around an AMD Athlon X2 5600+; I had constant problems with uncommanded shutdowns at the time (witk Kernel 2.6.24-23-rt, sometimes it didn't even get through booting when it turned itself off).  No such trouble with a Gigabyte MA78GM-S2HP, installed August 2009, which packs all-AMD hardware (780G chipset, ATI Radeon HD 3200 GPU), using the same CPU.  Unfortunately, nVIDIA has not cooperated with the open-source community, so I would not be surprised if some critical bug were introduced in reverse-engineering the nForce drivers in an attempt to get a working LinUX Kernel for nForce chipsets and the CPUs around which they are designed; no such problem with Advance Micro Devices to date, excepting the Radeon HD (for which AMD provides the FGLRX software, which has given me no core headaches to date). ):P

---

### Post by empty_spaces on 2009-10-01
> **bcschmerker said:**
> I see that ye were able to solve this problem in less time than it took me.  From May to August 2009, I ran an Elitegroup GeForce6100SM-M system board with all-nVIDIA hardware (nForce405 chipset) around an AMD Athlon X2 5600+; I had constant problems with uncommanded shutdowns at the time (witk Kernel 2.6.24-23-rt, sometimes it didn't even get through booting when it turned itself off).  No such trouble with a Gigabyte MA78GM-S2HP, installed August 2009, which packs all-AMD hardware (780G chipset, ATI Radeon HD 3200 GPU), using the same CPU.  Unfortunately, nVIDIA has not cooperated with the open-source community, so I would not be surprised if some critical bug were introduced in reverse-engineering the nForce drivers in an attempt to get a working LinUX Kernel for nForce chipsets and the CPUs around which they are designed; no such problem with Advance Micro Devices to date, excepting the Radeon HD (for which AMD provides the FGLRX software, which has given me no core headaches to date). ):P

That is such a coincidence. I had the exact same board (Elitegroup GeForce6100SM-M) and an AMD Athlon X2 4000+, which kept shutting down on me (no messages, just an instant power off). The RAM, PSU, CPU temps, all checked out OK. Finally, 3 weeks ago,  I just replaced the board with an ASUS and - no more power offs.

---

### Post by bgiannes on 2009-10-01
had the same problem, ramdom restarts.

The memory was bad, (as per mem check) i exchanged it.  

but it was still rebooting, (just not as often)

For me i had a "cheap" 650 Watt PS, that was not providing the ~400 watts my PC MoBo needed (all of the time), after changing the PS everything is fixed.  The PS was only 1 month old. I changed it for a hi end 450Watt.  

I went w/ a 450, as per this [http://educations.newegg.com/tool/psucalc/index.html](http://educations.newegg.com/tool/psucalc/index.html) "power supply calculator"  What PS do you have?

Looking back, when the PC was under hi loads, with all disks going (i have a Raid1 array, and another Two 1TB HDs) or gaming, or watching HD was when the PC would restart most.

---

### Post by n8hfi on 2009-10-02
> **brian mcgee said:**
> Glad to hear it's going well so far. On a fun note, you can boot your computer with a screwdriver or anything else that's metal. Basically, just make sure the two power switch pins connect for a moment. :)

64 hours up-time now... I'm convinced the power switch is the culprit.
I now have a special "turn computer on" tool (a jumper block clamped in a hemostat) to momentarily short the motherboard pins :).

The switch (and the case it came with, an Antec 902) is brand new and still under warranty, but it's going to be a pain.  Instead of replacing one part, I'll have to take all apart.  It'll be like replacing *everything*.  Maybe I can talk Antec into just sending me a new switch panel...

> **brian mcgee said:**
> I almost suggested the same as Arup (to replace the PSU), but did not since you see the shutdown dialog...

I had gone so far as to pick out a new PSU and put it on a wish list at Newegg, but I was reluctant to throw money at the problem without a better diagnosis.  I did pull an old one from another computer, but it was of uncertain capacity and had no SATA power connectors, so I was going to need to scrounge adapters before I could try it.  Didn't come to that after all.

> **bgiannes said:**
> had the same problem, ramdom restarts.
For me i had a "cheap" 650 Watt PS... I changed it for a hi end 450Watt.  
I went w/ a 450, as per this [http://educations.newegg.com/tool/psucalc/index.html](http://educations.newegg.com/tool/psucalc/index.html) "power supply calculator"  What PS do you have?


I have a "not cheap" 560W.  Newegg's calculator tells me 306W (most of the components were chosen with power consumption in mind; I have multiple drives and calculated a slightly higher number if all the platters were spinning.  So I was pretty confident there was enough power, although the possibility that the 12V load wasn't balanced across PS rails did cross my mind.

> **bgiannes said:**
> Looking back, when the PC was under hi loads, with all disks going (i have a Raid1 array, and another Two 1TB HDs) or gaming, or watching HD was when the PC would restart most.

No, it would shutdown with no load, drives spun down and no user logged in.  It definitely wasn't load dependent.  (My configuration is similar to yours, 2x640GB Raid-1 for / and /home, 3x1TB for raw audio/video, &c.)


Thanks to all for your help and suggestions.

---

### Post by Arup on 2009-10-02
If you have a Antec case with a faulty power switch, you need to return the entire case for replacement, real pain in the neck but you have to do it.

---

### Post by brian mcgee on 2009-10-03
> **n8hfi said:**
> Thanks to all for your help and suggestions.

No problem. Good luck with Antec. :)

---

