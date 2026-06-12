---
title: "Crashing"
date: 2008-07-26
forum: x86 64-bit Users
---

### Post by melenor on 2008-07-26
My installation of ubuntu 8.04 seems to crash every so often, sometimes, i can go a month without a crash, other times, i have 4 a day. I have tried reinstalling, i did this twice, My system is

ubuntu 8.04.1 64-bit
ATI X1800
Athlon X2 3000+
nforce 4
Audigy 1 ES
750GB-Data
250GB-Ubuntu
Logitech MX610
Belkin Wireless G USB Network Adapter F5D7050

several people i know have looked at it, and seem to think that the cause might be the Belkin adaptor or the Logitech MX610, I am wondering how i can find the exact cause of my crash, and how i could go about fixing it.
Also a side note, when ever it crashes the Caps Lock on my keyboard blinks.

---

### Post by Yellow Pasque on 2008-07-26
> Also a side note, when ever it crashes the Caps Lock on my keyboard blinks.
Sounds like a kernel panic. My money's on the Belkin adapter as well. If you would be so kind as to post the output of:
```
sudo lshw -C network
```

Also, check /var/log/messages to see if the system logged any useful info before locking up.

---

### Post by melenor on 2008-07-26
*-network               
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:11:50:b2:17:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=IEEE 802.11b/g


Looking at /var/log/messages, i see alot of stuff and i am unsure how to tell what is useful and what is not also there is a message.0 in /var/log/ as well.

---

### Post by Yellow Pasque on 2008-07-26
gzip the files and attach them or use a site like pastebin.

I read a bit about the wireless chipset (Ralink rt2500) and the Linux drivers appear to be a bit unpolished (especially with SMP kernels). You might try the latest code:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

---

### Post by melenor on 2008-07-27
alright here are the messages

---

### Post by melenor on 2008-07-28
Anyone make sense of the log files, or any ideas on how to stop the crashes?

---

### Post by melenor on 2008-07-30
Anyone help would be very useful. Please?

---

### Post by Cappy on 2008-07-30
Here are the two kinds of errors I see:
> Jul 25 21:46:37 QWERTY kernel: [11193.219134] nautilus[6093]: segfault at d9000034 rip 7f87e58e6f0f rsp 7ffff0e93c70 error 4
Jul 25 21:46:37 QWERTY kernel: [11193.751582] [fglrx] interrupt source 10000000 successfully disabled!
Jul 25 21:46:37 QWERTY kernel: [11193.751588] [fglrx] enable ID = 0x00000000
Jul 25 21:46:37 QWERTY kernel: [11193.751591] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000009
Jul 25 21:46:37 QWERTY kernel: [11193.751603] [fglrx] interrupt source 20008000 successfully disabled!
Jul 25 21:46:37 QWERTY kernel: [11193.751604] [fglrx] enable ID = 0x00000000
Jul 25 21:46:37 QWERTY kernel: [11193.751606] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000008
Jul 25 21:46:40 QWERTY kernel: [11196.479219] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 25 21:46:41 QWERTY exiting on signal 15
Jul 25 22:19:53 QWERTY syslogd 1.5.0#1ubuntu1: restart.
and
> 
Jul 26 21:54:56 QWERTY kernel: [41963.310903] SoftMAC: Open Authentication completed with 00:1c:10:ce:b5:3e
Jul 26 21:54:56 QWERTY kernel: [41963.345629] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jul 26 21:54:59 QWERTY kernel: [41965.426483] SoftMAC: Open Authentication completed with 00:1c:10:ce:b5:3e
Jul 26 21:54:59 QWERTY kernel: [41965.448106] SoftMAC: Open Authentication completed with 00:1c:10:ce:b5:3e
Jul 26 21:55:07 QWERTY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Jul 26 21:55:07 QWERTY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Jul 26 21:55:07 QWERTY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Jul 26 21:55:55 QWERTY syslogd 1.5.0#1ubuntu1: restart.


I also noticed the ACPI isn't loading so you may want to try turning that off with
```
acpi=off
```
in grub. [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) gives additional information on editing grub's menu.lst

It's either the wireless or the fglrx but I don't know which.

---

### Post by melenor on 2008-07-30
where do i put the 
Code:
acpi=off

I don't think it is fglrx because i was using that before all the crashing started. It started after i got some upgrades, New Mouse, WiFi Adaptor, and Hard Drive, i have checked Hard Drive and that is not it.

btw how did you get the box around the code, i have tried figureing it out, but haven't been able to.

---

