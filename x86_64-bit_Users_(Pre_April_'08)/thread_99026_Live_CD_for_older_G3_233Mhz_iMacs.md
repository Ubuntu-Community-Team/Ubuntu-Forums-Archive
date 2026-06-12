---
title: "Live CD for older G3 233Mhz iMacs"
date: 2005-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by nerkman on 2005-12-04
I have a G3 233 Mhz iMac with 160MB of RAM onboard, and 6MB of video RAM.  I can't seem to get past the initial Ubuntu splash screen, where it's initializing the Live CD.

The startup sound comes on, but my monitor is blank - like there is no sync signal being sent to it.

At first, I thought it was screen resolution or frequency - I fiddled around with that to no avail.

It's really a shame.  I was so looking foward to this.

Can anyone help me out or suggest something?  Maybe I don't have enough system RAM?

---

### Post by Mizzou_Engineer on 2005-12-04
Sometimes I had problems with my x86 laptop and the ACPI or Plug 'N Play BIOS screwing up booting (it would black screen after the splash screen.) I put the arguments "acpi=off" or "pnpbios=off" in the boot: prompt and it would usually work.

I don't think Macs used plug 'n pray BIOS or if your iMac has any ACPI as it is not a laptop. You could try to try some of the things that look likely here: [http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html)

---

### Post by peter_m on 2005-12-04
I might not be able to help you but I do have some info that might interest you. I tried the LIVE CD as well and had the same result with iMAC 333 revD. with 160MB ram. When I installed The actual system (5.10) the problem just disapeared and everything went well... Probably a bug in the LIVE version.

In my opinion it's a bit slower then OS 9.2.2 and a litle slower then OX 10.1, but it's interesting to fidle around with. I am currently trying different window managers and Destop Environments to see if I can't speed thigs up. The alternative DE that comes with Ubuntu is Xubuntu and it's speedier then Gnome, but still want faster :-).

Before I got to this point, I was playing with Debian and I had the same problems as you have with the LIVE CD. It was just a mater of screen timings and frequency. The only resolution that is close to standard on the iMAC screen is the 1024 x 768 @ 75hz with a horizontal freq of 60khz. If you want to experiement with frequencies, keep in mind tha the CRT iMAC only accept 60khx horizontal freq.

Hope it helps,

Peter_M

---

