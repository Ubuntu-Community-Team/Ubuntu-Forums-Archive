---
title: "Missing Memory"
date: 2007-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Calvin349 on 2007-12-15
Some system specs,

P4 3GHz (EM64T), MB=D915PBL, 4Gb ram, Ubuntu 64bit.

The system is up and running fine.  I have noticed a speed increase with 64bit.  Problem is I am only showing 2.8Gb of ram in System monitor.

Now here is the odd part.  When I go into my BIOS it tells me I have 4Gb.  When I run "sudo lshw" I get



    [I]description: Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal uuid=2FB3DFA8-F309-11D8-80AD-00E018A327D7
  *-core
       description: Motherboard
       product: D915PBL
       vendor: Intel Corporation
       physical id: 0
       version: AAC67720-204
       serial: BTBL43405648
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: CY91510A.86A.0040.2006.0926.1010 (09/26/2006)
          size: 64KB
          capacity: 448KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Genuine Intel(R) CPU processor
          serial: To Be Filled By O.E.M.
          slot: J2E1
          size: 3GHz
          capacity: 3060MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall x86-64 constant_tsc pni monitor ds_cpl cid xtpr
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 16KB
             capacity: 16KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 1MB
             capacity: 1MB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 41
          slot: System board or motherboard
          size: 4GB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: SerNum1
             slot: J6G1
             size: 1GB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: SerNum2
             slot: J6G2
             size: 1GB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 2
             serial: SerNum3
             slot: J6H1
             size: 1GB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: PartNum4
             vendor: Manufacturer4
             physical id: 3
             serial: SerNum4
             slot: J6H2
             size: 1GB
             width: 64 bits
             clock: 533MHz (1.9ns)[/I]

plus some



From all I can find if this thing was not 64 bit capable it would not be running now.

Am I just stupid or is I missin sumptin?

That second line bugs me but I do not know what it is pertaining too.

Thanks in advance,

Calvin

---

### Post by rsambuca on 2007-12-15
What do you get from

uname -m

---

### Post by Calvin349 on 2007-12-15
uname -m  returns:

*x86_64*


Thanks,

Calvin

---

### Post by rsambuca on 2007-12-15
You are definitely running 64bit.  I have no idea what that first 'width: 32 bits' means then.

---

### Post by nutz on 2007-12-15
Do you have an option in your bios for memory hole remapping? If so make sure it is enabled...

---

### Post by Calvin349 on 2007-12-16
Nope, got nothing like that in the BIOS.

Question... User memory is 2.8 Gig.  Swap is 1.6 Gig.  Normally I am used to the User mem being the total for the system.  Is that diff in Ubuntu?  I have attached a screen shot.

I should only be a noob for like the next 20 years or so. :lolflag: Thanks for your understanding.

Calvin

---

### Post by ian dobson on 2007-12-16
Hi,

You need to enable memory reallocation in you bios. 

Have a look here, your not the only one:- [http://www.itwriting.com/blog/?postid=152](http://www.itwriting.com/blog/?postid=152)

It sounds like a small bug/feature of the motherboard.

Regards
Ian Dobson

---

### Post by Calvin349 on 2007-12-17
Amaizing.  Not sure why that did not even cross my mind.  Thank you.

Calvin

---

### Post by ian dobson on 2007-12-19
Hi,

Maybe try a BIOS upgrade, in the thread listed in my post above one user reported that going to the newest bios increased his free memory (Bios only taking 800Mb rather than 1.4Gb).

Send a mail off to Intel asking about it. Thier support is actually quite good.

Regards
Ian Dobson

---

