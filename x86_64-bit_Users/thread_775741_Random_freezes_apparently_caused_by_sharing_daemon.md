---
title: "Random freezes apparently caused by sharing daemons"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by hizzk on 2008-04-30
Hi, I'm new to the forum but I've been using Ubuntu full-time for a couple of years now.

In all that time, I've never encountered this problem:

I just did a reinstall from Gutsy to Hardy (both 64-bit) and set up Samba to share files on my home network. I started getting weird system locks that ended in total freezes (no Alt+F1, ctrl+Alt+Bksp, keyboard, or even ssh, though mouse works sometimes temporarily).

I had some other weird instabilities and chalked it up to a wonky install, so I just went ahead and formatted and started over. Unfortunately, the freezes remained.

So, I ssh tunneled in with another computer and left 'top' running while I went about my business to see if something was acting strangely. Sure enough, smbd started spawning processes left and right until it overwhelmed the system (it usually took about 20 min. to reach a lock).

Based on that information, I uninstalled Samba and tried switching over to Netatalk (the one in the repos), since my other computers are Macs. Everything seemed fine until *it* (in the form of afpd) started spawning processes like crazy with eventual lockups.

I've since uninstalled Netatalk as well and haven't had any freezes since. However, this is an unacceptable solution since it makes my media server an island, so to speak.

Does anyone have any idea what could be causing this, or point me to some logs that might shed some light on the issue? Also, just to mention: this problem has occurred with and without compiz-fusion enabled.

(To note: I think Hardy is an amazing release with some really great new features. Kudos to the devs for all of their hard work.)

Update: I got another freeze overnight without samba or netatalk installed. /var/log/messages shows no new messages, and I can't find any errors in any logs I've checked (user.log, kern.log, dmesg, daemon.log, acpid, auth.log, syslog, Xorg.0.log) now I'm really confused. any info?

---

### Post by ConstantC on 2008-05-01
Hi Hizzk,

after your update things start to get familiar: random freezings. Because I'm a newbie I and the machine freezes completely I could not check the logs. Things happen when browsing the LAN or just browsing with Firefox.

config: AMD64-3500/939, Asus A8V, 2x512, 160GbSATA, ATi9600
dual boot with XP, installed Ubuntu 8.04 over SuSe-101

---

### Post by Yahuda on 2008-05-01
I'm not sure but its reason could be Compiz Fusion. 

[http://forum.compiz-fusion.org/showthread.php?t=8065](http://forum.compiz-fusion.org/showthread.php?t=8065)

---

### Post by hizzk on 2008-05-01
I had heard about the possible link to Compiz-Fusion, so I tried disabling it and the freezes remained. I also continued getting the freezes even with all sharing protocols uninstalled, only in that case whatever process happened to be active when it decided to freak out would start the process spawning thing.

I have since reformatted and dropped back down to Gutsy (leaving my /home partition intact) and haven't had any more problems. I considered filing a bug report, but none of the logs showed anything, so I don't imagine it would get much attention. It was highly reproducible for me (as in, every half hour or so), but there didn't appear to be any traces of a problem.

As much as I enjoyed using Hardy, I'm afraid this bug is a major deal-breaker for me and I'll be sticking with Gutsy.

I'll keep an eye on this thread, though, in case I can provide any info that might help anyone trying to tackle the issue.

---

### Post by j2fraser on 2008-05-01
For me, the problem was that the distribution upgrade to Hardy didn't upgrade Grub to use the new kernel. At least, that appears to have been the case, since editing /boot/grub/menu.lst, and adding an entry for the 2.6.24 kernel (and rebooting) *seems* to have fixed my problems. 

FYI - I'm using AMD64 Hardy in a dual boot configuration w/XP. I'm using fglrx restricted drivers, no compiz.

---

### Post by AnotherFineMess on 2008-05-02
I had the same annoying glitches of high iowaits (constant Hard Disk use) causing the system to become unresponsive. I tried unistalling the Tracker Deamon, Fuse Server, disable Effects etc. but nothing seemed to actually make things better. I tried compiling the new kernel (2.6.25) though it did not work 100% ok. In the end  i downloaded the kernel deb binaries from the Kernel archives for my AMD64 processor at [http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/]("http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/") which gave a breath of fresh air to my system. No more constant Hard Disk use...

[COLOR="Red"]You should uninstall your Graphics Card Drivers before rebooting and reinstall them after booting with your new kernel using the restricted drivers manager or with EnvyNG
[/COLOR]

Note that the correct files for the AMD64 architecture are:
[linux-headers-2.6.25-1-common_2.6.25-1snapshot.11177_amd64.deb]("http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/linux-headers-2.6.25-1-common_2.6.25-1snapshot.11177_amd64.deb")
[linux-image-2.6.25-1-amd64_2.6.25-1snapshot.11177_amd64.deb]("http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/linux-image-2.6.25-1-amd64_2.6.25-1snapshot.11177_amd64.deb")

When these 2 deb's are installed reboot and your new kernel will load as default from the grub menu

---

