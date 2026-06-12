---
title: "Ndiswrapper fails to run on ASPIRE 1522WLMi"
date: 2005-05-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by daugirdas on 2005-05-20
I have Acer **Aspire 1522 WLMi** laptop with IPN2220 (not 100% sure) wlan chipset. It used to work under ubuntu32, but under 64 bit its all screwed.
Instalation of source package completes without a glich (both 1.1 and 1.2 rc1). When I installed a driver it said "hardware present, invalid chipset". However when I try to load a 64 bit driver (neti2220X64) everything fails here. I had kernel Ooopses and so (2.6.11).
```

May 19 23:32:50 localhost kernel: ndiswrapper version 1.2rc1 loaded (preempt=no,smp=no)
May 19 23:32:50 localhost kernel: ndiswrapper: driver neti2220x64 (,17/01/2005,3.03.12.2006) loaded
May 19 23:32:50 localhost kernel: ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 21 (level, low) -> IRQ 21
May 19 23:32:50 localhost kernel: Unable to handle kernel paging request at fffff78000000014 RIP:
May 19 23:32:50 localhost kernel: [<ffffc2000167117c>]
May 19 23:32:50 localhost kernel: PGD 0
May 19 23:32:50 localhost kernel: Oops: 0000 [1]
May 19 23:32:50 localhost kernel: CPU 0
May 19 23:32:50 localhost kernel: Modules linked in: ndiswrapper isofs loop cpufreq_stats cpufreq_ondemand cpufreq_powersave pcmcia ipt_limit iptable_mangle ipt_LOG ipt_MASQUERADE iptable_nat ipt_TOS ipt_REJECT ip_conntrack_irc ip_conntrack_ftp ipt_state ip_conntrack iptable_filter ip_tables video sony_acpi pcc_acpi button battery container ac ipv6 af_packet snd_via82xx_modem snd_via82xx snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm usbhid snd_timer snd_page_alloc gameport snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore i2c_viapro i2c_core ehci_hcd uhci_hcd r8169 ohci1394 ieee1394 yenta_socket rsrc_nonstatic pcmcia_core pcspkr ext2 md dm_mod capability commoncap cpufreq_userspace powernow_k8 freq_table evdev nvidia joydev parport_pc lp parport tsdev ide_cd cdrom rtc mousedev psmouse ext3 jbd mbcache ide_generic via82cxxx ide_disk ide_core unix thermal processor fan fbcon crc32 font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
May 19 23:32:50 localhost kernel: Pid: 5459, comm: loadndisdriver Tainted: P   M  2.6.11-1-amd64-k8
May 19 23:32:50 localhost kernel: RIP: 0010:[<ffffc2000167117c>] [<ffffc2000167117c>]
May 19 23:32:50 localhost kernel: RSP: 0018:ffff81001a50dc30  EFLAGS: 00010206
May 19 23:32:50 localhost kernel: RAX: 0000000000000000 RBX: ffffc200016b0000 RCX: ffffc200016b000a
May 19 23:32:50 localhost kernel: RDX: 00000000fffffffe RSI: ffff81001a50dd24 RDI: 0000000000000000
May 19 23:32:50 localhost kernel: RBP: 0000000000000000 R08: 0000000000000000 R09: 0000000000000000
May 19 23:32:50 localhost kernel: R10: 0000000000000000 R11: 0000000000000008 R12: ffff810001bfa800
May 19 23:32:50 localhost kernel: R13: ffff810013469800 R14: ffff81001690c000 R15: 0000000000000002
May 19 23:32:50 localhost kernel: FS:  00002aaaaaac2860(0000) GS:ffffffff80407400(0000) knlGS:00000000560ba740
May 19 23:32:50 localhost kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
May 19 23:32:50 localhost kernel: CR2: fffff78000000014 CR3: 000000001f3df000 CR4: 00000000000006e0
May 19 23:32:50 localhost kernel: Process loadndisdriver (pid: 5459, threadinfo ffff81001a50c000, task ffff81001f46ce50)
May 19 23:32:50 localhost kernel: Stack: ffff81001690c000 ffff810013469800 ffff810001bfa800 ffff81001690c360
May 19 23:32:50 localhost kernel:        ffff81001a50dd24 ffff81001690c360 0000000000000000 ffffc200016ab255
May 19 23:32:50 localhost kernel:        ffffffff8011a5da 0000000000000015
May 19 23:32:50 localhost kernel: Call Trace:<ffffffff8011a5da>{mp_register_gsi+58} <ffffffff887d3b72>{:ndiswrapper:lin_to_win6+30}
May 19 23:32:50 localhost kernel:        <ffffffff801d5207>{pci_request_region+199} <ffffffff887cf1be>{:ndiswrapper:miniport_init+110}
May 19 23:32:50 localhost kernel:        <ffffffff887bf07a>{:ndiswrapper:ndiswrapper_add_one_pci_dev+298}
May 19 23:32:50 localhost kernel:        <ffffffff801d6a7d>{pci_device_probe_static+61} <ffffffff801d6ad9>{__pci_device_probe+41}
May 19 23:32:50 localhost kernel:        <ffffffff801d6b30>{pci_device_probe+48} <ffffffff802311dd>{driver_probe_device+77}
May 19 23:32:50 localhost kernel:        <ffffffff802312f6>{driver_attach+70} <ffffffff802317f0>{bus_add_driver+144}
May 19 23:32:50 localhost kernel:        <ffffffff80231d12>{driver_register+50} <ffffffff801d6dd6>{pci_register_driver+118}
May 19 23:32:50 localhost kernel:        <ffffffff887c0468>{:ndiswrapper:register_devices+1080}
May 19 23:32:50 localhost kernel:        <ffffffff887c05d3>{:ndiswrapper:wrapper_ioctl+67} <ffffffff8018024b>{do_ioctl+75}
May 19 23:32:50 localhost kernel:        <ffffffff80180575>{vfs_ioctl+421} <ffffffff8016f7ac>{__fput+268}
May 19 23:32:50 localhost kernel:        <ffffffff801805fa>{sys_ioctl+106} <ffffffff8010e15a>{system_call+126}
May 19 23:32:50 localhost kernel:
May 19 23:32:50 localhost kernel:
May 19 23:32:50 localhost kernel: Code: 48 a1 14 00 00 00 80 f7 ff ff 48 8d 93 30 e6 08 00 48 d3 f8
May 19 23:32:50 localhost kernel: RIP [<ffffc2000167117c>] RSP <ffff81001a50dc30>
May 19 23:32:50 localhost kernel: CR2: fffff78000000014
May 19 23:32:50 localhost kernel:  <3>ndiswrapper (wrapper_init:1571): loadndiswrapper failed (9); check system log for messages from 'loadndisdriver'
May 19 23:32:56 localhost udev[5500]: removing device node '/dev/ndiswrapper'

```
Even when driver is removed by ndiswrapper -e [name], ndiswrapper -l gives some sort of error:
```

daugirdas@dtr-linux64:~$ ndiswrapper -l
Installed ndis drivers:
chipset invalid driver!
daugirdas@dtr-linux64:~$

```

Is there anythyng wrong I was doing? Do I need a 2.6.12 kernel? A bug report to ndiswrapper mailing list? A different driver?

If you have the same laptop and have wlan on 64bit os working, please please please let me know how!!!

---

