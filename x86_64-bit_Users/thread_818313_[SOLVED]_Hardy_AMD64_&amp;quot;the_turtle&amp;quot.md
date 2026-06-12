---
title: "[SOLVED] Hardy AMD64 &amp;quot;the turtle&amp;quot;"
date: 2008-06-04
forum: x86 64-bit Users
---

### Post by fistuks on 2008-06-04
hello!

I'm using ubuntu for a while now and it absolutely gr8!
When the distro's update to hardy went out i decided to try the 64 bit version.

i have a:
amd athlon 64 x2 +3600
1gb ram
nvidia 8600gt

when i used 32bit gusty the computer never blinked.
i work on my computer with audio and video both native linux programs and windows on a virtualbox machine.

now that I've installed 64 hardy i can't listen to music on amarok while checking the mail... 
the system monitor indicates my cpu's about 30-40 % each when not running anything and jumps up to 90-100 easily when i start firefox.

any clues...?

---

### Post by jeffus_il on 2008-06-04
Try the system monitor processes tab sorted by "% cpu" descending. Run Amarok and Mail together and see which process is hogging tour Cpu. The resources tab will show you two cpu's see if both are overloaded or just one.

Are you running Ubuntu or Kubuntu?

---

### Post by fistuks on 2008-06-04
i'v tried that and could not get any clear conclusion.
the cpu usage in the resources section shows much more cpu usage from adding all of the cpu% from the process tab.

and i only gave amarok and thunderbird as an example.
the low performance is not specific to a single application.

i'm running ubuntu
i just like the kde more than the gnome players...

---

### Post by twothird on 2008-06-04
have you tried changing the way the CPU operates to Dynamic/Performance? if it's in Powersaving mode, it can get a bit slow I guess.

---

### Post by fistuks on 2008-06-04
how do i do that?

---

### Post by Nepherte on 2008-06-04
That will do you no good. In most cases this is already enabled and it works as follows: if the computer doesn't require much cpu power, the cpu will scale itself down, if the computer requires much power it will scale up again. Since it's cpu use is like 90% it will always scale itself up not reducing the cpu percentage. You'll have to find out what process/program is using so much cpu.

---

### Post by cubeist on 2008-06-04
Open a terminal, type *top* leave it somewhere you can see it and watch it while you navigate through various applications. After a few minutes you should be able to determine if it is just the applications that are slow, or if there is another process that is hogging your cpu.

My guess would be that tracker is what is slowing you down... it's the first thing I turn off on a new install...

---

### Post by fistuks on 2008-06-05
From looking at the numbers the apps are the source for the exaggerated CPU usage.
Tough on idle status it's indicators are reasonable, any action might be the simplest one in any of the open apps brings it's process resource exploits sky high.

and the biggest exploiters are:
xorg
firefox
amarok
virtualbox

and tell you the truth on my previous gusty i386 installation i used to work fluently with a vn working on a batch audio conversion process (something that my work demands all day long) amarok turned on while working on my mails and office apps.

i also have a FTP (gproftdp) for clients that i didn't dare activate since the hardy install.

---

### Post by BoredOutOfMyMind on 2008-06-05
> **cubeist said:**
> 
My guess would be that tracker is what is slowing you down... it's the first thing I turn off on a new install...

How do you turn tracker off or where to find more info. :confused:

---

### Post by studo77 on 2008-06-05
I would suggest to change audio settings to use ALSA. I saw the same problem. My sound crackled everytime the cpu had some work to do. But after changing to ALSA it is fine. Pulseaudio did take all the cpu-power on my system (amd64 3200+)

---

### Post by Jouke74 on 2008-06-05
Also with what are you checking the mail? Evolution? The evolution exchange feature also has (or had?) a bug where it would gulp-up 100% CPU usage writing a new message.

---

### Post by fistuks on 2008-06-05
I'm using thunderbird

> I would suggest to change audio settings to use ALSA. I saw the same problem. My sound crackled every time the CPU had some work to do. But after changing to ALSA it is fine. Pulseaudio did take all the cpu-power on my system (amd64 3200+)

as for pulsesudio isn't real tough on the cpu most of the time it sleeps and when it does work i never caught it using more then 1%

i don't know if it is related but - always before hardy get's overworked the mouse moves really strange

---

### Post by Jouke74 on 2008-06-05
Grasping straws here, and your videocard is not using the MESA driver accidentally?

---

### Post by fistuks on 2008-06-05
i don't really know what's MESA..
how do i check it?

i installed the restricted driver to activate compiz-fusion.

---

### Post by Jouke74 on 2008-06-05
Ok, if compiz is working with the restricted driver then you're definitively not using the MESA video driver (silly me) ](*,). Normally you could type "glxinfo" in the terminal and see the output.

Other notice from my experience: Firefox is using a lot of CPU when running Flash content. Basically because the nspluginwrapper is shifting it from 32 to 64 bit. 

I also de-installed and deactivated tracker.

Pulseaudio crackles with quite a number of programs, independent of CPU load. The easiest correction for this is indeed to switch the ouput (of the program) to ALSA usually somewhere under preference and sound settings.

You could try to put Compiz / desktop effects off for a check to see how that goes. 

The last thing you could check is your harddisk throughput (high cpu usage with reading and writing from HD), which you can check by opening a terminal and see what the commando "dmesg > CheckThisText.txt". Now open the file CheckThisText.txt and look at the harddisk / mount section for "/dev/sda" and DMA. Where /dev/sda is the partition in which you have installed Ubuntu (could also be /dev/hda/ /dev/sdb/ etc). Make sure that the DMA mode of your harddisk is on, but it is very unlikely that this is wrong.

---

### Post by fistuks on 2008-06-05
> The last thing you could check is your harddisk throughput (high cpu usage with reading and writing from HD), which you can check by opening a terminal and see what the commando "dmesg > CheckThisText.txt". Now open the file CheckThisText.txt and look at the harddisk / mount section for "/dev/sda" and DMA. Where /dev/sda is the partition in which you have installed Ubuntu (could also be /dev/hda/ /dev/sdb/ etc). Make sure that the DMA mode of your harddisk is on, but it is very unlikely that this is wrong.

i don't know exactly what is dmesg but i typed it in terminal and this is the output (there's a bunch of error stuff there but it gibberish to me...):

[   40.558637] agpgart: AGP aperture is 128M @ 0xd0000000
[   40.558677] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   40.558681] hpet0: 3 32-bit timers, 14318180 Hz
[   40.559724] AppArmor: AppArmor Filesystem Enabled
[   40.561811] Time: hpet clocksource has been installed.
[   40.561822] Switched to high resolution mode on CPU 0
[   40.561346] Switched to high resolution mode on CPU 1
[   40.573797] system 00:06: ioport range 0xc00-0xc0f has been reserved
[   40.573800] system 00:06: ioport range 0xd00-0xd0f has been reserved
[   40.573803] system 00:06: ioport range 0xa20-0xa2f has been reserved
[   40.573806] system 00:06: ioport range 0xa30-0xa3f has been reserved
[   40.573817] system 00:08: ioport range 0x3e0-0x3e7 has been reserved
[   40.573820] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   40.573822] system 00:08: ioport range 0x800-0x87f has been reserved
[   40.573825] system 00:08: ioport range 0x400-0x41f has been reserved
[   40.573830] system 00:08: iomem range 0x1c000000-0x1fffffff could not be reserved
[   40.573833] system 00:08: iomem range 0x3c000000-0x3fffffff could not be reserved
[   40.573843] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[   40.573847] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[   40.573853] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[   40.573860] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   40.573863] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
[   40.573866] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   40.573869] system 00:0f: iomem range 0x100000-0x3fffffff could not be reserved
[   40.573872] system 00:0f: iomem range 0xff780000-0xffffffff could not be reserved
[   40.574276] PCI: Bridge: 0000:00:01.0
[   40.574278]   IO window: disabled.
[   40.574282]   MEM window: disabled.
[   40.574285]   PREFETCH window: disabled.
[   40.574293] PCI: Bridge: 0000:00:02.0
[   40.574295]   IO window: c000-cfff
[   40.574300]   MEM window: f8000000-fbcfffff
[   40.574303]   PREFETCH window: 50000000-5fffffff
[   40.574308] PCI: Bridge: 0000:00:03.0
[   40.574310]   IO window: d000-dfff
[   40.574314]   MEM window: fbd00000-fbdfffff
[   40.574317]   PREFETCH window: disabled.
[   40.574322] PCI: Bridge: 0000:00:13.0
[   40.574323]   IO window: disabled.
[   40.574326]   MEM window: fbe00000-fbefffff
[   40.574329]   PREFETCH window: disabled.
[   40.574334] PCI: Bridge: 0000:00:13.1
[   40.574336]   IO window: e000-efff
[   40.574340]   MEM window: fbf00000-fbffffff
[   40.574342]   PREFETCH window: disabled.
[   40.574363] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   40.574383] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 27
[   40.574388] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   40.574401] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 31
[   40.574406] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   40.574417] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   40.574427] PCI: Setting latency timer of device 0000:00:13.1 to 64
[   40.574482] NET: Registered protocol family 2
[   40.609776] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   40.610269] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   40.611644] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   40.612285] TCP: Hash tables configured (established 131072 bind 65536)
[   40.612288] TCP reno registered
[   40.621808] checking if image is initramfs... it is
[   41.233849] Freeing initrd memory: 7856k freed
[   41.239893] audit: initializing netlink socket (disabled)
[   41.239907] audit(1212588485.292:1): initialized
[   41.241828] VFS: Disk quotas dquot_6.5.1
[   41.241906] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   41.242046] io scheduler noop registered
[   41.242048] io scheduler anticipatory registered
[   41.242050] io scheduler deadline registered
[   41.242144] io scheduler cfq registered (default)
[   41.242159] PCI: VIA PCI bridge detected. Disabling DAC.
[   41.242429] Boot video device is 0000:02:00.0
[   41.242621] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   41.242663] assign_interrupt_mode Found MSI capability
[   41.242712] Allocate Port Service[0000:00:02.0:pcie00]
[   41.242749] Allocate Port Service[0000:00:02.0:pcie02]
[   41.242830] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   41.242870] assign_interrupt_mode Found MSI capability
[   41.242915] Allocate Port Service[0000:00:03.0:pcie00]
[   41.242943] Allocate Port Service[0000:00:03.0:pcie02]
[   41.269934] Real Time Clock Driver v1.12ac
[   41.270184] hpet_acpi_add: no address or irqs in _CRS
[   41.270211] Linux agpgart interface v0.102
[   41.270214] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   41.270347] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   41.270942] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   41.271621] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   41.271688] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   41.271789] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   41.271792] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   41.271889] serio: i8042 KBD port at 0x60,0x64 irq 1
[   41.284537] mice: PS/2 mouse device common for all mice
[   41.284579] cpuidle: using governor ladder
[   41.284581] cpuidle: using governor menu
[   41.284729] NET: Registered protocol family 1
[   41.284833] registered taskstats version 1
[   41.284988]   Magic number: 12:846:130
[   41.285106]   hash matches device PNP0C02:02
[   41.285112]   hash matches device device:05
[   41.285118] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   41.285121] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   41.285123] EDD information not available.
[   41.285132] Freeing unused kernel memory: 320k freed
[   41.312720] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   42.498979] fuse init (API version 7.9)
[   42.565956] ACPI: Processor [P001] (supports 16 throttling states)
[   42.946914] SCSI subsystem initialized
[   43.001880] libata version 3.00 loaded.
[   43.001396] usbcore: registered new interface driver usbfs
[   43.001425] usbcore: registered new interface driver hub
[   43.003256] usbcore: registered new device driver usb
[   43.013852] pata_via 0000:00:0f.1: version 0.3.3
[   43.015830] scsi0 : pata_via
[   43.017989] scsi1 : pata_via
[   43.019130] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   43.019132] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   43.020311] USB Universal Host Controller Interface driver v3.0
[   43.124267] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   43.160244] Floppy drive(s): fd0 is 1.44M
[   43.176702] FDC 0 is a post-1991 82077
[   43.492263] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4167B, DL13, max UDMA/33
[   43.663841] ata2.00: configured for UDMA/33
[   43.667138] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4167B DL13 PQ: 0 ANSI: 5
[   43.667833] ahci 0000:03:00.0: version 3.0
[   43.667876] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 28 (level, low) -> IRQ 28
[   43.668039] PCI: Disallowing DAC for device 0000:03:00.0
[   44.669506] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   44.669512] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   44.669518] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   44.669691] scsi2 : ahci
[   44.670016] scsi3 : ahci
[   44.670083] ata3: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe100 irq 28
[   44.670088] ata4: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe180 irq 28
[   44.984859] ata3: SATA link down (SStatus 0 SControl 300)
[   45.304214] ata4: SATA link down (SStatus 0 SControl 300)
[   45.304782] sata_via 0000:00:0f.0: version 2.3
[   45.304813] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 21
[   45.304852] sata_via 0000:00:0f.0: routed to hard irq line 10
[   45.306981] scsi4 : sata_via
[   45.307070] scsi5 : sata_via
[   45.308309] ata5: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 21
[   45.308313] ata6: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 21
[   45.511784] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   45.675784] ata5.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   45.675789] ata5.00: 488397168 sectors, multi 16: LBA48 
[   45.683755] ata5.00: configured for UDMA/133
[   45.887508] ata6: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   45.898856] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   45.899616] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 20
[   45.899631] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   45.899960] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   45.899989] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000ac00
[   45.900131] usb usb1: configuration #1 chosen from 1 choice
[   45.900154] hub 1-0:1.0: USB hub found
[   45.900158] hub 1-0:1.0: 2 ports detected
[   46.002932] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 22
[   46.002947] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   46.002973] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   46.003001] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000a880
[   46.003110] usb usb2: configuration #1 chosen from 1 choice
[   46.003134] hub 2-0:1.0: USB hub found
[   46.003139] hub 2-0:1.0: 2 ports detected
[   46.106696] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
[   46.106710] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   46.106735] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   46.106761] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000a800
[   46.106874] usb usb3: configuration #1 chosen from 1 choice
[   46.106895] hub 3-0:1.0: USB hub found
[   46.106900] hub 3-0:1.0: 2 ports detected
[   46.214489] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 23
[   46.214503] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   46.214535] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   46.214561] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000a480
[   46.214668] usb usb4: configuration #1 chosen from 1 choice
[   46.214690] hub 4-0:1.0: USB hub found
[   46.214694] hub 4-0:1.0: 2 ports detected
[   46.246309] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   46.314447] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   46.314571] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   46.314639] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   46.314680] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf7fffc00
[   46.370046] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   46.370160] usb usb5: configuration #1 chosen from 1 choice
[   46.370184] hub 5-0:1.0: USB hub found
[   46.370190] hub 5-0:1.0: 8 ports detected
[   46.474327] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[   46.474341] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 29 (level, low) -> IRQ 29
[   46.474386] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   46.474400] ACPI: PCI interrupt for device 0000:03:00.1 disabled
[   46.476140] 8139cp 0000:05:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   46.476145] 8139cp 0000:05:09.0: Try the "8139too" driver instead.
[   46.476438] ACPI: PCI Interrupt 0000:05:07.2[B] -> GSI 18 (level, low) -> IRQ 18
[   46.526505] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fbfff800-fbffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   46.528512] 8139too Fast Ethernet driver 0.9.28
[   46.528578] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 29 (level, low) -> IRQ 29
[   46.528623] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   46.529072] scsi6 : pata_jmicron
[   46.529136] scsi7 : pata_jmicron
[   46.529159] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 29
[   46.529162] ata8: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 29
[   46.541271] Driver 'sr' needs updating - please use bus_type methods
[   46.548702] Driver 'sd' needs updating - please use bus_type methods
[   46.559293] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   46.559300] Uniform CD-ROM driver Revision: 3.20
[   46.559359] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   46.559696] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   46.559708] sd 4:0:0:0: [sda] Write Protect is off
[   46.559711] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   46.559726] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.559927] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   46.559936] sd 4:0:0:0: [sda] Write Protect is off
[   46.559939] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   46.559952] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.559957]  sda:<5>sr 1:0:0:0: Attached scsi generic sg0 type 5
[   46.565363] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   46.577636]  sda1 sda2 < sda5 sda6 >
[   46.607063] sd 4:0:0:0: [sda] Attached SCSI disk
[   46.769237] usb 1-1: device not accepting address 2, error -71
[   46.848612] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 20 (level, low) -> IRQ 20
[   46.849274] eth0: RealTek RTL8139 at 0xe400, 00:1a:92:16:e9:a2, IRQ 20
[   46.849276] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   46.914305] Attempting manual resume
[   46.914309] swsusp: Resume From Partition 8:6
[   46.914311] PM: Checking swsusp image.
[   46.913984] PM: Resume from disk failed.
[   46.955806] kjournald starting.  Commit interval 5 seconds
[   46.955304] EXT3-fs: mounted filesystem with ordered data mode.
[   47.799186] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[   47.966808] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   48.067222] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[00023c0141020632]
[   48.096140] usb 5-1: configuration #1 chosen from 1 choice
[   48.996238] usb 5-6: new high speed USB device using ehci_hcd and address 6
[   49.130384] usb 5-6: configuration #1 chosen from 1 choice
[   49.368482] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   49.540670] usb 2-1: configuration #1 chosen from 1 choice
[   49.779637] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   49.947863] usb 2-2: configuration #1 chosen from 1 choice
[   50.190786] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   50.392932] usb 3-1: configuration #1 chosen from 1 choice
[   54.910527] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   54.945298] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   55.051940] input: Power Button (FF) as /devices/virtual/input/input2
[   55.080270] ACPI: Power Button (FF) [PWRF]
[   55.080401] input: Power Button (CM) as /devices/virtual/input/input3
[   55.112196] ACPI: Power Button (CM) [PWRB]
[   55.714326] nvidia: module license 'NVIDIA' taints kernel.
[   56.302254] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4F11
[   56.302277] usbcore: registered new interface driver usblp
[   56.335125] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 24
[   56.335136] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   56.335369] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   56.480525] usbcore: registered new interface driver libusual
[   56.565929] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   56.623885] Initializing USB Mass Storage driver...
[   56.645606] scsi8 : SCSI emulation for USB Mass Storage devices
[   56.646103] usb-storage: device found at 2
[   56.646106] usb-storage: waiting for device to settle before scanning
[   56.646145] scsi9 : SCSI emulation for USB Mass Storage devices
[   56.646269] usbcore: registered new interface driver usb-storage
[   56.646273] USB Mass Storage support registered.
[   56.646276] usb-storage: device found at 6
[   56.646278] usb-storage: waiting for device to settle before scanning
[   56.821461] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   56.879972] gameport: EMU10K1 is pci0000:05:07.1/gameport0, io 0xe880, speed 1178kHz
[   56.938280] usbcore: registered new interface driver snd-usb-audio
[   56.938418] usbcore: registered new interface driver hiddev
[   56.956144] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input5
[   56.973074] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:10.1-1
[   56.973099] usbcore: registered new interface driver usbhid
[   56.973103] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   57.045812] ACPI: PCI Interrupt 0000:05:07.0[A] -> GSI 17 (level, low) -> IRQ 17
[   57.050420] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 2 ZS [2001]
[   57.084907] usbcore: registered new interface driver lmpcm_usb
[   57.084913] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   57.173295] parport_pc 00:05: reported by Plug and Play ACPI
[   57.173343] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   57.215990] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   57.216127] PCI: Setting latency timer of device 0000:04:01.0 to 64
[   57.989653] NET: Registered protocol family 17
[   60.080307] loop: module loaded
[   60.101145] lp0: using parport0 (interrupt-driven).
[   60.229192] Adding 3012148k swap on /dev/sda6.  Priority:-1 extents:1 across:3012148k
[   60.795574] EXT3 FS on sda5, internal journal
[   61.139252] NET: Registered protocol family 10
[   61.139474] lo: Disabled Privacy Extensions
[   61.635693] usb-storage: device scan complete
[   61.635794] usb-storage: device scan complete
[   61.636451] scsi 8:0:0:0: Direct-Access     WD       3200AAJ External 1.06 PQ: 0 ANSI: 0
[   61.636563] scsi 9:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[   61.640738] sd 8:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   61.641393] sd 8:0:0:0: [sdb] Write Protect is off
[   61.641396] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   61.641398] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   61.642388] sd 8:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   61.643014] sd 8:0:0:0: [sdb] Write Protect is off
[   61.643016] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   61.643018] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   61.643024]  sdb:<6>ip_tables: (C) 2000-2006 Netfilter Core Team
[   62.505081] No dock devices found.
[   62.912777] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ processors (2 cpu cores) (version 2.20.00)
[   62.913104] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xc
[   62.913110] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xe
[   62.913112] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   63.793297] ppdev: user-space parallel port driver
[   63.976916] audit(1212577708.245:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5271 profile="/usr/sbin/cupsd" namespace="default"
[   64.242375] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[   66.473460] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   66.473468] vboxdrv: Successfully done.
[   66.473470] vboxdrv: Found 2 processor cores.
[   66.473488] vboxdrv: fAsync=1 u64DiffCores=532524.
[   66.473561] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   66.473563] vboxdrv: Successfully loaded version 1.6.0 (interface 0x00070001).
[   66.943177]  sdb1
[   66.943272] sd 8:0:0:0: [sdb] Attached SCSI disk
[   66.943331] sd 8:0:0:0: Attached scsi generic sg2 type 0
[   66.944502] sd 9:0:0:0: [sdc] 1994752 512-byte hardware sectors (1021 MB)
[   66.945177] sd 9:0:0:0: [sdc] Write Protect is off
[   66.945181] sd 9:0:0:0: [sdc] Mode Sense: 23 00 00 00
[   66.945183] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[   66.947758] sd 9:0:0:0: [sdc] 1994752 512-byte hardware sectors (1021 MB)
[   66.948549] sd 9:0:0:0: [sdc] Write Protect is off
[   66.948553] sd 9:0:0:0: [sdc] Mode Sense: 23 00 00 00
[   66.948555] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[   66.948563]  sdc: sdc1
[   66.949525] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[   66.949583] sd 9:0:0:0: Attached scsi generic sg3 type 0
[   69.997652] Bluetooth: Core ver 2.11
[   69.997775] NET: Registered protocol family 31
[   69.997781] Bluetooth: HCI device and connection manager initialized
[   69.997786] Bluetooth: HCI socket layer initialized
[   70.007410] Bluetooth: L2CAP ver 2.9
[   70.007419] Bluetooth: L2CAP socket layer initialized
[   70.012468] Bluetooth: RFCOMM socket layer initialized
[   70.012489] Bluetooth: RFCOMM TTY layer initialized
[   70.012491] Bluetooth: RFCOMM ver 1.8
[   71.232113] eth0: no IPv6 routers present
[   71.444896] Netfilter messages via NETLINK v0.30.
[   75.187427] Clocksource tsc unstable (delta = -203609531 ns)
[  114.829766] hda-intel: Invalid position buffer, using LPIB read method instead.
[  277.743812] usb 5-1: reset high speed USB device using ehci_hcd and address 2
[  293.351310] usb 5-1: USB disconnect, address 2
[  301.710661] usb 5-1: new high speed USB device using ehci_hcd and address 7
[  301.777134] usb 5-1: configuration #1 chosen from 1 choice
[  301.779731] scsi10 : SCSI emulation for USB Mass Storage devices
[  301.780795] usb-storage: device found at 7
[  301.780802] usb-storage: waiting for device to settle before scanning
[  304.995771] usb-storage: device scan complete
[  310.596346] usb 5-1: reset high speed USB device using ehci_hcd and address 7
[  310.729531] scsi 10:0:0:0: Direct-Access     WD       3200AAJ External 1.06 PQ: 0 ANSI: 0
[  310.731003] sd 10:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
[  310.735585] sd 10:0:0:0: [sdd] Write Protect is off
[  310.735592] sd 10:0:0:0: [sdd] Mode Sense: 00 00 00 00
[  310.735595] sd 10:0:0:0: [sdd] Assuming drive cache: write through
[  310.736632] sd 10:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
[  310.737256] sd 10:0:0:0: [sdd] Write Protect is off
[  310.737259] sd 10:0:0:0: [sdd] Mode Sense: 00 00 00 00
[  310.737261] sd 10:0:0:0: [sdd] Assuming drive cache: write through
[  310.737269]  sdd: sdd1
[  310.745728] sd 10:0:0:0: [sdd] Attached SCSI disk
[  310.745778] sd 10:0:0:0: Attached scsi generic sg2 type 0
[  451.088119] usb 5-1: reset high speed USB device using ehci_hcd and address 7
[  559.503373] Buffer I/O error on device sdb1, logical block 786433
[  559.503389] Buffer I/O error on device sdb1, logical block 786433
[  559.515318] Buffer I/O error on device sdb1, logical block 786433
[  559.516709] Buffer I/O error on device sdb1, logical block 786433
[  559.518582] Buffer I/O error on device sdb1, logical block 786433
[  559.567236] Buffer I/O error on device sdb1, logical block 786433
[  559.567426] Buffer I/O error on device sdb1, logical block 786433
[  559.568774] Buffer I/O error on device sdb1, logical block 786433
[  559.570526] Buffer I/O error on device sdb1, logical block 786433
[  559.574399] Buffer I/O error on device sdb1, logical block 786433
[  578.648016] printk: 184 messages suppressed.
[  578.648024] Buffer I/O error on device sdb1, logical block 786433
[  578.649667] Buffer I/O error on device sdb1, logical block 786433
[  578.651305] Buffer I/O error on device sdb1, logical block 786433
[  611.126539] usb 5-1: reset high speed USB device using ehci_hcd and address 7
[  615.035952] usb 5-6: reset high speed USB device using ehci_hcd and address 6
[  615.173398] scsi11 : SCSI emulation for USB Mass Storage devices
[  615.175798] usb-storage: device found at 7
[  615.175807] usb-storage: waiting for device to settle before scanning
[  620.165656] usb-storage: device scan complete
[  620.166143] scsi 11:0:0:0: Direct-Access     WD       3200AAJ External 1.06 PQ: 0 ANSI: 0
[  620.168187] sd 11:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[  620.168866] sd 11:0:0:0: [sdc] Write Protect is off
[  620.168869] sd 11:0:0:0: [sdc] Mode Sense: 00 00 00 00
[  620.168871] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[  620.169861] sd 11:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[  620.170486] sd 11:0:0:0: [sdc] Write Protect is off
[  620.170488] sd 11:0:0:0: [sdc] Mode Sense: 00 00 00 00
[  620.170490] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[  620.170495]  sdc: sdc1
[  620.178109] sd 11:0:0:0: [sdc] Attached SCSI disk
[  620.178163] sd 11:0:0:0: Attached scsi generic sg2 type 0
[ 5585.534126] printk: 113 messages suppressed.
[ 5585.534134] Buffer I/O error on device sdb1, logical block 786433
[ 5585.634053] Buffer I/O error on device sdb1, logical block 786433
[ 5585.911056] Buffer I/O error on device sdb1, logical block 786433
[ 5585.916695] Buffer I/O error on device sdb1, logical block 786433
[ 5585.920366] Buffer I/O error on device sdb1, logical block 786433
[ 5585.924188] Buffer I/O error on device sdb1, logical block 786433
[ 5585.931708] Buffer I/O error on device sdb1, logical block 786433
[ 5585.937134] Buffer I/O error on device sdb1, logical block 786433
[ 5585.940748] Buffer I/O error on device sdb1, logical block 786433
[ 5585.945786] Buffer I/O error on device sdb1, logical block 786433
[ 6544.658316] printk: 21 messages suppressed.
[ 6544.658323] Buffer I/O error on device sdb1, logical block 786433
[ 6544.729889] Buffer I/O error on device sdb1, logical block 786433
[ 6544.761071] Buffer I/O error on device sdb1, logical block 786433
[ 6544.764087] Buffer I/O error on device sdb1, logical block 786433
[ 6544.773801] Buffer I/O error on device sdb1, logical block 786433
[ 6544.775444] Buffer I/O error on device sdb1, logical block 786433
[ 6544.777039] Buffer I/O error on device sdb1, logical block 786433
[ 6544.780939] Buffer I/O error on device sdb1, logical block 786433
[ 6544.782082] Buffer I/O error on device sdb1, logical block 786433
[ 6544.785844] Buffer I/O error on device sdb1, logical block 786433
[ 6993.105294] printk: 21 messages suppressed.
[ 6993.105308] python[739]: segfault at 6379 rip 7f7c13f5b89c rsp 7fff1d1e5b00 error 4
[ 7025.116496] python[918]: segfault at 6379 rip 7f604f5b489c rsp 7fff5883d150 error 4
[40956.161101] usb 2-1: USB disconnect, address 2
[40957.729278] usb 2-1: new low speed USB device using uhci_hcd and address 4
[40957.851712] usb 2-1: configuration #1 chosen from 1 choice
[40957.862310] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input6
[40957.876180] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:10.1-1
[40970.169552] compiz.real[6113]: segfault at 390 rip 40fee0 rsp 7fff34d12450 error 4

---

### Post by Jouke74 on 2008-06-05
There is at least one problem with your WD 3200AAJ External harddrive, but I can't see if you boot Ubuntu from this one. 

[ 61.640738] sd 8:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[ 61.641393] sd 8:0:0:0: [sdb] Write Protect is off
[ 61.641396] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 61.641398] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 61.642388] sd 8:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[ 61.643014] sd 8:0:0:0: [sdb] Write Protect is off
[ 61.643016] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 61.643018] sd 8:0:0:0: [sdb] Assuming drive cache: write through

^
Buffer I/O error on device sdb1, logical block 786433 and many more error of this type.


[ 6993.105308] python[739]: segfault at 6379 rip 7f7c13f5b89c rsp 7fff1d1e5b00 error 4
[ 7025.116496] python[918]: segfault at 6379 rip 7f604f5b489c rsp 7fff5883d150 error 4
[40970.169552] compiz.real[6113]: segfault at 390 rip 40fee0 rsp 7fff34d12450 error 4

Compiz and python crash here. 



Are you connecting multiple external Western Digital disks, or is it just one WD 3200AAJ External connecting and reconnecting, I guess the last?
scsi 8:0:0:0: Direct-Access WD 3200AAJ External 1.06 PQ: 0 ANSI: 0
scsi 10:0:0:0: Direct-Access WD 3200AAJ External 1.06 PQ: 0 ANSI: 0

If it is reconnecting, that explains the IO errors ar 8:0:0:0, and maybe also the long cpu-io wait times, especially if you read something from this disk (your Virtual Box VM maybe?)

---

### Post by fistuks on 2008-06-05
i only have one and it's not my boot disk. it is also ntfs if it is important..

how do i fix this reconnecting?
now that i think of, 
there were many times i noticed it's working (you can hear it) when nothing from me or an application running was asking for it...
could it be some with the usb?

what do you mean about the python and compiz crash? i have compiz enabled...

---

### Post by fistuks on 2008-06-05
is there some kind of manual about this log?

---

### Post by Jouke74 on 2008-06-05
After crash they are reloaded, the errors can also be non-fatal for the program. 

The WD disk probably goes into USB sleep mode to safe power. Check if your system is running better if you don't have the drive connected at all. Note btw. that this may not be the reason for the slow down, since it is not your system disk.

---

### Post by murrie on 2008-06-05
> **fistuks said:**
> i'v tried that and could not get any clear conclusion.
the cpu usage in the resources section shows much more cpu usage from adding all of the cpu% from the process tab.

and i only gave amarok and Thunderbird as an example.
the low performance is not specific to a single application.

i'm running ubuntu
i just like the kde more than the gnome players...

I am running firefox, evolution, amarok and gimp while downloading updates from the internet and the whole system is working flawlessly.  Asus mobo, amd x2 6000+ oc by 20%, 4 gig ram ddr2 800, nvidia gainward 8600 gts, hooked to dell 30 inch flatpanel, running at 2560X1600X24 bit colour.  Works like a treat.  This is a stock install with nvidia driver, flash and java installed.

---

### Post by fistuks on 2008-06-06
> I am running firefox, evolution, amarok and gimp while downloading updates from the internet and the whole system is working flawlessly. Asus mobo, amd x2 6000+ oc by 20%, 4 gig ram ddr2 800, nvidia gainward 8600 gts, hooked to dell 30 inch flatpanel, running at 2560X1600X24 bit colour. Works like a treat. This is a stock install with nvidia driver, flash and java installed. 

I'm so happy for you... You are such a nice person...

> After crash they are reloaded, the errors can also be non-fatal for the program.

The WD disk probably goes into USB sleep mode to safe power. Check if your system is running better if you don't have the drive connected at all. Note btw. that this may not be the reason for the slow down, since it is not your system disk.

thanx!
I don't know what in the process cleared my system but i did a format to the WD disk and - slow no more!
Is there manual i can learn how to understand is log file?

---

### Post by Jouke74 on 2008-06-06
The log file is a clutter of all sorts of program information and problems of the Kernel (I assume Debug Messages). I don't think there is a simple manual for this, since the output is dependent on many factors (used hardware and software). I did not learn reading it from a manual, but if you run through it carefully and google some individual terms you'll start to understand things slowly.

Interesting that a format solved it. Glad I could help. Please also put the thread on "SOLVED".

---

### Post by jsandeo on 2008-06-06
After updating my amd64 system to Hardy, everything started being slow as hell... my box was constantly doing swap.

I added the following boot options to my boot image at /boot/grub/menu.lst :
fb=false noapic nolapic

Now everything seems to be fine again.

---

### Post by fistuks on 2008-06-06
how do i put it in "solved"?

---

### Post by soxs on 2008-06-06
thread tools below the 2 grey baars.
"thread tools" -> "mark thread as solved"

---

