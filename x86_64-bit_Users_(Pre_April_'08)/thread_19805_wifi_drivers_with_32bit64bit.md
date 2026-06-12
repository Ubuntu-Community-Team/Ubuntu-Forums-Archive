---
title: "wifi drivers with 32bit/64bit"
date: 2005-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by BaffledMollusc on 2005-03-13
I'm about to install Ubuntu on my AMD64 machine, but I'm worried about getting the wireless adapter to work (a Netcomm NP542; don't ask me what the chipset is because I don't know and haven't been able to find out yet).

I'm wondering whether to install a 64-bit version of Ubuntu or stick with a 32 bit version. Is it the case that all drivers included in the 32-bit version are present in the 64-bit version, or are some missing? What I'm asking is, is there a lower chance that wireless will work out of the box using 64-bit?

---

### Post by wmcbrine on 2005-03-13
All open-source drivers should work. Closed-source, third-party drivers may not be available for 64-bit. I can't speak to your card.

I would just get the Live CD and try it out. In fact, that's what I did, and I grabbed the Installation CD later that day. :) All my hardware was autodetected.

---

### Post by BaffledMollusc on 2005-03-13
Yeah, I guess "try it and see" is probably the best option. Which I was going to do anyway; I was just hoping that someone would say, "Hey, I've got that card and it works fine under 64-bit - install away!"  :lol: 

I'll post back here in a couple of days if I can get it work.

---

### Post by BaffledMollusc on 2005-03-15
[QUOTE=BaffledMollusc]Yeah, I guess "try it and see" is probably the best option. Which I was going to do anyway; I was just hoping that someone would say, "Hey, I've got that card and it works fine under 64-bit - install away!"  :lol: 

I'll post back here in a couple of days if I can get it work.[/QUOTE]

Well, I'm reporting back, even though it's not specifically 64-bit related, in case someone happens to search the forum for the same wireless adapter model I have. I installed the 32-bit version of Hoary, and wireless was detected during install and the network settings were automatically configured. When I booted into Ubuntu I could open Firefox and go surfing immediately. Absolutely jaw-dropping.

Anyway, I presume that means that there is an open-source driver in the kernel, and so presumably this wireless adapter will work on 64-bit too, although I haven't tried it yet.

---

### Post by dickohead on 2005-06-29
[QUOTE=BaffledMollusc]Well, I'm reporting back, even though it's not specifically 64-bit related, in case someone happens to search the forum for the same wireless adapter model I have. I installed the 32-bit version of Hoary, and wireless was detected during install and the network settings were automatically configured. When I booted into Ubuntu I could open Firefox and go surfing immediately. Absolutely jaw-dropping.

Anyway, I presume that means that there is an open-source driver in the kernel, and so presumably this wireless adapter will work on 64-bit too, although I haven't tried it yet.[/QUOTE]
 i'm using Ubuntu on a 64bit laptop, and have a NetComm NP543 but it won't work.... what do i need to do in order to get it working...? It never lights up, and the same could be said about SuSE 9.2 (32 and 64bit) as it never picked up my card...

---

### Post by toastedd on 2005-08-04
[QUOTE=dickohead]i'm using Ubuntu on a 64bit laptop, and have a NetComm NP543 but it won't work.... what do i need to do in order to get it working...? It never lights up, and the same could be said about SuSE 9.2 (32 and 64bit) as it never picked up my card...[/QUOTE]

Same here!

I also have a NetComm NP54**3** (not NP542) and it is not auto detected and I can't find out what chipset it is and thus have no idea what driver to use.

Can anyone help us for the Netcomm NP543??

Thanks

EDIT: IT USES AN ACX111

---

