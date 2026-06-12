---
title: "Crunched Filesystems on Nforce 570 Ssytem"
date: 2008-12-23
forum: x86 64-bit Users
---

### Post by bundwallah on 2008-12-23
I installed Ubuntu Studio 8.10 (64Bit)Two weekends ago.  It was beautiful, fast, responsive, feature rich, yet unstable.

Two days after initial install, I powered up my system to find that that /home was crunched.  I couldn't restore the filesystem, so I did a reinstall.  At that point I had no data on it as I was still configuring and testing the system.  A reinstall wouldnt take too much time.

Two days after my rebuild I lost "/".  Very frustrating.  Sensing that there may be a problem with my PC.  I did an install of WindowsXP 64 Bit edition.  It has been running flawlessly for 1 week.  So, I can surmise the hardware is OK.

Here's my setup. 

ASUS M2NE - SLI Deluxe (NForce 570 chipset)
Athlon X2 5000+
8GB RAM
2 * 160GB SATA2 (In RAID 0, the first time I installed, RAID 1 on the second install) FYI  I used the built in RAID on the ASUS board.

1 * 500GB SATA2 (data drive only)
1 * 750GB SATA2 (data drive only)

Having had two strokes of bad luck with Ubuntu but flawless operation on WindowsXP (go figure).  I'd say the chipset drivers might be at fault.  I could go with a non-RAID setup for the system drives but I'm too used to RAID 0 Speed.

To be clear, the filesystem issues resided with the RAID sets on the 160GB drives only.  The two "data" drives were OK.

My questions therefore. 

1.) Anyone experience a similar problem with their Nforce 570 based system?

2.) Any suggestions on upgrading the chipset drivers?  Nvidia's site doesn't have Ubuntu Specific binaries.  See here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Anyone try to upgrade the drivers?  Any success?

I'd really like to make Ubuntu my main system and run anything Windows based in VirtualBox, which ran beautifully before my filesystems died.  :(


About me.  I'm fairly proficient in Linux, not a noob but nor am I an expert.  My background is Windows NT - 2k3, AIX 4.3.  HPUX 11.  RHES 3.0.  So, don't worry about dumbing down your replies. :)

Thanks in advance.

---

