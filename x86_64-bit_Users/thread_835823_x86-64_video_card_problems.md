---
title: "x86-64 video card problems"
date: 2008-06-20
forum: x86 64-bit Users
---

### Post by pcflyer44 on 2008-06-20
:confused:Hello I am having trouble with getting my AGP video cards to work the PCI card works fine and came up instantly and the 3D stuff came on for me to, I did try Nvidia and ATI in the AGP slot.


system:
Nforce3: motherboard from Biostar
want to use ATI X1300 AGP 256MB
started with Nvidia fx5600xt AGP 128MB
now using Nvidia fx5500 PCI 256MB

---

### Post by nikgare on 2008-06-21
What problems are you having with the AGP card?
Is it refusing to work at all, or is it another problem?

---

### Post by soxs on 2008-06-21
did you install any drivers in order to make the pci one (pci or pci express?) work?

open a terminal and post the output from (while PCI(E) is plugged):
```
glxinfo|grep render
```
```
fglrxinfo
```

if you did not install any drivers you should dl ati catalyst 8.6 and give it a shot or (the ubuntu prefered method) install the driver via System -> System... -> Hardware drivers

---

### Post by pcflyer44 on 2008-06-21
the AGP card is working in the windows os .
I did manage to get the Nvidia fx5600xt to work it turned out to be a port problem but the ATI will work in low res mode and the message I get is that the selected video card was not recognized and the drivers that come from ATI say I must be a super user, do I need to set up a virtual window to run it

---

### Post by soxs on 2008-06-22
> **pcflyer44 said:**
> the AGP card is working in the windows os .
I did manage to get the Nvidia fx5600xt to work it turned out to be a port problem but the ATI will work in low res mode and the message I get is that the selected video card was not recognized and the drivers that come from ATI say I must be a super user, do I need to set up a virtual window to run it

To obtain super user rights, you need to put sudo infront of the at installer.
```
cd /where/the/installer/is
```
So in termnal it shoul look like (or at least very similar):
```
sudo ./ati-driver-installer-8-6-x86.x86_64.run
```

---

### Post by pcflyer44 on 2008-06-23
I had the ATI card working somewhat before I read your post and now  the 3d stuff came on thank you very much. I work in a retail store selling computers and other home entertainment things and I have been telling everyone who will listen about the Ubuntu Linux system  it really is the best one out there and I have been waiting for a good one to come out and I'm even putting on a PPC for fun to see if it will work ( wish it came in the 8.04 ):)

---

