---
title: "a8n-sli premium fully supported?"
date: 2006-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by rtl on 2006-02-14
I have a a8n-sli premium with a 4800+/4gb/4*sata2 as raid0/1 that I'm currently running FreeBSD 6.0 on. I say running, but it is having some issues, firstly it fails to recognise the full 4gb of ram, it only sees 3gb (this appears to due to the PAE support or lack of it). Secondly, when running some heavy database analysis (Postgres/Python/C) it appears to be leaking memory big time. No-one on the FreeBSD lists has been able to help, so I'm considering the drastic step of installing another distro (drastic because there are some large databases on the box that I will have to dump/restore, which will take a loooong time). I am using Ubuntu on my dev laptop and love it, so Ubuntu 64 might be the way to go. I'm not interested in installing a UI - it's a server, so cli is preferred. 

The question is then, does Ubuntu 64 fully support this m/b  combination, allowing the use of >= 4gb of ram, the on-board nVidia raid 0/1 and full smp support for the dual core cpu? I've seen other people on the forum with this m/b but no-one using the same setup.

---

### Post by RAOF on 2006-02-14
The -amd64-smp kernel should support your full 4gb, with dual core support.
You'll need to do some fiddling with the initial setup for your nvidia raid - it'll be seen as four independant drives.  The installer supports LVM though, so you should be able to set up some form of mirroring/striping with that.

---

### Post by digitalsy on 2006-02-14
I'll chime in with my 2 cents even though hardware wise it's not exactly what you've got. I've got an A8N-SLI Premium with an Opteron 170 (dual core) and 2GB ram. the amd64-smp kernel detects both cores, and all 2GB of ram. I would see no issue with it detecting an additional 2. I haven't tried raid yet, but usually these onboard raid is not true hardware raid. It's software emulated so you're probably better off using linux's own software raid implementation.
 [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mdadm&searchon=names&subword=1&version=breezy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mdadm&searchon=names&subword=1&version=breezy&release=all")

[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html)

---

### Post by rtl on 2006-02-15
[I]RAOF: The installer supports LVM though, so you should be able to set up some form of mirroring/striping with that.
[/I]
I'm not tied to the nVidia raid, but that's one thing that FreeBSD does support and I would think that even a partial h/w raid would be faster than s/w only -  but a quick google failed to turn up any comparisons. 

I have heard the odd horror story wrt LVM and that's a bit of a concern.

*digitalsy: I would see no issue with it detecting an additional 2(gb of ram).*

That's what I thought as well, but there is an issue of many (all?) boards putting buffers, etc in the 3-4gb address space. Some m/b support moving/remapping these buffers to beyond the 4gb range, but as I found out not all *nix support it. I've seen similar questions on other lists/fora (e.g. RH officially says that chipset it is not yet tested/supported for 64 bit).

---

### Post by RAOF on 2006-02-15
I don't know how much the nVidia raid does in hardware, but I don't think it's very much.  LVM should be practically as fast, with the advantage that you can dynamically add/remove space to the array.

About the 4gb RAM issue - someone on this board recently posted that they'd got their (different) setup to access 3.8 gb of their 4 with some specific bios options.  If it doesn't work out of the box, something similar should.

---

### Post by rtl on 2006-02-15
Hmmm, maybe the 64 bit Live CD would be the best way to answer the ram question at least.

---

### Post by RAOF on 2006-02-15
A fine plan.

---

