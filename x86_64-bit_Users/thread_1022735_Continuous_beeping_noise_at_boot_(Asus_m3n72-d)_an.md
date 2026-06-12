---
title: "Continuous beeping noise at boot (Asus m3n72-d) and sound problems (Realtec ALC1200)"
date: 2008-12-27
forum: x86 64-bit Users
---

### Post by ggv6 on 2008-12-27
Hi

I have a system with Asus m2n73-d, AMD phenom quad 2.6 and 8gb ram.

Every other time when I boot the system I get the errors

ACPI expecting a reference package element found 0
USB device 1-4 not accepting error -62
Unable to enumerate USB device on port 4.

The system starts beeping continuously. If I leave it to boot it starts fine without a problem but the beeping noise continues. If I reboot it goes away or may do exactly the same. Its not possible to reproduce every time but happens about 50% of the time. It does not seem to always go away after a cold boot.

Also another problem I have is sound. It uses Realtek ALC1200 8 which is always detected on the pci bus but alsa does not detect it. I went through the forums and tries different things and get it to work sometimes but this again is random. Somehow I believe that both problems are related and have to do with how the BIOS initialises the hardware.

Has anyone experienced similar problems and has any ideas on how to debug or fix these?

Thanks

---

### Post by steveneddy on 2008-12-27
From this website:

[http://www.bioscentral.com/beepcodes/awardbeep.htm](http://www.bioscentral.com/beepcodes/awardbeep.htm)

Looks like either bad or poorly seated memory.

Try turning off and unplugging your PC and pulling the memory out and reseating it back onto the MB.

Then plug in the PC and restart and post back.

Also while you are in there wiggle the CPU cooler just to seat it a little better.

EDIT:

I also might add that with this much RAM that the RAM sticks should all be the same brand and the same size for optimum performance.

---

### Post by ggv6 on 2008-12-27
I have check all the hardware that sits properly and also tried removing ram and leaving only 2 or 4 gb and still get the same problems. If I do not start ubuntu and try windows then everything is fine.

---

### Post by steveneddy on 2008-12-27
> **ggv6 said:**
> I have check all the hardware that sits properly and also tried removing ram and leaving only 2 or 4 gb and still get the same problems. If I do not start ubuntu and try windows then everything is fine.

I would reinstall Ubuntu from a known good disc.

Only takes 20 minutes.

Maybe as a test make another user, make this user an admin also, and boot into this user to test if the symptoms are still the same.

If so I would reinstall if Windows seems to work well and Ubuntu not.

Does the same thing occur when running from the Live CD?

---

### Post by ggv6 on 2008-12-28
hi

same problem with live cd. I tried different copy of cd and reinstalled and same problems again. So I installed gentoo AMD64 from scratch and everything works just fine. I am not sure if the ubuntu kernel was compiled with something incompatible.

---

### Post by steveneddy on 2008-12-28
> **ggv6 said:**
> hi

same problem with live cd. I tried different copy of cd and reinstalled and same problems again. So I installed gentoo AMD64 from scratch and everything works just fine. I am not sure if the ubuntu kernel was compiled with something incompatible.

Interesting - maybe a hardware incompatibility.

Is this solved?

---

### Post by ggv6 on 2008-12-30
I could not solve it so I had to move this pc to gentoo for now.
I am sure if I rebuild the kernel at ubuntu with same options would probably work fine but I would have to do it every time I get an update and ubuntu is not friendly when it comes to this.

Thanks for you replies

---

### Post by miraclemaxim on 2009-01-11
I have the EXACT same problem with my evga 780i board (x3350 cpu).  I also get the usb errors and have 8gb of ram.  Sometimes it'll boot, and the system beeps will start and never stop.  Other times they never start and then sometimes they start and then stop as kde starts booting.

This didn't happen in hardy, but only when I upgraded to Intrepid.

---

### Post by Yellow Pasque on 2009-01-11
The common denominator seems to be an nvidia chipset. I suspect that the problem will be solved by either updating the BIOS and/or using a newer kernel (though using a newer probably kernel isn't feasible for most users).

If the issue doesn't affect usability and you just want to shut off the PC speaker, see: [http://www.thinkwiki.org/wiki/How_to_disable_the_pc_speaker_(beep](http://www.thinkwiki.org/wiki/How_to_disable_the_pc_speaker_(beep)!)

---

### Post by Mike Bailey on 2009-01-12
Similar problem with ThinkPad SL500, Ubuntu 8.10 64 bit, Intel ICH9 (PM45) Express Chipset, Nvidia GeForce 9300M GS graphics, Intel Core 2 Duo 8600 cpu, 4 gig. ram. Dual boot with Windows XP.  Often when doing a warm reboot from Windows XP and/or a logout/login from Ubuntu, there's a continuous speaker beeping.  PC speaker can't be disabled in the BIOS, but even then this would just be masking the problem.  I've also experienced the same beeping problem when uninstalling/reinstalling the Nvidia restricted graphics drivers.

There does not seem to be a consistency other than when it happens, it's at full volume.  Sometimes it's resolved by shutting down completely and doing a cold boot.  It almost seems as if it might be a timing issue.  It happens less often once I removed the 'quiet' option from the GRUB line I boot from so that there's a brief console message or two before initializing the graphical interface.  This is not consistent, but did reduce the occurrence ~somewhat.

Mike

---

### Post by BlackDex on 2009-01-12
Hello there,

I have the same problem with an Acer Aspire X3200.
I updated the BIOS, no luck.
I am trying to check some other stuff to fix it.
But it doesn't always happen strange enough.

I Saw a post on a Fedora forum, about disableing ACPI with acpi-off within grub. But that is no a solution.

EDIT:
The paramters where: "acpi=off apm=on apm=power-off"

---

### Post by BlackDex on 2009-01-12
It really is frustrating.
I can't get it to work.

Those beeps can't be shutoff, unless there is some way of adding an option to the grub parameters?

I Don't want to install an other OS then Ubuntu, but it looks like i don't have a choice :( .

---

### Post by BlackDex on 2009-01-14
Well the only way i can fix this is by adding:
"acpi=off noacpi" to the kernel boot params.

The only big down-side of this, is that the pc won't fully shutdown on it's own.
I need to manualy push the power button.

Is there any fix for this?

---

### Post by BlackDex on 2009-01-14
I finally fixed this problem after a long long discussion on freenode #kernel.

The problem occured arround: "ACPI: Expecting a [Reference] package element, found type 0"

Here it loaded the thermal and fan modules.
After adding the two modules to the blacklist, and executed the following command:
```
sudo update-initramfs -k all -c
```

All was fixed.
It seems this for some reason triggered the ACPI part of the BIOS to crash or something i think.

Also, i had USB errors, they are gone also.

Anyway it is fixed now, with many thanks to enouf.

---

### Post by beetlejuice_masterson on 2009-01-31
I'm having the same problem -- my pc seems to beep continuously on boot about 1/2 the time.

I ran a sudo modprobe -l | grep "acpi"

Are these the two modules that I need to blacklist?  Won't this have an adverse affect on my system (i.e. overheating???)

/lib/modules/2.6.27-9-generic/kernel/drivers/acpi/fan.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/acpi/thermal.ko

Any help/suggestions are appreciated!

---

### Post by BlackDex on 2009-02-02
Most modern bioses control the fan there selfs, and it is good enough.
It realy fixed my problems.
Just try it out.

---

### Post by beetlejuice_masterson on 2009-02-03
Actually i found a less elegant but also less invasive method...

I dual boot vista and if I wait until the grub countdown reaches "7" before pressing enter to boot ubuntu 8.10 (x64) it works every time.  Open sesame.

---

### Post by BlackDex on 2009-02-04
If that is the case it seems like an timing issue.
Like the BIOS still needs to load stuff or something.

---

### Post by Ben Alex on 2009-05-07
I had the same problem as many people on this thread, which was resolved simply through executing the following command. I also had a green monitor at boot time in addition to the endless beeping. Thanks BlackDex!

> **BlackDex said:**
> 
```
sudo update-initramfs -k all -c
```


---

