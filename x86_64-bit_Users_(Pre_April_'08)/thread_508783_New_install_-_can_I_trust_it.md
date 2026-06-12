---
title: "New install - can I trust it?"
date: 2007-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by 56seeker on 2007-07-24
Hi all..

I'm trying to build an Ubuntu 64 server for the purpose of hosting VMware server.

It's a new machine, on new hardware; and it's driving me nuts.

It's based on 4 250 Gb SATA disks, which I've set up in software RAID.

/boot 150Mb RAID1
/root      9 Gb  RAID5
/var     1.1 Gb RAID5
/VMFS (virtual machine store) 720 G

The only commands ran on the machine up to now are:

apt-get update
apt-get dist-upgrade
apt-get openssh-server

Setting up the RAIDs was a NIGHTMARE in it's self; but hopefully I've got it somewhere right now.
However; I'm left with three problems which leave me unwilling to progress further with the project:

1) It won't shutdown  or reboot cleanly. I can see that RAID disks fail to unmount while shutting down.
2) It won't reboot. It'll shut down, but I get wierd error messages on the restart and I can't access a terminal
3) Very intermittant response to SSH or putty. Some times I can get in; most times it's connection refused by host.

So my first question is what logs should I be looking at to try to trouble shoot all this? I realise that this post is lacking all kinds of details; but I'd be gratefull for a few pointers to start trying to sort it all out.

---

### Post by tgm4883 on 2007-07-24
if you just installed why are you doing a dist-upgrade?

Check /var/log/syslog and /var/log/messages

---

### Post by 56seeker on 2007-07-24
I do the dist-upgrade on the thoery that the CD is by definition out of date. This is backed up by the command resulting in a 70 mb down load.

Here's the log messages. I had to log in to my windows desktop from my Ubuntu lap top to get a connection to my Ubuntu server; and even then I lost connection umpteen times :([PHP]seeker@fakefarm:/var/log$ view syslog

Jul 24 22:16:12 fakefarm syslogd 1.4.1#20ubuntu4: restart.

Jul 24 22:16:12 fakefarm kernel: Inspecting /boot/System.map-2.6.20-15-generic

Jul 24 22:16:13 fakefarm kernel: Loaded 25649 symbols from /boot/System.map-2.6.20-15-generic.

Jul 24 22:16:13 fakefarm kernel: Symbols match kernel version 2.6.20.

Jul 24 22:16:13 fakefarm kernel: No module symbols loaded - kernel modules not enabled.

Jul 24 22:16:13 fakefarm kernel: [    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)

Jul 24 22:16:13 fakefarm kernel: [    0.000000] Command line: root=/dev/md2 ro quiet splash

Jul 24 22:16:13 fakefarm kernel: [    0.000000] BIOS-provided physical RAM map:

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7e2fc00 (usable)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 00000000b7e2fc00 - 00000000b7e3eaab (ACPI NVS)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 00000000b7f2fc00 - 00000000b7f30000 (ACPI NVS)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 00000000b7f30000 - 00000000b7f40000 (ACPI data)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 00000000b7f40000 - 00000000b7ff0000 (ACPI NVS)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 00000000b7ff0000 - 00000000b8000000 (reserved)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 00000000fed13000 - 00000000fed1a000 (reserved)

                                                                               1,1           Top





login as: seeker

seeker@192.168.2.50's password:

Linux fakefarm 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64



The programs included with the Ubuntu system are free software;

the exact distribution terms for each program are described in the

individual files in /usr/share/doc/*/copyright.



Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by

applicable law.

Last login: Wed Jul 25 00:38:45 2007 from 192.168.2.103

seeker@fakefarm:~$ view /var/log/messages

Jul 24 22:16:12 fakefarm syslogd 1.4.1#20ubuntu4: restart.

Jul 24 22:16:12 fakefarm kernel: Inspecting /boot/System.map-2.6.20-15-generic

Jul 24 22:16:13 fakefarm kernel: Loaded 25649 symbols from /boot/System.map-2.6.20-15-generic.

Jul 24 22:16:13 fakefarm kernel: Symbols match kernel version 2.6.20.

Jul 24 22:16:13 fakefarm kernel: No module symbols loaded - kernel modules not enabled.

Jul 24 22:16:13 fakefarm kernel: [    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)

Jul 24 22:16:13 fakefarm kernel: [    0.000000] Command line: root=/dev/md2 ro quiet splash

Jul 24 22:16:13 fakefarm kernel: [    0.000000] BIOS-provided physical RAM map:

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7e2fc00 (usable)

Jul 24 22:16:13 fakefarm kernel: [    0.000000]  BIOS-e820: 00000000b7e2fc00 - 00000000b7e3eaab (ACPI NVS)

"/var/log/messages" [readonly] 1905L, 173969C                 1,1           Top
[/PHP]

---

### Post by tgm4883 on 2007-07-24
If thats why your doing the upgrade, then you should be doing

sudo apt-get upgrade

Because if you do 

sudo apt-get dist-upgrade

then you are upgrading feisty to gutsy.

Perhaps that is why you are having problems

---

### Post by 56seeker on 2007-07-24
Thanks for the reply.

I hadn't considered the possibility that I may be inadvertedly beta testing Gutsy!

However; I'm on about my twientieth install trying to sort this out; and I've noticed that I get the problems noted above wether I update or not; and that if I perform an apt-get upgrade instead of a dist-upgrade then two packages are held back.

Should I be checking any other logs to trouble shoot the RAID and SSH problems?

I should point out that I tested my install plan on a 34 bit virtual machine intensively without problems; so I'm reasonably convinced it's either hardware related or that there's someting different with 64 bit Ubuntu I'm not taking into account.

---

### Post by kuja on 2007-07-24
No, that won't switch you over to gutsy, despite the misleading name. It just behaves a bit differently when resolving dependencies. 

From the man page:  
dist-upgrade
          dist-upgrade in addition to performing the function of upgrade, also
          intelligently handles changing dependencies with new versions of
          packages; apt-get has a "smart" conflict resolution system, and it
          will attempt to upgrade the most important packages at the expense
          of less important ones if necessary. The /etc/apt/sources.list file
          contains a list of locations from which to retrieve desired package
          files. See also apt_preferences(5) for a mechanism for overriding
          the general settings for individual packages.

---

