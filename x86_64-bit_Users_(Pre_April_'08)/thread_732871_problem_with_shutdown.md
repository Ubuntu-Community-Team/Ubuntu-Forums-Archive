---
title: "problem with shutdown"
date: 2008-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by archimedes1981 on 2008-03-23
system won't shutdown fully. everything locks up and pc won't turn off unless on/off button is pressed.

---

### Post by Ehtetur on 2008-03-23
> **archimedes1981 said:**
> system won't shutdown fully. everything locks up and pc won't turn off unless on/off button is pressed.
Hi archimedes1981... 
hrmmmm... That sounds more like a statement than a question...:twisted:

To get an idea of where the problem lies, take a look at the logs and see if they point to anything specific that could be causing the lockup:
> System --> Administration --> System Log

Does it lock up during reboot, just during shutdown, or both!?

---

### Post by archimedes1981 on 2008-04-26
no just on shutdown.
i might be having trouble because of my Uli 5263 ethernet controller. The driver does not seem to be made for it despite the fact that it works. i'll try looking up in the logs but i'm not that good to understand what's wrong. I looked up about this problem a lot and other people have it . some say that it went away after some time. i tried adding some codes to media files i can't remember. probably it has to do something with the ethernet because i added apm=power-off acpi=off and noapic to boot because it hung when running. I'm not sure but probably when not using the internet it doesn't hang. before the boot options were set it used to shutdown properly but only if it worked long enough to let me do a shutdown before hanging.

---

### Post by archimedes1981 on 2008-04-26
Apr 26 10:29:46 Arch-Ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Apr 26 10:29:42 Arch-Ubuntu kernel: [    0.000000] Entering add_active_range(0, 256, 262064) 1 entries of 3200 used
Apr 26 10:29:42 Arch-Ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Apr 26 10:29:42 Arch-Ubuntu kernel: [    0.000000] Entering add_active_range(0, 256, 262064) 1 entries of 3200 used
Apr 26 10:29:42 Arch-Ubuntu kernel: [    0.000000] On node 0 totalpages: 261967
Apr 26 10:29:42 Arch-Ubuntu kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Apr 26 10:29:42 Arch-Ubuntu kernel: [    0.000000]   DMA zone: 1125 pages reserved
Apr 26 10:29:42 Arch-Ubuntu kernel: [    0.000000]   DMA zone: 2818 pages, LIFO batch:0
Apr 26 10:29:42 Arch-Ubuntu kernel: [    0.000000]   DMA32 zone: 3526 pages used for memmap
Apr 26 10:29:42 Arch-Ubuntu kernel: [    0.000000]   DMA32 zone: 254442 pages, LIFO batch:31
Apr 26 10:29:42 Arch-Ubuntu kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Apr 26 10:29:42 Arch-Ubuntu kernel: [   22.175740] PCI: Probing PCI hardware (bus 00)
Apr 26 10:29:42 Arch-Ubuntu kernel: [   22.176826] PCI: Using ALI IRQ Router
Apr 26 10:29:42 Arch-Ubuntu kernel: [   22.176841] PCI: setting IRQ 11 as level-triggered
Apr 26 10:29:42 Arch-Ubuntu kernel: [   22.179566] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 26 10:29:42 Arch-Ubuntu kernel: [   22.179572] PCI: Setting latency timer of device 0000:00:02.0 to 64
Apr 26 10:29:42 Arch-Ubuntu kernel: [   22.887258] Boot video device is 0000:01:00.0
Apr 26 10:29:42 Arch-Ubuntu kernel: [   34.282464] libata version 2.21 loaded.
Apr 26 10:29:42 Arch-Ubuntu kernel: [   34.294260] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 26 10:29:42 Arch-Ubuntu kernel: [   35.099581] PCI: setting IRQ 10 as level-triggered
Apr 26 10:29:42 Arch-Ubuntu kernel: [   35.110853] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 26 10:29:42 Arch-Ubuntu kernel: [   35.119413] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 26 10:29:42 Arch-Ubuntu kernel: [   35.600229] Probing IDE interface ide0...
Apr 26 10:29:42 Arch-Ubuntu kernel: [   36.562825] hda: selected mode 0x46
Apr 26 10:29:42 Arch-Ubuntu kernel: [   36.563042] Probing IDE interface ide1...
Apr 26 10:29:42 Arch-Ubuntu kernel: [   38.142795] hdc: selected mode 0x42
Apr 26 10:29:42 Arch-Ubuntu kernel: [   38.143158] hdd: selected mode 0x42
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.567118] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_1689'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.741950] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5246'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.743863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4152'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.744250] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4172'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.744560] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5249'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.744863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_1563'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.745166] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_7101'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.745473] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5455'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.745774] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5263'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.746072] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5229'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.746371] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5229_ide_0_0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.746669] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5229_ide_1_0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.746973] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5229_ide_1_1'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.747272] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5289'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.747569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5289_scsi_host'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.747865] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5289_scsi_host_scsi_device_lun0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.748161] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5237'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.748497] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_0f_0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.748834] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_0f_0_if0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.749168] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5237_0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.749486] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_0f_1'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.749790] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_0f_1_if0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.750087] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.750405] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_if0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.750704] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_if0_bluetooth_hci'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.751007] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_if1'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.751304] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5237_1'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.751599] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_0f_2'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.751896] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_0f_2_if0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.752189] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5239'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.752482] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_0f_3'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.752775] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_0f_3_if0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.753067] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1022_1100'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.753364] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1022_1101'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.753656] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1022_1102'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.753949] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1022_1103'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.754240] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.754530] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.754821] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.755137] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.755435] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.755744] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.756038] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.756329] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.756619] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.756910] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0b_6a_d1_f7_30'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.769657] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5289_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.791406] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5455_oss_pcm_1'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.791803] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5455_oss_pcm_0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.792111] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5455_alsa_control__1'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.792419] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5455_oss_pcm_0_0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.792722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5455_oss_mixer__1'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.793024] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5455_alsa_capture_0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.793324] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5455_alsa_playback_0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.793632] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5455_alsa_capture_1'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.793932] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b9_5455_alsa_playback_2'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.794232] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.794531] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.794837] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.795136] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.795434] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_0'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.795732] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.796060] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_1'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.796380] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.796686] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_0f_0_usbraw'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.796986] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_0f_1_usbraw'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.797284] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_usbraw'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.797607] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_0f_2_usbraw'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.797908] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_0f_3_usbraw'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.813962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Y36DGEPE'). 
Apr 26 10:29:42 Arch-Ubuntu NetworkManager: <debug> [1209198582.820794] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_AA7CF3337CF2F8C1'). 
Apr 26 10:29:43 Arch-Ubuntu NetworkManager: <debug> [1209198583.081700] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_BENQ_DVD_DD_DW1620'). 
Apr 26 10:29:43 Arch-Ubuntu NetworkManager: <debug> [1209198583.096778] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_Pioneer_DVD_ROM_ATAPIModel_DVD_116_0122'). 
Apr 26 10:29:43 Arch-Ubuntu NetworkManager: <debug> [1209198583.526364] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Maxtor_6L200S0_L594AAAG'). 
Apr 26 10:29:43 Arch-Ubuntu NetworkManager: <debug> [1209198583.644708] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_72FC4E81FC4E4019'). 
Apr 26 10:29:43 Arch-Ubuntu NetworkManager: <debug> [1209198583.679547] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Apr 26 10:29:43 Arch-Ubuntu NetworkManager: <debug> [1209198583.684591] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_c9b3b17d_9617_414b_a546_9b7cd6d6db36'). 
Apr 26 10:29:43 Arch-Ubuntu NetworkManager: <debug> [1209198583.773524] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8cb23d0b_96b0_49c1_b04b_02a7818a26b2'). 
Apr 26 10:29:43 Arch-Ubuntu NetworkManager: <debug> [1209198583.941896] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_e74bc2ab_85cf_43ab_b66f_7a881f9b5589'). 
Apr 26 10:29:44 Arch-Ubuntu NetworkManager: <debug> [1209198584.016797] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_433b41d4_d9e4_4c22_a7c9_ad882dc0e36d'). 
Apr 26 10:29:44 Arch-Ubuntu NetworkManager: <debug> [1209198584.476508] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Ubuntu_5_04_i386'). 
Apr 26 10:29:44 Arch-Ubuntu audio[4714]: add_service_record: got record id 0x10000
Apr 26 10:29:44 Arch-Ubuntu audio[4714]: add_service_record: got record id 0x10001
Apr 26 10:29:44 Arch-Ubuntu NetworkManager: <debug> [1209198584.874918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Apr 26 10:29:44 Arch-Ubuntu NetworkManager: <debug> [1209198584.886221] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Apr 26 10:29:47 Arch-Ubuntu kernel: [   60.966190] eth0: no IPv6 routers present
Apr 26 10:30:18 Arch-Ubuntu kernel: [   91.188193] ISO 9660 Extensions: Microsoft Joliet Level 3
Apr 26 10:30:18 Arch-Ubuntu kernel: [   91.345859] ISO 9660 Extensions: RRIP_1991A
Apr 26 10:36:24 Arch-Ubuntu kernel: [  457.199713] spurious 8259A interrupt: IRQ7.

---

### Post by archimedes1981 on 2008-04-30
anybody help??

---

### Post by archimedes1981 on 2008-05-21
noapic acpi=force apm=power_off : did the trick
however although the system shuts down completely i did not see the orange bar. How can i be sure that there is no harm done by forcing acpi ? is it safe?

false alarm. i'm back to a hanging system.

---

