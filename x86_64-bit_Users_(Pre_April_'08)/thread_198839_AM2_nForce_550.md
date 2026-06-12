---
title: "AM2 nForce 550"
date: 2006-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by glocksout on 2006-06-17
I just bought a new system last night that is an MSI nForce 550 chipset with an AM2 3500 CPU. The GPU is a 7600GS.

I am setting up a dual-boot with XP pro. I installed XP and then installed Ubuntu on a clean partition and set up Grub. When I boot Ubuntu, the load screen will stop and I'll get an error about the video and x server.

I put in the LiveCD and the same error came up.

I read somewhere that the AM2 may not be supported yet. Is this what is wrong?

---

### Post by TJInc. on 2006-06-18
Hi Glocksout,

I have the ASUS M2N32-SLI motherboard with the AMD64 X2 4200+ CPU (AM2).

I had nothing but problems, with the Live 64 bit CD, Live 32 Bit CD and Alternate 64 Bit CD (text mode). after 3 days of frustrations, I downloaded Fedora Core 5, and it all installed as normal, it even recognised my Raid-0 drives as one drive as it should. 

Sorry, but I'd wait for the next version of Ubuntu for 64 bit processors. I must say that the Package Update installer, fonts and themes look much nicer under Ubuntu 6.06, than Fedora. But, I suppose there is nothing stopping me from installing the Ubuntu themes, fonts and colors into Fedora.

Just to be fair, you'll probably find that ALL the Linux distributions are a little flakey with (AM2). If you want stability, you may want to try Gentoo 64 bit edition, or possibly even SUSE 10.1. All I can say is that Ubuntu 64 bit edition is the worst out the major distributions, I've seen to date. It needs a lot more work to make it stable and usable.

Best of Luck...

---

### Post by Jason_25 on 2006-06-18
Sounds like you just have video problems.  Have you tried the vesa driver yet?

---

### Post by TJInc. on 2006-06-18
Vesa Driver ?

Not quite sure what you mean. How would you use the VESA driver, if you can't even boot into Ubuntu using the Live CD properly ?

Has anyone out there managed to get Ubuntu 64bit working in a stable fashion on a nForce 550 chipset or in my case the nForce 590, with the amd64 X2 (AM2) 4200+ or similar. If they have, I'd really appreciate if one could explain how it's done (HOWTO). Ubuntu was my favourite distribution, back in my old Pentium 4 days. 

Thanks very much.

---

### Post by Jason_25 on 2006-06-18
[QUOTE=TJInc.]
Not quite sure what you mean. How would you use the VESA driver, if you can't even boot into Ubuntu using the Live CD properly ?
[/QUOTE]
I'm not sure what _you_ mean.  If you have gotten far enough to get an error about the x server, the boot process is finished.  You are then free to switch to a virtual console to troubleshoot your problem.

---

### Post by TJInc. on 2006-06-18
Hi Jason_25,

I''ll try to print out some of the logs next time.

In the mean time, I'm also running the same graphics card as glocksout, the NVidia 7600GS. Maybe there is something there, what I've noticed before is the system usually hangs with a blank screen prior to booting X-Windows, I've even tried the VGA option with no success.

Thanks.

---

### Post by Jason_25 on 2006-06-19
[QUOTE=TJInc.]Hi Jason_25,

I''ll try to print out some of the logs next time.

In the mean time, I'm also running the same graphics card as glocksout, the NVidia 7600GS. Maybe there is something there, what I've noticed before is the system usually hangs with a blank screen prior to booting X-Windows, I've even tried the VGA option with no success.

Thanks.[/QUOTE]
That doesn't sound good.  Verify that you burnt your cd's at 24x or lower and you have run memtest, verified the hardware is stable, etc.  Also, you could try to boot without acpi maybe.

---

### Post by ieccles on 2006-06-29
I've been running Ubuntu 6.06 64 bit version with an AMD64 3200 AM2 processor for a few weeks now with no problems.  I did nothing special, just installed from the 64 bit Live CD.

However, I am running an nForce4 chipset.  I know up until 6 months or so ago, nForce4 had little support in Linux, but has since become fairly well supported.  I expected the same to be true for the nForce5 chipset, so I bought a board with the nForce4 chipset to avoid any compatibility headaches.

I know this doesn't particularly help you too much, as I doubt you want to buy yet more new/expensive hardware just to get Ubuntu 6.06 running, but maybe it can help out people thinking of moving to AM2.

---

### Post by go.lem on 2006-10-02
Hello!

I use:
ASUS M2N32 WS Professional nForce 590 sli with pxi-x - slots
AMD X2 3800+ EE (65Watt) dualcore cpu
ASUS GeForce 7600GS Top Silent
3ware 8002-sata-raid-card
1024MB G.Skill DDR2-800MHz RAM
ATA-DVD-drive

*The problem with installations is not the vesa-x-server-driver problem _but_ a bug in the interupt-controller-handling of the motherboard-bios

*The problem is not a AM2-cpu-socket related thing. The nForce4 Motherboards function very well without problems, but it is a nForce 5xx (500 570 590 sli) related thing!!
---
I got the boot-problems solved with the bootparameter typed at the end of the installmenue bootparameter promtline (after hitting F6 in ubuntu 6.06): "noapic" just that and in my case, for i use a dual-core cpu "maxcpus=2" (hit F6, scroll to the end of the bottpromt-line and typ in (add): e.g.:: 

noapic maxcpus=2

I run into further problems with the install-process. My machine hangs in the copiing-process after partition, after creation of a user-account, after network-configuration and after fetching deb-packets by internet.

It is probably a kernel-related problem.

The mobo has a bios-apic-bug (still in the bios 0501.bin biosversion!!) and asus seems not to care for linux support (hey asus-guys trie not to corrupt my good oppinions towards ASUS-Products, PLEASE CARE!!!)

I got the server-32bit version of ubuntu 6.06.1 running but no ubuntu desktop versions: 32bit, 64bit 32bit-6.06.1, ubuntu, kubuntu, xubuntu, edubuntu ....

just an other trial pending ...](*,) 
best regards go.lem

---

