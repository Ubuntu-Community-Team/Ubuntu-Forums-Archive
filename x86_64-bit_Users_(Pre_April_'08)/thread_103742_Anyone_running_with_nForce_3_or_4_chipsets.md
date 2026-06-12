---
title: "Anyone running with nForce 3 or 4 chipsets?"
date: 2005-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by SolidAndShade on 2005-12-14
Hey everyone,

I'm considering getting a Biostar iDeq 330p mini computer with the nVidia nForce 4 chipset. Does anyone reading have the above chipset (or better yet, the above system)? Do the onboard netrworking and sound systems work all right? What about the SATA controller. I've had a hard time finding information about Linux compatability with the new nForce chipsets. Thanks.

---

### Post by rhys_jones on 2005-12-14
I have the nForce 4 chipset.  Just installed yesterday and audio/networking are fine.  The SATA is recognized as a SCSI device, but no issues with that so far ...

---

### Post by scaine on 2005-12-14
I've got an Nforce 3 chipset on my Epoc motherboard running an AMD 4200+ Dual Core with AGP graphics, SATA and UDMA drives.

I've not had a single hardware issue so far.  Couple of funnies with running a 64-bit distro (never done this before) and I might abandon it due to a fundamental lack of understanding, but the hardware support has been perfect so far.

---

### Post by darkpark on 2005-12-14
i've got the nforce 3 250 chipset and no problems here.  it's a Gigabyte k8nsc-939 with an amd64 3500+

---

### Post by RAOF on 2005-12-14
nForce 4 works out of the box.  You shouldn't have any problems.

---

### Post by grsing on 2005-12-14
I've got an NForce 4, works fine (haven't tested the sound, I've got a PCI sound card, but I have no reason to think it doesn't work, everything else worked out of the box).

---

### Post by jon_gunnar on 2005-12-15
[QUOTE=SolidAndShade]Hey everyone,

I'm considering getting a Biostar iDeq 330p mini computer with the nVidia nForce 4 chipset. Does anyone reading have the above chipset (or better yet, the above system)? Do the onboard netrworking and sound systems work all right? What about the SATA controller. I've had a hard time finding information about Linux compatability with the new nForce chipsets. Thanks.[/QUOTE]

Running Asus A8N-SLI Deluxe card, sound and networking works OK. Sata no problem. 
Asus NVidia 6600 PCIe card. Grafics without any problem at all.
Only issue is that If I try to put in PATA disks everything hangs.
But the rest is go-go :smile:

---

### Post by SolidAndShade on 2005-12-15
Thanks guys. Is anyone running with nForce 4 and a PCIe video card? I just did a search and saw some people saying they had trouble with those cards under nForce 4, but others seem to be doing fine. My particular interest is in the Geforce 6600 GT PCIe card, and someone said that the nVidia card was having trouble when coupled with the nForce 4 chipset. I'd appreciate any info you can share.

---

### Post by olivierp on 2005-12-15
[quote=SolidAndShade]Thanks guys. Is anyone running with nForce 4 and a PCIe video card? I just did a search and saw some people saying they had trouble with those cards under nForce 4, but others seem to be doing fine. My particular interest is in the Geforce 6600 GT PCIe card, and someone said that the nVidia card was having trouble when coupled with the nForce 4 chipset. I'd appreciate any info you can share.[/quote]

Asus A8N-SLI (nForce4), GeForce 6200 PCI-express, 2Gb RAM (4 x 512Mb)
Network, Sound, SATA, Graphics (Nvidia's 1.0-7676 drivers) working fine ... as long as the system doesn't get too hot. The only issues I had were caused by a failing chipset fan (known problem of this specific motherboard) and its "integrated" overclocking.

---

### Post by wjp.reg on 2005-12-15
Well what the heck is wrong with me then?

I just bought the Gigabyte GA-K8N51GMF-9 (socket 939) with geFORCE 6100 and nFORCE 430 and I'm unable to boot into graphics mode after installing 64-bit ubuntu.  Onboard LAN identified, but sound and more importantly, onboard video is not recognized.

I was able to boot into init 5 using Puppy 1.5 (32-bit) and SuSE 10.0 (32-bit and 86_64-bit) with LAN and Video working, but onboard 8-channel HD audio no-go.

I figured I have to wait until some drivers are updated. :)

guess I should update my signature below..

---

### Post by mesilliac on 2005-12-15
I'm using a PCIe GeForce 6600 GT with an nForce 4 chipset (Gigabyte GA-K8NF-9 motherboard) and everything is working fine :).

---

### Post by rhys_jones on 2005-12-15
My PCI-e card is actually an ATI 300 se, I had some initial issues with the installation but they were eventually resolved by perusing this board and looking for others that had had similar problems.  So I can't answer to the Geforce card, but I always though they actually got better results than Ati? :confused:

---

### Post by handy on 2005-12-18
I'm running a self built system comprised of the following:  GA-K8NS Ultra 939 (nForce 3), 3500+, 2Gig DDR 400 Dual Channel, agp 6800GT 256Mb, SBLive 5.1, Booting from a WD 80Gb PATA primary master, dual booting to Maxtor 160 Gb primary slave with 2 ntfs (& 1 fat32 partitions for easy share between systems when required), WD Raptor 36Gb SATA ntfs, Pioneer DV110D.  I have a video capture card that I haven't got around to setting up yet.

The only trouble that I have had is getting the sound right, I use both onboard & PCI in windoze, the onboard is used only for VOiP.  I had to turn off the onboard in the BIOS, (I know you can change a setting, but it changed itself back so I killed onboard.) & do this:

  [http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

to make the sound do the right thing.  If you have sound trouble I can't recomend using the above link highly enough. :KS 

I also highly recomend "Automatix"  for easy installation of the nVidia proprietory drivers, apart from all the other things that it makes easy.

Unreal Tournament 2004 runs at 1600x1200 smoothly even when there is a lot of action.  That is the ultimate test as far as I can see.

If I was buying today I wouldn't change a thing. :p 

Cheers,

handy

---

### Post by grsing on 2005-12-18
[QUOTE=SolidAndShade]Thanks guys. Is anyone running with nForce 4 and a PCIe video card? I just did a search and saw some people saying they had trouble with those cards under nForce 4, but others seem to be doing fine. My particular interest is in the Geforce 6600 GT PCIe card, and someone said that the nVidia card was having trouble when coupled with the nForce 4 chipset. I'd appreciate any info you can share.[/QUOTE]

That's the exact card I'm running, on an nForce 4, works fine.

---

### Post by fuddjaf on 2005-12-18
i am also running nforce4 (abit kn8 mb) and pcie geforce 6600 gt (evga).  sound, video, sata... everything worked right away, though i havent tried the dual view monitors on the video card; ive read that can take a little tweaking.

---

### Post by scunc_dvl on 2005-12-20
Got a gb GA-K8NF-9 (Nforce4x the slow one) and Nvidia GeForce 6600LE PCIe. Haven't been able to test the SATA yet, certainly hope it works when I get around to it, but the BSOD with the 6600 graphics card was the biggest mess.

The kernel I compiled a few days ago (My failed attempt at a badram patch, since it patches 386 and not amd64 code :P ) caused me to go back to VESA mode and download the latest NVidia driver package ( 8174, pkg 2 I believe ), I thought they didn't work...

Gee whiz, found out later I *wasn't supposed to install 32-bit compatibility* during its installation! (Good thing I knew about kernels that time I used it too :P ). Whoops :P Took another trip to the forums to get that detail straight, after another day messing around with *xorg.conf* like I always in previous BSOD fixes. Got it working though. Don't make that mistake :P


I wonder if installing the chipset drivers from Nvidia.org would make any performance difference at all? I believe I downloaded it for no reason, thinking it would give me more features, but I looked at the 'readme' and thought not so I stuck with the stock chipset stuff (Even though the output in 'dmesg' (kernel log) does have a lot of junk in it I'd like to see go away).

[BTW, those features I was thinking of was the fact the Realtek AC'97 thing has Karaoke software in windows, thinking it may be hardware based, since many real-time sound processes used to be quite processor intensive... I get carried away with that software and play CD's, sound effects and even entire games transposed half an octave down (!) *laughs* Support for that would be great for me then. ]

---

### Post by bonzodog on 2005-12-20
I have an MSI K8N Neo Platinum Nforce 3 socket 754 with on-board sound and GBLan - i chose it specifically because the boards are famed for working out of the box in linux. The sound is 5 channel surround, and it's recognised as an Nvidia CK8S sound card. The Graphics card is a PNY GeForce 6200GT AGP 256MB, but would only  run graphics without the 3D driver in 'vesa'. I installed the 3D drivers as one of the first things I did, and it's been fine since. I have 1GB RAM on board this and an AMD64 3000+.

---

