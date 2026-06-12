---
title: "Geforce 6150 / Nforce 430"
date: 2006-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mago on 2006-02-06
Hi. I'm new to linux (yet another once-on-the-dark-side-of-the-force-and-finally-awakening-pc-user) and after some days of intense googling and playing with a halfway installed kubuntu breezy, i got it somewhat running. I found a lot of helpful details in this forum, so I decided to join :p . Well, i'm on an Asus A8n-vm csm with an a64 3000+ venice. I'm having the same problems as many others with this chipset and linux... can't install nvidia video driver (8178 patched), nor nforce adudio and ethernet driver. After a lot of reading (and learning) i managed to boot with the vesa driver, just when i was ready to give dapper a try (which will be delayed). The thing is that without internet, getting things for linux is not an easy task. For the nvidia driver i got as far as installing gcc-3.4 (and exporting it), getting the headers and source and then hard linking them (ln -s & -sf) after install to /usr/src/linux but installer crashes even with --kernel-source-path=/usr/src/linux option with a friendly "./linux/version.h does not exist... you newbie are not configuring your kernel source files (which i don't know how to do)" message (uname -r=2.6.12-9-amd64-generic). Nforce driver (0310) is less picky, simply stating that the kernel source files are missing (though i do have them, linked and everything). Oh, by the way, there's something wrong with apci, but that is Asus fault (still no bios update). I found over the net a workaround to this, but it doesn't look easy and this isn't too much of a problem anyway (other than some error messages at boot).
I tried so many things that i'm kinda lost now. Where should i be looking? What am i doing wrong? 
Any help will be greatly appreciated.
Oh, and sorry for my english (or the lack of it)... :cry:

---

