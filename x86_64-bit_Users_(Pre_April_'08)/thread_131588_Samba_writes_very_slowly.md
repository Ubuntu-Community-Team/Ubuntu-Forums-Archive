---
title: "Samba writes very slowly"
date: 2006-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by biovore on 2006-02-16
I installed the 64bit kubuntu system on my box the other day. I setup samba, and it apears to be working.. I can authenticate and read the files just fine from the server. But on my 32bit kubuntu box, when I try to write to the samba share I get the follow note in my dmesg. The write speed is only about 100kb/s (very slow considering its on GB ethernet) smb_writepage_sync: failed write, wsize=4096, write_ret=-512 (this is on client box) My MS boxes also have slow issues when tring to write to the 64bit kubuntu box. Any Ideas on what this is tring to tell me. Is something setup wrong? I didn't have this problem with the old box (32bit amd with debian on it) note: If I use ftp, there are no speed problems. After some hacking at the problem, it appears to be a problems with the raid card in my box. (ARC-1220) when I write to a share that is not on that card, it works just fine. So back to the drawing board to figure out whats with samba + the ARC-1220 (PCI-e) card.. unfortionly there isn't any debug from what I can tell.. :-/

Note: To get the ACR-1220 card to work in ubuntu to have to do some nasty kernel hacks to get the dam thing to work..  The linux-kernel-sources that come from apt seem to be plan sources from kernel.org..  I also found a kernel-patch packages and installed the "debian" kernel patches..  Then I added the ARCMSR module to the kernel source tree (by hand no patch system for there tarded driver) and rebuild that kernel using the config file /boot/config`uname --kernel-version`.

It seems to work.  But this samba problems has me licked.

---

