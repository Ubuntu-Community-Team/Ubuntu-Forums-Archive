---
title: "LiveCD boot hangs at random moments during boot"
date: 2007-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by RIProof on 2007-04-13
I am having a problem booting off of a LiveCD I made for Ubuntu. I have tried both 6.06 and 6.10 versions on the AMD 64 chipset. I have an AMD Turion 64X2, and it normally runs Windows Vista, and I am interested in creating a dual-boot setup, but I want to try Ubuntu first. My machine is an HP dv6253: [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00846935&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00846935&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

When I boot off of the 6.06 image, the booting will hang at various stages:

Sometimes when initializing something containing the words "Enterprise Value Server .... [OK]" (I'm at work right now and the exact phrase escapes me) and sometimes when initializing the Network Interface.

When I boot off of the 6.10 image, I see the strange-looking gray and green progress bars dancing around, and they seemingly complete, and then I get stuck at a black screen.

My searches on the web have revealed similar problems, but the solutions to those problems have not worked in my case. I have tried turing APIC off in the boot parameters and it had no effect.

Are there some other boot parameters I should use? Should I just buy one of those Linux start-up magazines that come with a Linux CD? Should I try a 32-bit version? Reading around here about 32 vs 64 gives mixed results -- some people have no problem and some have many. Any hints you can give would be great. 

I am relatively new to Linux but not to UNIX (school's CS dept uses NetBSD so I've had to learn for the sake of my GPA). I'd like to have a dual-boot machine so I can learn more about Linux-based OSes.

---

### Post by RIProof on 2007-04-14
Well thanks for all of your helpful replies! /sarcasm

I downloaded the 32-bit image and out of three tries, I could load the LiveCD once. Gee I don't know, but 33% reliability seems a little low for an OS to be installed on one of my machines. Peace out Ubuntu.

---

### Post by Jouke74 on 2007-04-16
Maybe you should wait a couple of days and start with Feisty, and then take the alternate CD with text based installer? Also search in google for people running linux on your laptop and send them a mail or PM if possible. I used that and it got me a few decent replies. Of course, no one is stopping you to switch for another distro.

---

### Post by bugler on 2007-04-16
ripproof:

I have a dv6450 working nearly flawlessly.  For some reason the live cd and installed need a combination of noapic for the boot parameter.  Some things for editing the boot parameters is hit F6 when ubuntu menu pops up.  Add -noapic to the end of the boot line.  That fixed it for me.  I have also had luck with pci=noacpi, -noapic, and something else I couldn't remember.  All of this was really confusing for me at first.  You might have to use 1 or all of the combinations.  I would start with the noapic command first then try the other ones, then try some combinations.

If it works remember which one or combinations.  You will have to edit the /etc/grub/menu.lst file and add it there for permanent solution.

Let us know how it turns out.

Bugler

---

