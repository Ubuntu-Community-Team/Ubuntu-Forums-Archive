---
title: "webcam and pcmcia card reader issues"
date: 2007-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by alek66 on 2007-03-25
I cant make my old logitech quickcam work, do I need any packages or something?
heres mi dmesg
```
alek@DeathStar:~$ dmesg | grep cam
[   41.255804] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.3 $Date: 2005/04/15 19:32:49 $)
[   41.255809] quickcam: Kernel:2.6.17-11-generic bus:4 class:FF subclass:FF vendor:046D product:0840
[   41.256879] quickcam: Sensor HDCS-1000/1100 detected
[   41.257162] quickcam: Registered device: /dev/video0
[   41.257180] usbcore: registered new driver quickcam
[ 5805.811167] Modules linked in: usblp vfat fat nls_utf8 ntfs binfmt_misc nls_cp437 isofs udf rfcomm l2cap powernow_k8 cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sbs sony_acpi pcc_acpi i2c_ec hotkey dev_acpi button battery container ac asus_acpi sg sd_mod af_packet ipv6 sbp2 parport_pc lp parport quickcam usb_storage scsi_mod hci_usb pcmcia usbhid libusual videodev joydev tsdev bluetooth snd_via82xx gameport snd_via82xx_modem nvidia snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event i2c_viapro snd_pcm snd_mpu401_uart pcspkr yenta_socket rsrc_nonstatic pcmcia_core snd_seq snd_timer i2c_core via_ircc snd_rawmidi snd_seq_device r1000 r8169 evdev irda crc_ccitt snd soundcore snd_page_alloc psmouse serio_raw shpchp pci_hotplug ext3 jbd ehci_hcd uhci_hcd usbcore ohci1394 ieee1394 ide_generic ide_cd cdrom ide_disk via82cxxx generic thermal processor fan vesafb capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
[ 5805.811335]        <ffffffff888bb0fb>{:quickcam:qc_isoc_stop+203} <ffffffff888bd3e9>{:quickcam:qc_v4l_close+73}

```

Also my laptop comes with a pcmcia multi card reader(acer brand) Works ok in suse, but here... no can do
```
alek@DeathStar:~$ dmesg | grep pcmcia
[ 5805.811167] Modules linked in: usblp vfat fat nls_utf8 ntfs binfmt_misc nls_cp437 isofs udf rfcomm l2cap powernow_k8 cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sbs sony_acpi pcc_acpi i2c_ec hotkey dev_acpi button battery container ac asus_acpi sg sd_mod af_packet ipv6 sbp2 parport_pc lp parport quickcam usb_storage scsi_mod hci_usb pcmcia usbhid libusual videodev joydev tsdev bluetooth snd_via82xx gameport snd_via82xx_modem nvidia snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event i2c_viapro snd_pcm snd_mpu401_uart pcspkr yenta_socket rsrc_nonstatic pcmcia_core snd_seq snd_timer i2c_core via_ircc snd_rawmidi snd_seq_device r1000 r8169 evdev irda crc_ccitt snd soundcore snd_page_alloc psmouse serio_raw shpchp pci_hotplug ext3 jbd ehci_hcd uhci_hcd usbcore ohci1394 ieee1394 ide_generic ide_cd cdrom ide_disk via82cxxx generic thermal processor fan vesafb capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor

```

any tips or pointers to read or something?

---

