---
title: "New ubuntu build using AMD 64 CPU"
date: 2006-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by j0eb0b on 2006-08-14
i am looking for some advice about a new computer build that I am beginning. 

While all the hardware is not yet determined, it is going to be a fairly high end build around an AMD FX-55 processor.  Current generation components (Video card, memory, ect.) will be used.  i really like Unbuntu (running on my older AMD 32 bit overclocker with two year old hardware) but am concerned about driver support with new hardware.  I don't want to fall back to XP but don't want to cripple my new build either  Some of the questions outstanding are:

Nvidia or VIA based MB?
ATI or Nvidia video?
Soundblaster x-FI sound card?
other modern devices (wi-fi, bluetooth, SATA, RAID, ect.)?

If I have to build as a dual-boot with XP first i will but Ubuntu is the future and am willing to work through now if there is a legitmate chance the I can successfully. What works and what doesn't?

Thanks, 
Joe

---

### Post by Grey on 2006-08-14
nVidia or Via:

Take your pick.  I have 3 A8V based computers that have been running for a few years.  Likewise, I also administer 3 nVidia based computers.

ATi or nVidia:

Take your pick.  My ATi computers work just fine, and I don't have too many outstanding issues, the main complaint is that they don't perform as well in Linux as they do in Windows.  Extremely bleeding edge cards take about a month to be supported.  nVidia should work just as well in Linux as they do in Windows.

Soundblaster X-Fi:

Should work fine.  Creative seems to be fairly decent about Linux support from my experience.

Wi-Fi:

Try to get something that doesn't use broadcom if you want native drivers.

Bluetooth:

Better than Windows in my experience.

SATA/RAID:

I have had my fill of RAID.  I did successfully manage to force a Promise TX2000 to work in Linux though, but it was an experience.  I might suggest software RAID, if you MUST have it.  I hear that Adaptec cards work well if you want a hardware solution.  As far as SATA is concerned, I've NEVER had a problem.  (other than a hardware nForce 4 problem.  In which case, it doesn't matter what OS you use).

In short, you shouldn't have much issue.  I've always considered the thing about Linux not supporting newest hardware to be a myth, unless you have some strange piece of hardware nobody cares about (like my $10 USB atheros wifi card I got at Fry's).

---

### Post by j0eb0b on 2006-08-14
Most of what you relate is good news, indeed,  Two further questions:

Any opinion about DFI LAN Party MBs in any of their forms using Ubuntu?  I am a longtime (though not manical) overclocker 

Ideas/experience with USB devices and Ubuntu?  I have a number of peripherals that are not absolute crap but are not apparently supported by Ubuntu (Debian) such as Visioneer 5800 USB scanner and HP 43xx digital camera.

Thanks,
Joe

---

### Post by kuja on 2006-08-15
I'm sure the motherboard won't make a lot of difference in Ubuntu. As per hardware, I'm on a fairly fresh build myself right now (well, the majority of the guts anyway). Unless something is the absolute newest out I would expect support for it. I hear a lot of people have had trouble with wifi, though many do seem to get it to work. (might take work though?) SATA will be no problem at all. I would most definitely avoid using your motherboard's RAID setup as well (it would be great if it were pure hardware RAID, but it's not)... use software RAID. According to [http://www.alsa-project.org](http://www.alsa-project.org) that sound card will not work!!

---

### Post by puppy on 2006-08-24
Don't bother with the Creative X-Fi - there won't be support for that card until at least the middle of 2007, if then... the M-Audio range of cards are well-supported however, and some of their products are fairly high-end (certainly favoured by musicians/podcasters etc anyways)

---

### Post by Hg80 on 2006-08-24
> 
Nvidia or VIA based MB?
Nvidia NF4 here and it works fine
> 
ATI or Nvidia video?
ATI is a no,no for Linux go for Nvidia as there driver support if great
> 
Soundblaster x-FI sound card?
X-fi has no Linux support yet so go for the older soundblaster
> 
other modern devices (wi-fi, bluetooth, SATA, RAID, ect.)?
Just becareful with wifi try looking on these forums

---

### Post by AllenGG on 2006-08-24
This is a very good question. Ask before you buy !
After 20 months with an ASUS mobo (VIA), an AMD64 CPU with 1.5G memory, an NVidia video, using the S-ATA drives (2) without the "Promise -Raid" controller. Ubuntu recognizes everything here, as does Knoppix-Live. Not so other Distros.
BUT, wi-fi has been a no-no, Broadcom didn't work. see previous.
Apparently "Startech"  has a[ _Network adapter_]("http://www.startech.com/Product/ItemDetail.aspx?productid=PCI555WG&c=CA") that works with Linux.
Used the onboard sound and Eth0 , works well. It was a premium board, and easy to assemble. 8)
Big important addition : U-P-S, had enough of power outages,
and, big plus, Ubuntu set it up without my bungling !:mrgreen:

---

