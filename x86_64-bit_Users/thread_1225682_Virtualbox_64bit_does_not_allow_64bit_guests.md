---
title: "Virtualbox 64bit??? does not allow 64bit guests"
date: 2009-07-28
forum: x86 64-bit Users
---

### Post by dlmarti on 2009-07-28
So here's the deal I have a 64bit Xeon, running 64bit Jaunty.

I install virtualbox (I've tried downloading the amd64 deb file directly AND putting virtual box into the software sources and doing apt-get).

When I go to run 64bit guests, the guests (both windows and Ubuntu) say that the environment is not 64bit.

I've done all the virtualbox 64bit hacks (the ACPI stuff), still no go.

How can I be absolutely sure that the package I have is truely a 64bit package (even though it says amd64)????

---

### Post by John Jason Jordan on 2009-07-28
> **dlmarti said:**
> So here's the deal I have a 64bit Xeon, running 64bit Jaunty.

I install virtualbox (I've tried downloading the amd64 deb file directly AND putting virtual box into the software sources and doing apt-get).

When I go to run 64bit guests, the guests (both windows and Ubuntu) say that the environment is not 64bit.

I've done all the virtualbox 64bit hacks (the ACPI stuff), still no go.

How can I be absolutely sure that the package I have is truely a 64bit package (even though it says amd64)????

First, to use a 64-bit guest OS in VB you need VB 2.0 or later. I think that appeared for the first time in the repositories for Intrepid. 

Second, why did you download the .deb file when you can just enable the appropriate repo and then install with Synaptic? That's the way I did it and I have no trouble installing 64-bit guest OSs. Unless you're using an Ubuntu earlier than Intrepid, I would uninstall what you have and then install it using Synaptic. Synaptic is my buddy. She always figures out all the dependencies and stuff so I don't have to trouble my little head about them.

I don't know if any of that helps, but at least I can assure you that it can be done.

---

### Post by dlmarti on 2009-07-29
Its version 3.0.2.

I did try letting apt get the package for me, AND downloading it myself (with a uninstall between).  Same result.

How do I determine if a package is truely 64bit????

---

### Post by rannable on 2009-07-29
i think people download it from the website to get a newer version, plus older versions of ubuntu had a buggy version of vbox OSE, i think the default download from the website is the non-OSE...

---

### Post by kelvin spratt on 2009-07-29
All need to do is go to Vbox site add the correct repro to your apt repro list then use synaptic to install the version you want. 
when you use vbox select 64bit thats it simple.
You can only use 64bit with a 64bit opperating system check you are using 64bit distro.

---

### Post by mgranet on 2009-07-29
Also, you have to have a CPU with virtualization support.

---

### Post by dlmarti on 2009-07-29
Guys, I did all the above, what I'm asking is how do I determine that the package that is installed IS the 64bit version?

---

### Post by jespdj on 2009-07-29
Even the 32-bit version of VirtualBox can run 64-bit guest operating systems. But you do need to have a processor with hardware virtualization support and you need to make sure it's switched on in the virtual machine you've created.

How did you create your virtual machine? One of the first steps the wizard asks is what type of guest OS you want. Select "Ubuntu (64-bit)" (or whatever, as long as you choose 64-bit) there.

---

### Post by dlmarti on 2009-07-29
> **jespdj said:**
> Even the 32-bit version of VirtualBox can run 64-bit guest operating systems. But you do need to have a processor with hardware virtualization support and you need to make sure it's switched on in the virtual machine you've created.

How did you create your virtual machine? One of the first steps the wizard asks is what type of guest OS you want. Select "Ubuntu (64-bit)" (or whatever, as long as you choose 64-bit) there.

I'm not given the option of Ubuntu 64bit.
I assume hardware virtualization works because I have several 32bit guests.

---

### Post by mgranet on 2009-07-30
Your 32 bit guests are running software virtualized. The error you described in your first post nailed it: It's not a 64bit environment. That means you don't have a CPU with hardware virtualization. I get the same error when I accidentally download a x64 .iso out of habit.

---

### Post by dlmarti on 2009-07-30
> **mgranet said:**
> Your 32 bit guests are running software virtualized. The error you described in your first post nailed it: It's not a 64bit environment. That means you don't have a CPU with hardware virtualization. I get the same error when I accidentally download a x64 .iso out of habit.

So your saying its possible to have a 64bit Xeon, but not have the hardware virtualization for a 64bit environment?

---

### Post by mgranet on 2009-07-30
Yep. I have a 939 Athlon 64 X2, but because it's an E stepping revision, it does not support the virtualization extensions that the later F revision AM2 chips do. Intel is the same way; virtualization was released after 64 bit was already in market.

---

### Post by dlmarti on 2009-07-30
> **mgranet said:**
> Yep. I have a 939 Athlon 64 X2, but because it's an E stepping revision, it does not support the virtualization extensions that the later F revision AM2 chips do. Intel is the same way; virtualization was released after 64 bit was already in market.

Son of a biatch  :)

Thanks for the help.

---

### Post by dlmarti on 2009-07-30
but wait a minute.
If I CAN run virtual box 32bit guests, why can't I have 64bit guests when 32bit processors can????

---

### Post by mgranet on 2009-07-30
They found a hack for the 32bit. 

Yeah, I know. It sucks.

---

### Post by xebian on 2009-07-30
Not sure from your post if you already did but in the settings->system->acceleration, you should enable Hardware Virtualization: VT-x/AMD-V.  Of course this is possible only if your Mobo is VT enabled in your BIOS.

---

### Post by dlmarti on 2009-07-30
> **xebian said:**
> Not sure from your post if you already did but in the settings->system->acceleration, you should enable Hardware Virtualization: VT-x/AMD-V.  Of course this is possible only if your Mobo is VT enabled in your BIOS.

I see the setting, but its ghosted, and doesn't allow me to select.

---

### Post by xebian on 2009-07-30
> **dlmarti said:**
> I see the setting, but its ghosted, and doesn't allow me to select.

Which means either your cpu does not support it, or your Mobo doesn't or your BIOS does not or not enabled.

I suspect it's not enabled in your BIOS/MObo setup because you do have a newer cpu.

---

