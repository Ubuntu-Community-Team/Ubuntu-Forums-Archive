---
title: "[SOLVED] Help: 10 Hardy Crashes Today"
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by elmoosecapitan on 2008-07-14
Hi everyone,


I have had ten freezes/crashes since 09:30, it is currently 14:51, and I would like to know what is going on. The first crash occurred due to rythmbox. The following two crashes occurred while reading CNN articles (about 4 FF tabs) and Rythmbox playing in the background. The fourth crash happened when I was moving from one desktop to another. Five occurred when I was reading a dvi file with Evince. I left for lunch eventually and properly turned off my computer, I also stopped running RythmBox after five. After the sixth crash I started to notice that my memory no longer swaps with virtual memory, which it usually does at a low level, my RAM recorded ~600MB/2900MB from the time of my 5th crash until my eighth crash. The eight one was while writing an email via thunderbird. Nine and ten occurred in an attempt to boot my OS after six.

I am currently running in safe mode, hoping that it does not crash while I write this message.

I have also noticed that when Hardy crashes, the CapsLk light flashes.


cheers




Programs (Minus system monitor, these are the programs that I run on a regular basis):
Firefox 3.0 (official/non-beta)
~between 2 and 10 tabs
Rythmbox
Thunderbird (2 email clients)
System Monitor
Evince PDF reader
1 terminal
6 virtual desktops (3 were empty)

Hardware:
ThinkPad T61
x86_64
2x 2.40GHz
3Gb RAM
8.3 Gb Virtual Memory
OS:
8.04
Kernel 2.6.24-19-generic
gnome 2.22.2

Last Update:
Yesterday morning, single flash update

---

### Post by stchman on 2008-07-14
> **elmoosecapitan said:**
> Hi everyone,


I have had eight freezes/crashes since 09:30, it is currently 14:51, and I would like to know what is going on. The first crash occurred due to rythmbox. The following two crashes occurred while reading CNN articles (about 4 FF tabs) and Rythmbox playing in the background. The fourth crash happened when I was moving from one desktop to another. Five occurred when I was reading a dvi file with Evince. I left for lunch eventually and properly turned off my computer. After the fifth crash I started to notice that my memory no longer swaps with virtual memory, which it usually does at a low level. Sixth while writing an email via thunderbird. Seven and eight occurred in an attempt to boot my OS after six.

I am currently running in safe mode, hoping that it does not crash while I write this message.

I have also noticed that when Hardy crashes, the CapsLk light flashes.


cheers




Programs (Minus system monitor, these are the programs that I run on a regular basis):
Firefox 3.0 (official/non-beta)
~between 2 and 10 tabs
Rythmbox
Thunderbird (2 email clients)
System Monitor
Evince PDF reader
1 terminal
6 virtual desktops (3 were empty)

Hardware:
ThinkPad T61
x86_64
2x 2.40GHz
3Gb RAM
8.3 Gb Virtual Memory
OS:
8.04
Kernel 2.6.24-19-generic
gnome 2.22.2

Last Update:
Yesterday morning, single flash update

So I can assume that the crashing just started today?

If yes there might be a hardware problem.  Try booting up the Live CD to see if Ubuntu crashes using that.

---

### Post by elmoosecapitan on 2008-07-14
Yes, the crashes have just started today. I do get regular crash every now and then, but nothing out of the ordinary until today. I already checking out my hardware [system->admin->harware test] and drivers and everything passed.

---

### Post by rob_quill on 2008-07-14
Hey.

From [http://www.linuxquestions.org/questions/linux-general-1/caps-lock-and-scroll-lock-flashing-47433/](http://www.linuxquestions.org/questions/linux-general-1/caps-lock-and-scroll-lock-flashing-47433/) I found that a blinking keyboard light means a kernel panic.

I'd suggest looking at /var/log/messages or /var/log/syslog straight after a crash (or now if you are feeling keen) and see if there is anything strange going on. Probably syslog is better, but try both. You can open them in your favourite text editor and have a look at the bottom of each file.

Also maybe you could just grep those two files from PANIC or something similar.

Let me know how you get on and I hope that helps.

Rob

---

### Post by elmoosecapitan on 2008-07-14
Here are some grep searches. I don't believe those that occurred during boot are showing. Fortunately I have only had the capslk light flash. My harddrive, however, is running warmer than it normally would. These all correspond to my system crashing.

MoosePad:~$ grep panic /var/log/syslog
MoosePad:~$ grep restart /var/log/syslog
Jul 14 09:42:49 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 10:51:58 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 12:52:55 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 13:02:06 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 13:17:03 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 13:28:56 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 14:23:35 MoosePad syslogd 1.5.0#1ubuntu1: restart.
MoosePad:~$ grep restart /var/log/messages
Jul 14 09:42:49 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 10:51:58 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 12:52:55 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 13:02:06 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 13:17:03 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 13:28:56 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 14:23:35 MoosePad syslogd 1.5.0#1ubuntu1: restart.
MoosePad:~$ grep error /var/log/messages
Jul 14 10:51:58 MoosePad kernel: [   13.220961] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 14 12:52:55 MoosePad kernel: [   21.737952] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 14 13:02:06 MoosePad kernel: [   13.346162] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 14 13:17:03 MoosePad kernel: [   13.350819] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 14 13:28:56 MoosePad kernel: [   14.654439] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 14 13:37:23 MoosePad kernel: [  190.621973] npviewer.bin[7279]: segfault at f5aa3030 rip f7897540 rsp ffed994c error 4
Jul 14 14:23:36 MoosePad kernel: [   13.897570] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
MoosePad:~$ grep failure /var/log/messages
MoosePad:~$ grep failure /var/log/syslog
MoosePad:~$ grep fail /var/log/messages
Jul 14 10:30:06 MoosePad kernel: [ 2916.289349] psmouse.c: resync failed, issuing reconnect request
Jul 14 10:52:00 MoosePad kernel: [   26.169204] vnet0: starting userspace STP failed, starting kernel STP
Jul 14 12:52:56 MoosePad kernel: [   33.852948] vnet0: starting userspace STP failed, starting kernel STP
Jul 14 13:02:07 MoosePad kernel: [   25.536738] vnet0: starting userspace STP failed, starting kernel STP
Jul 14 13:17:04 MoosePad kernel: [   25.912391] vnet0: starting userspace STP failed, starting kernel STP
Jul 14 13:28:57 MoosePad kernel: [   26.455929] vnet0: starting userspace STP failed, starting kernel STP
Jul 14 14:23:37 MoosePad kernel: [   27.012204] vnet0: starting userspace STP failed, starting kernel STP
MoosePad:~$  
MoosePad:~$

---

### Post by rob_quill on 2008-07-14
You could try looking at the last thing that is written in the file before the restart occurs. For instance the other day my laptop kept crashing and when I looked at the syslog I saw that right before it crashed (well right before I restart it) it tried to do something with the VPN, which I do not use, do I deleted my VPN settings.

Also I'm not sure if grep is case sensitive but a kernel panic is normally written in all caps.

Let me know what turns up.

Rob

---

### Post by elmoosecapitan on 2008-07-14
Jul 14 09:42:49 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 09:42:49 MoosePad anacron[6086]: Job `cron.daily' terminated
Jul 14 09:42:49 MoosePad anacron[6086]: Normal exit (1 job run)
Jul 14 09:49:31 MoosePad kernel: [  641.206426] iwl4965: Microcode SW error detected.  Restarting 0x2000000.
Jul 14 09:49:34 MoosePad kernel: [  644.209399] iwl4965: Can't stop Rx DMA.
Jul 14 10:01:36 MoosePad kernel: [ 1206.582814] iwl4965: Microcode SW error detected.  Restarting 0x2000000.
Jul 14 10:01:37 MoosePad kernel: [ 1209.581167] iwl4965: Can't stop Rx DMA.
Jul 14 10:09:21 MoosePad kernel: [ 1672.567336] iwl4965: Microcode SW error detected.  Restarting 0x2000000.
Jul 14 10:09:24 MoosePad kernel: [ 1675.569956] iwl4965: Can't stop Rx DMA.
Jul 14 10:17:02 MoosePad /USR/SBIN/CRON[9665]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 14 10:24:17 MoosePad kernel: [ 2567.897392] iwl4965: Microcode SW error detected.  Restarting 0x2000000.
Jul 14 10:24:20 MoosePad kernel: [ 2570.896509] iwl4965: Can't stop Rx DMA.
Jul 14 10:24:29 MoosePad kernel: [ 2579.099507] iwl4965: Microcode SW error detected.  Restarting 0x2000000.
Jul 14 10:24:32 MoosePad kernel: [ 2582.099928] iwl4965: Can't stop Rx DMA.
Jul 14 10:28:25 MoosePad kernel: [ 2814.614089] iwl4965: Microcode SW error detected.  Restarting 0x2000000.
Jul 14 10:28:28 MoosePad kernel: [ 2817.612140] iwl4965: Can't stop Rx DMA.
Jul 14 10:28:53 MoosePad kernel: [ 2842.469280] iwl4965: Microcode SW error detected.  Restarting 0x2000000.
Jul 14 10:28:55 MoosePad kernel: [ 2845.467996] iwl4965: Can't stop Rx DMA.
Jul 14 10:30:03 MoosePad kernel: [ 2913.266264] iwl4965: Microcode SW error detected.  Restarting 0x2000000.
Jul 14 10:30:06 MoosePad kernel: [ 2916.264573] iwl4965: Can't stop Rx DMA.
Jul 14 10:30:06 MoosePad kernel: [ 2916.264663] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Jul 14 10:30:06 MoosePad kernel: [ 2916.289349] psmouse.c: resync failed, issuing reconnect request
Jul 14 10:34:03 MoosePad kernel: [ 3152.234779] iwl4965: HCMD skipped: index (33) 28 30
Jul 14 10:34:03 MoosePad kernel: [ 3152.234786] iwl4965: HCMD skipped: index (33) 28 31
Jul 14 10:34:03 MoosePad kernel: [ 3152.234787] iwl4965: HCMD skipped: index (33) 28 32
Jul 14 10:34:06 MoosePad kernel: [ 3155.238514] iwl4965: Can't stop Rx DMA.
Jul 14 10:34:06 MoosePad kernel: [ 3155.505962] iwl4965: HCMD skipped: index (33) 7 9
Jul 14 10:34:06 MoosePad kernel: [ 3155.505967] iwl4965: HCMD skipped: index (33) 7 10


Jul 14 10:44:47 MoosePad kernel: [ 3458.040629] iwl4965: HCMD skipped: index (33) 7 29
Jul 14 10:44:47 MoosePad kernel: [ 3458.040630] iwl4965: HCMD skipped: index (33) 7 30
Jul 14 10:44:47 MoosePad kernel: [ 3458.040632] iwl4965: HCMD skipped: index (33) 7 31
Jul 14 10:44:47 MoosePad kernel: [ 3458.040634] iwl4965: HCMD skipped: index (33) 7 32
Jul 14 10:44:50 MoosePad kernel: [ 3461.038425] iwl4965: Can't stop Rx DMA.
Jul 14 10:51:58 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 10:51:58 MoosePad kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 14 10:51:58 MoosePad kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 14 10:51:58 MoosePad kernel: Symbols match kernel version 2.6.24.
Jul 14 10:51:58 MoosePad kernel: Loaded 37553 symbols from 106 modules.


Jul 14 10:52:42 MoosePad kernel: [   49.919941]    groups: 03
Jul 14 10:56:29 MoosePad ntpd[6376]: synchronized to 91.189.94.4, stratum 2
Jul 14 10:56:29 MoosePad ntpd[6376]: kernel time sync status change 0001
Jul 14 10:59:35 MoosePad kernel: [  371.848595] iwl4965: Microcode SW error detected.  Restarting 0x2000000.
Jul 14 10:59:38 MoosePad kernel: [  374.847047] iwl4965: Can't stop Rx DMA.
Jul 14 11:11:58 MoosePad -- MARK --
Jul 14 11:17:01 MoosePad /USR/SBIN/CRON[8276]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 14 11:31:58 MoosePad -- MARK --
Jul 14 11:51:58 MoosePad -- MARK --
Jul 14 11:54:42 MoosePad init: tty4 main process (4951) killed by TERM signal
Jul 14 11:54:42 MoosePad init: tty5 main process (4952) killed by TERM signal
Jul 14 11:54:42 MoosePad init: tty2 main process (4954) killed by TERM signal
Jul 14 11:54:42 MoosePad init: tty3 main process (4955) killed by TERM signal
Jul 14 11:54:42 MoosePad init: tty1 main process (6216) killed by TERM signal
Jul 14 11:54:42 MoosePad init: tty6 main process (4956) killed by TERM signal
Jul 14 11:54:43 MoosePad gdm[6047]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jul 14 11:54:43 MoosePad gdm[6047]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Jul 14 11:54:46 MoosePad avahi-daemon[5404]: Got SIGTERM, quitting.
Jul 14 11:54:46 MoosePad avahi-daemon[5404]: Leaving mDNS multicast group on interface vnet0.IPv4 with address 192.168.122.1.
Jul 14 11:54:46 MoosePad avahi-daemon[5404]: Leaving mDNS multicast group on interface eth0.IPv4 with address 131.225.56.194.
Jul 14 11:54:46 MoosePad libvirtd: Shutting down on signal 15
Jul 14 11:54:46 MoosePad dnsmasq[5610]: exiting on receipt of SIGTERM
Jul 14 11:54:48 MoosePad kernel: [ 3139.354189] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 14 11:54:49 MoosePad exiting on signal 15
Jul 14 12:52:55 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 12:52:55 MoosePad kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 14 12:52:55 MoosePad kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.


Jul 14 12:53:32 MoosePad hcid[5876]: Default passkey agent (:1.29, /org/bluez/passkey) registered
Jul 14 12:53:32 MoosePad hcid[5876]: Default authorization agent (:1.29, /org/bluez/auth) registered
Jul 14 12:53:44 MoosePad NetworkManager: <info>  Updating allowed wireless network lists. 
Jul 14 12:53:45 MoosePad kernel: [   57.331249] CPU0 attaching NULL sched-domain.
Jul 14 12:53:45 MoosePad kernel: [   57.331257] CPU1 attaching NULL sched-domain.
Jul 14 12:53:45 MoosePad kernel: [   57.349967] CPU0 attaching sched-domain:
Jul 14 12:53:45 MoosePad kernel: [   57.349973]  domain 0: span 03
Jul 14 12:53:45 MoosePad kernel: [   57.349974]   groups: 01 02
Jul 14 12:53:45 MoosePad kernel: [   57.349977]   domain 1: span 03
Jul 14 12:53:45 MoosePad kernel: [   57.349978]    groups: 03
Jul 14 12:53:45 MoosePad kernel: [   57.349980] CPU1 attaching sched-domain:
Jul 14 12:53:45 MoosePad kernel: [   57.349981]  domain 0: span 03
Jul 14 12:53:45 MoosePad kernel: [   57.349982]   groups: 02 01
Jul 14 12:53:45 MoosePad kernel: [   57.349984]   domain 1: span 03
Jul 14 12:53:45 MoosePad kernel: [   57.349985]    groups: 03
Jul 14 12:57:29 MoosePad ntpd[6332]: synchronized to 91.189.94.4, stratum 2
Jul 14 12:57:29 MoosePad ntpd[6332]: kernel time sync status change 0001
Jul 14 13:02:06 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 13:02:06 MoosePad kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 14 13:02:06 MoosePad kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 14 13:02:06 MoosePad kernel: Symbols match kernel version 2.6.24.


Jul 14 13:02:45 MoosePad kernel: [   48.547632]   domain 1: span 03
Jul 14 13:02:45 MoosePad kernel: [   48.547633]    groups: 03
Jul 14 13:06:40 MoosePad ntpd[6352]: synchronized to 91.189.94.4, stratum 2
Jul 14 13:06:40 MoosePad ntpd[6352]: kernel time sync status change 0001
Jul 14 13:17:03 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 13:17:03 MoosePad kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 14 13:17:03 MoosePad kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 14 13:17:03 MoosePad kernel: Symbols match kernel version 2.6.24.
Jul 14 13:17:03 MoosePad kernel: Loaded 37553 symbols from 106 modules.
Jul 14 13:17:03 MoosePad kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 14 13:17:03 MoosePad kernel: [    0.000000] Initializing cgroup subsys cpu

---

### Post by elmoosecapitan on 2008-07-14
while gathering information, my system crashed... again.

I plugged in my ipod and twenty minutes later: crash. I believe the two are unrelated. This is still in safe mode. I ran all the programs I stated above to induce a memory swap but I was only able to achieve 806/2900 Mb of RAM, sustained for about 30 minutes when my system crashed, and hence no swap took place.




Jul 14 15:39:05 MoosePad NetworkManager: <debug> [1216067945.677708] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_DCED_2844'). 
Jul 14 15:39:05 MoosePad hald: mounted /dev/sdb2 on behalf of uid 1000
Jul 14 15:39:07 MoosePad pulseaudio[6894]: shm.c: shm_open() failed: No such file or directory
Jul 14 15:39:07 MoosePad pulseaudio[6894]: pstream.c: Failed to import memory block.
Jul 14 15:54:30 MoosePad syslogd 1.5.0#1ubuntu1: restart.
Jul 14 15:54:30 MoosePad kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 14 15:54:30 MoosePad kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul 14 15:54:30 MoosePad kernel: Symbols match kernel version 2.6.24.

---

### Post by markbuntu on 2008-07-14
Try booting into a previous kernel when grub comes up. See if that helps.

---

### Post by elmoosecapitan on 2008-07-16
Hi All,

Thanks for all your help yesterday. After doing a massive review of my logs and talking to many people we've concluded that it's a hardware failure involving the hard drive.

Other forum posts indicating that a flashing caps lock light helped a lot.

The nice thing is that it is still under warranty. : )


cheers

---

### Post by wefojoij on 2008-07-31
Hi. Can you please say how you traced this to a hard drive problem? I am also experiencing a crash involving a flashing caps lock, but "panic" is not found in the syslog.

Thanks.

---

### Post by Jouke74 on 2008-08-01
DMA is direct memory access of the HD (controller), when he loads stuff the computer crashes, he can't swap...
I would still do a memtest and HD controller test too.

---

### Post by elmoosecapitan on 2008-08-01
Hi All,

Symptoms:
Rampant crashing during normal usage, heavy usage, safemode, booting, gerb.
Excessive (I mean really excessive) hard drive heat.
Flashing 'Caps Lock' light, not 'Scroll Lock', when crash had occurred.
During crash, all hardware and software froze (minus single flashing light).
Crashes occurred anywhere from 20 second frequency to 90 minute frequency. Frequency is defined as time from last boot.

History:
No traces or odd notes in /var/log/ files; most were checked.
Stable Kernel; late kernel update was over a month prior to incident.
No updates for ~3 days preceding onset of symptoms.

Computer:
New (2008 April) T61 ThinkPad with 64-bit Ubuntu.

Testing:
Past RAM test and all diagnostics, including HD, that come native with Ubuntu and ThinkPad. Considered HD to be problem because of excessive heat.

Conclusion:
Lenovo replaced the thermal fan, no other hardware replaced.

Belief:
Fan had epic failure, resulting in overheating of key components and hence crashing. New fan is no longer silent, but heat displacement is pretty effective (it's pretty strong).



cheers

---

