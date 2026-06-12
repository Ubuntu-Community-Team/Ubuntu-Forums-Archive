---
title: "Suspend but no resume with Hardy amd64 on HP L2000 laptop (Turion)"
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by halfmanhalfbug on 2008-05-09
Hello Ubuntus. My 64 bit Hardy 8.04 system suspends but the screen, keyboard, and wireless never wake up. In /var/log/pm-suspend.log I see the following:
```
Thu May  8 13:53:45 ICT 2008: running suspend hooks.
===== Thu May  8 13:53:45 ICT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Thu May  8 13:53:45 ICT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Thu May  8 13:53:45 ICT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Thu May  8 13:53:45 ICT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Thu May  8 13:53:46 ICT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Thu May  8 13:53:46 ICT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Thu May  8 13:53:46 ICT 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Thu May  8 13:53:48 ICT 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Thu May  8 13:53:48 ICT 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Thu May  8 13:53:48 ICT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Thu May  8 13:53:48 ICT 2008: done running suspend hooks.
Thu May  8 13:55:22 ICT 2008: running resume hooks.
===== Thu May  8 13:55:22 ICT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
cef43ac0:00cf: FEFEFEFF ILLEGAL EXTENDED X86 OPCODE!
halt_sys: file [non-UTF character], line -966517840
```
Looks like a clash between 64 bit and 32 bit somewhere in the 99video script. Does anyone else have this problem? I have googled and searched ubuntuforums but can find nothing.
The /var/log/messages shows:```

May  8 13:53:46 crash kernel: [ 3730.351177] ehci_hcd 0000:00:13.2: remove, state 4
May  8 13:53:46 crash kernel: [ 3730.351663] usb usb3: USB disconnect, address 1
May  8 13:53:46 crash kernel: [ 3730.353607] ehci_hcd 0000:00:13.2: USB bus 3 deregistered
May  8 13:53:46 crash kernel: [ 3730.354306] ACPI: PCI interrupt for device 0000:00:13.2 disabled
May  8 13:53:46 crash kernel: [ 3730.433756] ACPI: PCI interrupt for device 0000:05:00.0 disabled
May  8 13:53:46 crash kernel: [ 3730.575536] ACPI: PCI interrupt for device 0000:05:02.0 disabled
May  8 13:53:48 crash kernel: [ 3732.441651] Syncing filesystems ... done.
May  8 13:55:22 crash kernel: [ 3732.442568] Freezing user space processes ... (elapsed 0.00 seconds) done.
May  8 13:55:22 crash kernel: [ 3732.443766] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
May  8 13:55:22 crash kernel: [ 3732.538267] Suspending console(s)
May  8 13:55:22 crash kernel: [ 3732.574254] sd 0:0:0:0: [sda] Synchronizing SCSI cache
May  8 13:55:22 crash kernel: [ 3732.711019] sd 0:0:0:0: [sda] Stopping disk
May  8 13:55:22 crash kernel: [ 3733.750072] ACPI: PCI interrupt for device 0000:05:09.4 disabled
May  8 13:55:22 crash kernel: [ 3733.765736] ACPI: PCI interrupt for device 0000:05:09.3 disabled
May  8 13:55:22 crash kernel: [ 3733.797996] ACPI: PCI interrupt for device 0000:00:14.6 disabled
May  8 13:55:22 crash kernel: [ 3733.798267] ACPI: PCI interrupt for device 0000:00:14.5 disabled
May  8 13:55:22 crash kernel: [ 3733.798490] ACPI: PCI interrupt for device 0000:00:14.1 disabled
May  8 13:55:22 crash kernel: [ 3733.798643] ACPI: PCI interrupt for device 0000:00:13.1 disabled
May  8 13:55:22 crash kernel: [ 3733.798700] ACPI: PCI interrupt for device 0000:00:13.0 disabled
May  8 13:55:22 crash kernel: [ 3733.881717] Disabling non-boot CPUs ...
May  8 13:55:22 crash kernel: [    0.338068] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
May  8 13:55:22 crash kernel: [    0.359186] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
May  8 13:55:22 crash kernel: [    0.383310] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
May  8 13:55:22 crash kernel: [    0.383862] ata1.01: _GTF evaluation failed (AE 0x1001)
May  8 13:55:22 crash kernel: [    0.384479] ata2.01: _GTF evaluation failed (AE 0x1001)
May  8 13:55:22 crash kernel: [    0.384644] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
May  8 13:55:22 crash kernel: [    0.387661] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
May  8 13:55:22 crash kernel: [    0.388254] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
May  8 13:55:22 crash kernel: [    0.453299] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[c0208800-c0208fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
May  8 13:55:22 crash kernel: [    0.467199] ACPI: PCI Interrupt 0000:05:09.3[A] -> GSI 17 (level, low) -> IRQ 17
May  8 13:55:22 crash kernel: [    0.483201] ACPI: PCI Interrupt 0000:05:09.4[A] -> GSI 17 (level, low) -> IRQ 17
May  8 13:55:22 crash kernel: [    0.827542] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
May  8 13:55:22 crash kernel: [    0.827545] ata2.00: ACPI cmd ef/03:22:00:00:00:a0 filtered out
May  8 13:55:22 crash kernel: [    0.827562] ata2.00: simplex DMA is claimed by other device, disabling DMA
May  8 13:55:22 crash kernel: [    1.063390] ata2.00: configured for PIO4
May  8 13:55:22 crash kernel: [    1.182781] sd 0:0:0:0: [sda] Starting disk
May  8 13:55:22 crash kernel: [    3.426210] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
May  8 13:55:22 crash kernel: [    3.426213] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
May  8 13:55:22 crash kernel: [    3.450441] ata1.00: configured for UDMA/100
May  8 13:55:22 crash kernel: [    3.467840] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
May  8 13:55:22 crash kernel: [    3.467854] sd 0:0:0:0: [sda] Write Protect is off
May  8 13:55:22 crash kernel: [    3.467873] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  8 13:55:22 crash kernel: [    3.516940] Restarting tasks ... <6>usb 2-3: USB disconnect, address 3
May  8 13:55:22 crash kernel: [    3.566327] done.
May  8 13:55:22 crash gnome-power-manager: (broose) Resuming computer
May  8 14:00:15 crash syslogd 1.5.0#1ubuntu1: restart.
```
Resume worked fine in Feisty but now fails with the old Feisty kernel so I think it is a problem with pm-suspend rather than the kernel but I'm not sure. 
Specs:
HP L2000 with Turion processor
ATI 200M using radeon module (open source driver)
bcm4318 using bcm43xx module, usb using ehci-hcd and ohci_hcd modules
2.6.24-16-generic #1 SMP 
I appreciate any help with this and thanks in advance.
(And is there a better way to reboot the computer than holding down the power key for 6 seconds? The keyboard is not responsive to the usual ctl-alt-bkspc or ctl-alt-f1 etc. and not even the caps lock light responds.)
-hmhb

---

### Post by PmDematagoda on 2008-05-09
Actually it is very likely that it is a kernel issue since kernel 2.6.24 is very unreliable with both suspend and hibernation, kernel 2.6.25 has this fixed and you can get suspend and hibernation back if you either compile the 2.6.25 kernel or if you use a distro that uses kernel 2.6.25 such as Fedora 9.

---

### Post by halfmanhalfbug on 2008-05-09
Thanks PmDematagoda. I've found additional problems with DVD playback, Evolution, npviewer/Firefox beta3 in Hardy so I'll be downgrading back to Gutsy. The Heron is a turkey on my laptop.

---

### Post by halfmanhalfbug on 2008-05-10
I found that "/etc/acpi/sleep.sh force" works. The laptop resumes OK. See the following link for more info:
[http://ubuntuforums.org/showthread.php?t=782782]("http://ubuntuforums.org/showthread.php?t=782782")
I cannot get pm-suspend to resume with either the "radeon" open source driver or the "fglrx" proprietary driver.
And a note to all who's dvd players (mplayer, xine-ui, etc) cannot find the dvd, use preferences in the applications to point them to "/dev/dvd1" (or other number...check your /dev/ directory) rather than the default "/dev/dvd", which doesn't seem to exist in Hardy.

---

### Post by halfmanhalfbug on 2008-05-11
update:
I just did a clean install of Hardy and now neither pm-suspend nor /etc/acpi/sleep.sh work. Oh well.
pm-suspend gets to "suspending console(s)" and then stops with the text still on the screen.
/etc/acpi/sleep.sh shuts off the screen but never goes further. The LED lights stay on but nobody's home...totally unresponsive.

---

### Post by PmDematagoda on 2008-05-11
halfmanhalfbug:- this is just a suggestion, but why don't you give Fedora 9 a try and see if your suspend issues are solved there?

---

### Post by halfmanhalfbug on 2008-05-12
Hi PmDematagoda. Yes, I will definitely keep my eye on Fedora 9 to see if it works with my model of laptop. I used to use Fedora a couple years ago. Fedora's big so finding the bandwidth here in Vietnam to download it will take a bit of doing...
In a side note, the Hardy upgrade created "/dev/dvd1" and "dev/cdrom1" but the clean installation created "/dev/dvd" and "/dev/cdrom". Odd.

---

### Post by PmDematagoda on 2008-05-14
Actually Fedora is the same size as Ubuntu if you get the Live/install CD from [here]("http://fedoraproject.org/en/get-fedora").

---

