---
title: "Kernel Oops"
date: 2007-08-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by newpers on 2007-08-19
Any ideas on the following?

Message from syslogd@poopy at Sun Aug 19 13:13:44 2007 ...
poopy kernel: [  344.089097] Oops: 0000 [1] SMP 

Message from syslogd@poopy at Sun Aug 19 13:13:44 2007 ...
poopy kernel: [  344.089327] CR2: 000000003155f840

---

### Post by newpers on 2007-08-19
Oh yeah...

Aug 19 13:12:56 poopy kernel: [  320.157640] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 19 13:12:56 poopy kernel: [  320.190833] Netfilter messages via NETLINK v0.30.
Aug 19 13:12:56 poopy kernel: [  320.199625] nf_conntrack version 0.5.0 (4091 buckets, 32728 max)
Aug 19 13:13:44 poopy kernel: [  344.089078] Unable to handle kernel paging request at 000000003155f840 RIP: 
Aug 19 13:13:44 poopy kernel: [  344.089085]  [add_timer_on+12/96] add_timer_on+0xc/0x60
Aug 19 13:13:44 poopy kernel: [  344.089093] PGD 25334067 PUD 25338067 PMD 0 
Aug 19 13:13:44 poopy kernel: [  344.089097] Oops: 0000 [1] SMP 
Aug 19 13:13:44 poopy kernel: [  344.089099] CPU 0 
Aug 19 13:13:44 poopy kernel: [  344.089101] Modules linked in: xt_tcpudp xt_state iptable_nat nf_conntrack_ipv4 iptable_filter nf_nat
_irc nf_conntrack_irc nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack nfnetlink ip_tables x_tables ppdev powernow_k8 cpufreq_powersave
 cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table tc1100_wmi pcc_acpi sony_acpi dev_acpi video battery
 container sbs button i2c_ec dock ac asus_acpi backlight nls_utf8 ntfs sbp2 lp snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_in
tel8x0 snd_seq_dummy snd_seq_oss snd_seq_midi snd_mpu401 snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_o
ss nvidia(P) snd_seq_midi_event snd_seq analog snd_mpu401_uart snd_rawmidi emu10k1_gp gameport snd_pcm snd_util_mem snd_hwdep parport_
pc parport snd_timer snd_seq_device psmouse serio_raw i2c_nforce2 shpchp k8temp snd soundcore i2c_core pci_hotplug snd_page_alloc ipv6
 tsdev evdev reiserfs sg sd_mod ide_cd cdrom 8139cp generic amd74xx ata_generic floppy 
Aug 19 13:13:44 poopy kernel: 139too mii ohci1394 ieee1394 sata_nv libata scsi_mod ehci_hcd ohci_hcd usbcore thermal processor fan fbc
on tileblit font bitblit softcursor vesafb cfbcopyarea cfbimgblt cfbfillrect capability commoncap

---

