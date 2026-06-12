---
title: "Shuttle SN85G4 V3 Issues"
date: 2006-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by nmatheis on 2006-01-16
Hello
I got the itch to upgrade my computer, seeing as it was several years old.  I ran across a book at the library on putting computers together.  In it, they showed how to assemble an SSF - a Shuttle SN85G4 with AMD x64 processor.   So, I ordered some parts and assembled the machine.  My parts were:

*Shuttle SN85G4 V3 (case, motherboard, onboard ethernet, onboard audio, onboard cardreader, onboard usb, onboard firewire)
*Maxtor 80GB IDE HD (from my old beast)
*NEC dual-layer DVD Burner
*1GB OCZ Premiere PC3200 DDR RAM
*AMD Athlon 3000+ 64-bit processor
*CompUSA Radeon 9250 AGP Video Card
*go2.0 USB 2.0 PCI card
*19" Proview LCD monitor
*wireless keyboard / mouse combo
*Actiontek DSL modem from Quest -> Linksys router

I wanted to have a dual boot machine, so I installed WinXP Pro 64-bit edition with SP1 + Kubuntu 5.10.  Problems I'm having:
*WinXP recognizes that I have a network connection but I can't get anywhere with it.  Set it for DHCP, which the router is outputting to no avail.
*Tried throwing in the Shuttle Mainboard CD an looking for ethernet drivers with no luck - didn't find anything.
*Loaded up Kubuntu - tried running update via Adept, but it stopped working with 64 packages left and hasn't started running again (I have enabled all repositories in the Repository Manager).  I can start the program, but it won't fetch updates anymore - just stalls out).
*I can surf the web wth Kubuntu (but not with WinXP).
*I've got a laptop running WinXP hooked up to the same router on the web with no problems.  Possibly faster than the Kubuntu boc I'm on now, even though the laptop is a few years old already.
*Can get to yahoo, but can't use the reply button - nothing happens.
*Couldn't get anything to work at first, so I had to use the Maxtor Cd that came with my HD to write all zeros to the HD.  Then I was able to install WinXP w/out errors.
*Web with the Kubuntu install runs slowly at times and stalls out sometimes.
* I have had several crashes with Adept, and my recent logins start out with having to enter my su-password as Adept starts up first thing in the login after I had already closed it in the previous login.

Anyhow, I really want to be able to use the SSF I just put together with reliability but am frustrated with the inability to get WinXP to work online at all and with Kubuntu for not being reliable with the web / updates via Adept.  Any help provided will be GREATLY appreciated!!!

Thanks!
Nikolaus

---

### Post by bernardfrancois on 2006-01-20
Best thing to do is to try to find out if your hardware will work well with linux (meaning: if the manufacturer did an effort supporting linux or at least to make it compatible).
Since the problems are bigger in windows, this might not be the issue.

Maybe you could try installing 32 bit versions (of windows and ubuntu). I know, you won't get the same performance, but you will have less problems.

I am using ubuntu 5.10 (gnome), also the 64bit version, but on an AMD Sempron 2600+.
I didn't try yahoo, I am using gaim instead (it also supports yahoo), and it's working fine.

Maybe you could install synaptic (apt-get install synaptic) I guess... Or maybe you can first try *apt-get dist-upgrade*, which sometimes solves problems with repositories...

---

