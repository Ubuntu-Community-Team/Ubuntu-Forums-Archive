---
title: "Linux on old Mac"
date: 2006-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by aneblanc on 2006-02-24
Hello,

I was just given an old Macintosh computer. Its specifications are not enough to install Linux in the version 5.10 that requires 128 MB of RAM and 1.8GB of disk space.

That Mac has a 200 MHz processor, a 2GB disk and 32 MB of RAM and OS 8.0.

Can someone tell me if there is a version to download to install on this old computer.

Another subsidiary question: Is it possible to download directly on the hard drive of the Mac and then install Linux right from there as I have no CD burner?

Thanks 

Thierry

---

### Post by jdp on 2006-02-24
What model is it?  And don't be overy concerned about the install specs, if you increase the RAM to at least 64MB, it should run ok.  Of course the more the better.

Use the same techniques as are described for Beige G3 installs.  Nearly any PCI PowerMac/Performa/PowerBook can use the same setup.

---

### Post by aneblanc on 2006-02-24
Hi,

Thanks for your help.

"What model is it? "

It says SuperMac S900, 604e/200 on the spec. sheet.

The OS version is not 8.0 but 8.6

The spec. sheet says for the RAM:
168 Pin DIMMs at 70 ns max. access time

Any advice about which one to buy or should I take the cheapest available?

What about the space on the hard drive? The HD has 2GB and the Ubuntu requirements call for 1.8GB of disk space. Will I still have enough space to store documents and a few programs? 
To sum it up, is it possible to change over to Linux without investing too much money in hardware on an old computer?

I am completely new to Apple and Macintosh. I even have no clue about the difference between those 2 words. Do they mean the same?

Thanks

Thierry

---

### Post by linear on 2006-02-24
SuperMac was one of the ill-fated Macintosh clones, made by Umax: [http://www.lowendmac.com/supermacs/s900.shtml]("http://www.lowendmac.com/supermacs/s900.shtml").
 
Apple is the company; Macintosh is the computer.
 
I don't think you'd be very happy with 200MB of free space after the install (unless you don't plan on installing much else, though I imagine you could strip out un-needed programs).
 
Nearly any reputable memory should be OK (but avoid Kingston ValueRam).

---

### Post by Jagged on 2006-02-24
I am a fairly new mac user with linux. I have found that many macs run Ubuntu with no problem. I would just try it and see what happens...*note make sure to hold down "c" after you power on you machine*
If it works i would just suggest getting a slightly larger harddrive. You can get smaller ones rather cheap.

Currently running Ubuntu Breezy on 10 imac g3's with only 64mb ram, 4gb harddrives, networked.
Being prepped for use as an internet cafe.

---

### Post by linear on 2006-02-24
[quote=Jagged]*note make sure to hold down "c" after you power on you machine*[/quote]
Sorry, the SuperMac is "Old World", and can't be booted normally from a Linux CD.

---

### Post by Jagged on 2006-02-24
hehe...told you I'm new to the Mac world!

---

### Post by jdp on 2006-02-24
If you do a **server** install, then go in and install the **xubuntu-desktop** instead of Gnome, it might be useable.  I've been meaning to get back into the installs I started for the 7600/132 and the 8500/120 machines I have.  I suspect that Gnome is way too much for the CPUs in anything pre-G3.  Gnome bogs down the Beige G3/300 I have, so I'm very sure that dropping back a CPU generation and losing clock speed and RAM will really kill speed.

---

### Post by aneblanc on 2006-02-24
Is that going to work as RAM:

[http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=508621&CatId=827](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=508621&CatId=827)

Premium 128MB PC133 SDRAM 133MHz Memory

Memory Size   	128MB
Memory Speed   	133MHz PC133
Memory Type   	SDRAM
Pins   	168

That's for sale for CAN $29.99 at Tigerdirect?

Thanks Linear for the link. I hope their forum can also help set me up.

"If you do a server install, then go in and install the xubuntu-desktop instead of Gnome, it might be useable. I've been meaning to get back into the installs I started for the 7600/132 and the 8500/120 machines I have. I suspect that Gnome is way too much for the CPUs in anything pre-G3. Gnome bogs down the Beige G3/300 I have, so I'm very sure that dropping back a CPU generation and losing clock speed and RAM will really kill speed."

I didn't really understand this one. What is a server install? What is xubuntu-desktop? Is it the disk I have got with the version 5.10 on it?

Great to get all that attention.

Cheers

Thierry

---

### Post by jdp on 2006-02-24
Nope, that Mac does not take the newer PC-133 SDRAM.  You need Mac compatible 5v FPM DIMM.  Take a look at [http://www.ramseeker.com](http://www.ramseeker.com) and in the top menu that says **Select Macintosh Model:** choose the item that says **168-pin DIMM** and then pres the **Go** button.  That'll give you a list of vendors that sell RAM that should work with your Mac.

RamSeeker is one of the best pricing sites for Mac RAM.

If you can, buy matched pairs of RAM.  Then you can put them in paired slots to "interleave" them and the system will run faster.  ie, if you buy two of the same 64MB DIMMs, put one in slot A1, the other in slot B1.  Then the system will automatically interleave them if possible and perform better.

---

