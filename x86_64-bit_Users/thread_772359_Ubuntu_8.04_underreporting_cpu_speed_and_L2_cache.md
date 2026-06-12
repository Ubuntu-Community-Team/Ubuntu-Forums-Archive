---
title: "Ubuntu 8.04 underreporting cpu speed and L2 cache"
date: 2008-04-28
forum: x86 64-bit Users
---

### Post by dlmoak on 2008-04-28
I'm a new user with a new Shuttle SG31G2 desktop and a Dual Core e8400 3 Gig processor.  Install went fine.  Everything is working.  lshw reports the cpu as being 3 Gig but reports the speed as 266.  Also indicates that the L2 cache is disabled.

cpuinfo sees the cpu and shows the cache size.

Does lshw report what the cpu is doing at that moment or the cpui's general capabilities?  If the former, then the chip may actually be running at 266 when I run lshw, but would the chip actually disable the L2 cache if it didn't think it needed it?

I saw nothing in the cmos that indicated that anything was being disabled\enabled for L2 cache.

Is there something I can run that will sufficiently load the cpu to see if it is stepping down?

---

### Post by Half-Left on 2008-04-28
cpuinfo should be the correct info, if your running with no L2 cache and 266 you will notice things being slow.

---

### Post by Yellow Pasque on 2008-04-28
RIght click on empty space in the bar (we call it a panel in Gnome) at the top of your screen. Select "Add to Panel". Look for the CPU Speed Monitoring Applet. Click that and OK. Do some tasks like loading Firefox and moving windows around.

Are you sure the speed is being reported as 266 and not the FSB? I don't think Intel's chips are capable of running that low. The last time I checked, the lowest Core2-based chips could run was 1.2GHz (6 * 200) with Speedstep.

---

### Post by dlmoak on 2008-04-28
> **Temüjin said:**
> RIght click on empty space in the bar (we call it a panel in Gnome) at the top of your screen. Select "Add to Panel". Look for the CPU Speed Monitoring Applet. Click that and OK. Do some tasks like loading Firefox and moving windows around.



I could only find the CPU Frequency Scaling Monitor.  It shows the cpu running at 2.40 gigs and says it is 100% utilized.

Here is the relevant portion of lshw with highlights in red:
description: Desktop Computer
    product: SG31
    vendor: Shuttle Inc
    version: V10
    serial: 0
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=0 uuid=01020907-0301-0103-0807-060504030201
  *-core
       description: Motherboard
       product: FG31
       vendor: Shuttle Inc
       physical id: 0
       version: V10
       serial: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (01/18/2008)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     **[COLOR="Red"]E8400  @ 3.00GHz[/COLOR]**
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: Intel(R)
          slot: Socket 775
          size: 2394MHz
          capacity: 4GHz
          width: 64 bits
         **[COLOR="Red"] clock: 266MHz[/COLOR]**
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall x86-64 constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
       **[COLOR="Red"] *-cache:1 DISABLED[/COLOR]**
             description: L2 cache
             physical id: c
             slot: External Cache
             capabilities: synchronous external write-back

---

### Post by Yellow Pasque on 2008-04-28
Hmm. It looks like the BIOS is incompatible with the 333MHz FSB that the chip should run and is setting it to 266MHz. It's recognizing the CPU and its mulitplier (9 * 266 = 2.4GHz), but not the 333MHz FSB or the cache. You need to update the BIOS.
[http://global.shuttle.com/download03.jsp?PI=646](http://global.shuttle.com/download03.jsp?PI=646)

Actually, it looks like you're running the latest BIOS. Do you have the option of manually raising your FSB clock to 333 MHz?

---

### Post by restamp on 2008-04-28
I don't have the problem of underreported CPU speed, but I have noticed a difference between CPU speed behavior on Feisty, and what it is now on Hardy.  I run two instantiations of the CPU Frequency Scaling Monitor on my panel, one set to look at CPU0 and the other set to look at CPU1.  On Feisty, they would operate fairly independently.  On Hardy, they always appear to operate in lock step.

On an otherwise quiescent machine, from a terminal I can put the shell in an infinite loop.  On Feisty, one CPU would go to full speed while the other would remain at the lower speed.  On Hardy, both seem to go full power speed together.  Furthermore, if I force either of the CPUs to full power through the Frequency Scaling Monitor on Hardy, the change affects both CPUs.

Can anyone shed some light on whether there has been a change in the way Ubuntu handles CPU frequency scaling in either Gutsy or Hardy, or is this simply a bug?

An aside:  One problem I had on Feisty in this area that I have not noticed on Hardy is that its frequency scaling ceased to work correctly (became quite flaky) after Feisty was suspended and then resumed.  Hardy seems to handle this much better.

---

### Post by Yellow Pasque on 2008-04-28
restamp, what CPU do you have? I doubt the cores were running at two different speeds. It sounds more like a delayed report from the sensor software on the second core.

---

### Post by dlmoak on 2008-04-28
> **Temüjin said:**
> 
Actually, it looks like you're running the latest BIOS. Do you have the option of manually raising your FSB clock to 333 MHz?

I came to the same conclusion.  The shuttle site indicates that there was an update to the BIOS I have (1/18/2008) on 2/5/2008.

1.Fixed CPU Default frequency show & OC function incorrect.
2.Fixed can't detect USB 2.0 device when use WIN2000 OS.

Looks like this would fix my problem.  I'm having trouble figuring out how to make a DOS bootable CD that a SATA drive can boot from.  I have only the HDD and the CD/DVD in the machine and they are both SATA.  I've downloaded the BIOS and the AWDFLASH.EXE from the Shuttle site. 

I can only change the voltage on the FSB in my CMOS as far as I can tell.

---

### Post by Yellow Pasque on 2008-04-28
dlmoak, you wouldn't be running DDR2-533 by any chance, would you?

---

### Post by restamp on 2008-04-28
> **Temüjin said:**
> restamp, what CPU do you have? I doubt the cores were running at two different speeds. It sounds more like a delayed report from the sensor software on the second core.

Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz

I wondered about the ability of the hardware to be able to control the CPUs independently.  I would think that would be a bus designer's nightmare.  However, it sure looked to be the case under Feisty.  If you can confirm that that is not possible in the E6750, then I'll have to believe it was a reporting quirk, but I could *cat /proc/cpuinfo* and see 1998.00 Mhz on one cpu, and 2664.00 Mhz on the other.  Indeed, sometimes I could watch a single compute bound process seemingly swap back and forth between cores, with one core, and then the other, but never both simultaneously, going to full speed.

---

### Post by dlmoak on 2008-04-29
> **Temüjin said:**
> dlmoak, you wouldn't be running DDR2-533 by any chance, would you?

Nope - DDR2-800.  BTW, the frequency in the BIOS was not originally at 9 - it was originally set at 6.  I changed it when I was checking things out in the BIOS.

I have made a bootable USB Zip disk, which seems to be supported as a boot device in my BIOS.  I'll try flashing the BIOS sometime tonight after I get home from work.  Unfortunately, my bosses don't think its as much fun for me to stay home and play with my new computer as I do :)

I appreciate all the input.  Hopefully the flash will fix things.  I'll let you know.  In the meantime if there are any other suggestions I'd be happy to hear them.

---

### Post by dlmoak on 2008-04-30
I didn't actually have time to flash the BIOS last night so no progress to report.  I found an old IDE CD-Drive that I can connect and boot from as soon as I make a disk.  Hopefully more news tomorrow.

---

### Post by dlmoak on 2008-04-30
Well I don't know why or how, but the clock speed is now being reported accurately.  Here is the portion of lshw:

     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: Intel(R)
          slot: Socket 775
          size: [COLOR="Red"]2997MHz[/COLOR]
          capacity: 4GHz
          width: 64 bits
          clock:[COLOR="Red"] 333MHz[/COLOR]

It still reports the L2 cache as disabled so I may go ahead and flash the BIOS, but for now I'll leave well enough alone.  AFAIK I did nothing to correct the situation.

:confused:

Thanks again for your help!

---

