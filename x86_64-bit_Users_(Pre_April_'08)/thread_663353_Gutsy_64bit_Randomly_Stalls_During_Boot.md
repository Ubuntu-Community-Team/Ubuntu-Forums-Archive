---
title: "Gutsy 64bit Randomly Stalls During Boot"
date: 2008-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by JayBee808 on 2008-01-10
I've got two different 7.10 installations on an Intel P35 quad core2 (q6600) with a geforce 8800gts.  They both will randomly stall for several minutes during boot-up after this line:

io scheduler cfq registered (default)

The keyboard and other USB devices will go dark, and the computer appears to be frozen for a couple minutes.  Then keyboard, mouse, etc. will light up, and after a few seconds the boot messages will start flying by, and the system starts fine.

I checked the /var/logs/dmesg file and the next line to appear after the stall is:

Boot video device is 0000:01:00.0

The video device is an EVGA geforce 8800gts 640mb PCI Express card.

This appears to be totally random.  It doesn't matter if the PC is restarting or powered off, sometimes it stalls, the rest of the time it boots in about 20 seconds.  I would like to get this fixed, it is frustrating not knowing what to expect when I turn the PC on or reboot.  Anyone have the same problem, or advice?

---

### Post by Yellow Pasque on 2008-01-10
The only suggestion I can make is to make sure your video card is seated properly. Remove it and push that sucker in HARD. If your PCIe slot has a retaining clip, it should lock into place by itself (without you touching it).

Good luck.

---

### Post by Bokonon on 2008-01-10
Don't overdo it.  Forcing electronic components into slots can have some very undesired consequences.  

I got very lucky when I jammed a screw driver into the motherboard while using it to 'force' a north bridge fan mount.   I gouged the surface, but apparently no damage was done (crosses fingers).  

I also saw blue light and smoke when I slipped while putting in a mounting screw on a component while the system was running.  I was simply too lazy or rushed to shut the system down properly.  That was really scary.

Go slowly and deliberately and if you get frustrated with a component, best to take a break rather than breaking some component.

---

### Post by JayBee808 on 2008-01-11
Hi,

Thanks for the suggestion.  I will try and reseat the card after work tonight.  The case has several "layers" to dig through to get to the video card, so it will take a little while to disassemble.  This is the first PCI-express video card I have installed, it didn't really pop in when I installed it, but the clip did lock.

This machine also dual-boots into XP pro, and I have never had any hangs or video troubles with that.  The stall only occurs when booting Ubuntu.

---

### Post by JayBee808 on 2008-01-11
> **Bokonon said:**
> best to take a break rather than breaking some component.
 Yeah, especially at the price these components go for!

---

### Post by JayBee808 on 2008-03-04
After tearing the machine apart with no success, I have discovered that this is being caused by a BIOS setting.  I disabled the "Enable Legacy USB" setting, and the computer no longer stalls for a long period of time.  Occasionally it will pause for a second after that line "io scheduler cfq registered (default)", but then it will quickly move on.  With Legacy USB enabled it would sit there for 3-5 minutes.  The hang would come right after all the lights on USB devices flickered on and off, then it would freeze, and eventually come back with all devices lighting up again.

This had also started to happen when booting Windows XP, but Windows wouldn't ever get past it.  It would permanently freeze.

I am still curious why the machine pauses only once in while when checking USB devices, and not every time.  I will settle for it though, a 30 second boot is much better than 5 minutes.

I hope this helps someone else with this problem.  The motherboard is a Gigabyte P35-DQ6.

---

