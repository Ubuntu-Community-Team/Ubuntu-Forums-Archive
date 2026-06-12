---
title: "64bit Edgy install problems"
date: 2007-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Shinobi_no_mono on 2007-03-15
Trying to install Edgy 64bit on my new box.

Few seconds after choosing "Start or install Ubuntu" I get hung-up where the Ubuntu logo is gray with 10 vertical gray lines under the logo, thats it, just hangs, zilch.

I put in 6.06 and it booted up after a while and with some errors listed.

I'd like to do a fresh install with Edgy.

Hardware is:
AMD Athlon64x2 5200+ Windsor 2.6GHz
abit NF-M2 nView
Mushkin 2gb SDRAM DDR2 800 (PC2 6400)
WD Caviar RE2  WD5000YS 500GB SATA

Wondering if its a Bios setting/hardware configuration or something else.

New to Ubuntu, any help would be appreciated.

Quicker I dump MS, the better!

---

### Post by loserboy on 2007-03-15
whats your video card?

I had the same problem with my nvidia 7800 and i hear its doing the same on some other 7 or 8 series cards, there is a workaround

---

### Post by Shinobi_no_mono on 2007-03-15
> **loserboy said:**
> whats your video card?

I had the same problem with my nvidia 7800 and i hear its doing the same on some other 7 or 8 series cards, there is a workaround

None, using the onboard Nvida 6150 chipset for video.

Not a gamer so I don't need it, could always upgrade later but for now nothing.

---

### Post by loserboy on 2007-03-15
ok well i guess it could still apply, lemme find the workaround

---

### Post by loserboy on 2007-03-15
[https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

#59618 under installation, try that, if its not it it won't harm anything

---

### Post by Shinobi_no_mono on 2007-03-15
> **loserboy said:**
> [https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

#59618 under installation, try that, if its not it it won't harm anything

I tried booting up in "Safe Graphics Mode" like they said, still hung-up on the gray logo.

Maybe a hammer to the mobo would work? :lolflag:

---

### Post by Kilz on 2007-03-15
You could also try the Alternate install CD. It isnt as pretty, but for 64bit it offers a greater chance of success of install.

---

### Post by s1ptome on 2007-03-15
hi

on my laptop, i had to use another workaround: try to boot with some additionnal options, like "noapic" and/or "nolapic" etc... my laptop requires "noapic".
To do so, when you're on then screen where to choose start or install ubuntu, press a key (i think it's F6, but they're listed at the bottom of your screen, choose the good one ;) ) and just add your option(s) to the line that appeared, then press enter to boot.

hope this helps you,
s1ptome

---

### Post by loserboy on 2007-03-16
> **Shinobi_no_mono said:**
> I tried booting up in "Safe Graphics Mode" like they said, still hung-up on the gray logo.

Maybe a hammer to the mobo would work? :lolflag:

but did you do the whole workaround adding the parameters "Remove splash and add break=bottom."? then make sure that its using vesa?

---

### Post by Shinobi_no_mono on 2007-03-16
> **loserboy said:**
> but did you do the whole workaround adding the parameters "Remove splash and add break=bottom."? then make sure that its using vesa?

I just did that and now I get a whole bunch of text but not what this says [https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)

Something about ACPI stuff and un-able to open a rtc device, got me its all new to me.

Hell might as well type it all out by hand so you guys know what the hell it is since I haven't the foggiest.

94.839727] TCP bic registered
94.839773] NET: Registered protocol family 1
94.839810] NET: Registered protocol family 8
94.839872] NET: Registered protocol family 20
94.840283] ACPI: (supports S0 S3 S4 S5)
94.840460] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
94.840511] Freeing unused kernel memory: 188k freed
94.873684] input: AT Translated Set 2 keyboard as /class/input/input0
94.878764] Capability LSM initialized
94.897653] ACPI: Fan [FAN] (on)
94.900027] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Dev is not present [20060707]
94.900121] ACPI: Getting cpuindex for acpiid 0x1
94.901659] ACPI: Thermal Zone [THRM] (40 c)
95.124824] SCSI subsystem initialized
95.127873] libata version1.20 loaded.
95.130077] sata_nv 0000:00:0e.0: version 0.8
95.130829] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
95.130569] GSI 16 sharing vector 0xB1 and IRQ 16
95.130607] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 23 (lev low) -> IRQ 177
95.130857] PCI: Setting latency timer of device 0000:00:0e.0 to 64
95.130961] ata1: SATA max UDMA/133 cmd 0x9F0 ct1 0xBF2 bmdma 0xE000 irq 177
95.131012] ata2: SATA max UDMA/133 cmd 0x970 ct1 0xB72 bmdma 0xE008 irq 177

Ok thats what I get when I typed "break=bottom" replacing the "splash" part.

Anybody have a idea?

---

### Post by loserboy on 2007-03-19
so it never came to a prompt for you to type anything, it just freezes on the last line you have there?

---

### Post by in_flu_ence on 2007-03-19
Do you have an USB drive plug-in to your PC when you boot up? It seems to me that the bootup is at the stage of detecting hard-drives. I has a past experience where it just hang at the point it tries to detect the USB Harddisk. I don't think yours is the video card problem as yet (Not sure).

---

### Post by irish8890 on 2007-03-19
I am still having some trouble installing Ubuntu on my AMD64 3700+ system.  Here are a couple of things I have tried to help alleviate the hang-ups:

- Set BIOS to no IDE DMA access
- Made PCIe block sizes smaller (dropped them to 2048 from 4096)
- Use text install mode
- Install options nodma, noapci, noapic, nofb
- Install Ubuntu on an EIDE drive.  I have had problems installing on WD SATA drives, Seagate SATA drives seem a little better (not sure if this is due to DMA or the drive buffer sizes or something else)

One of the last UK Linux magazines Linux Format or Linux Pro had an excellent article on some things to do when installation does not happen seamlessly, without hassles.

Hope this helps!

John

---

### Post by Shinobi_no_mono on 2007-03-19
I ended up installing Dapper first since my other box which is running windoze can't burn anything. So I did that and burned Edgy i386 and did a fresh install. Suffice to say I got Edgy to install, just not the 64bit version.

I'll have to look into what you all have recommended, especially since it is a SATA drive.

The video was horrible until I updated the Nvida drivers, now its fine and running in 1600x1200.

Thanks for everyone's help so far!

---

### Post by in_flu_ence on 2007-03-19
I have installed my ubuntu & kubuntu 64bit in WD SATA drives. There was not any problem for me somehow. I didn't even set any thing on my boot-up.

But i guess irish8890 has given some of the common tweaks available.

Just feel strange for u that you manage to install 32bit but not the 64bit. I didn't expect that though but I might just not know enough in this aspect.

---

