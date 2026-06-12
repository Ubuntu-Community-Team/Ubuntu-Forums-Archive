---
title: "[SOLVED] Dead USB after strartup!"
date: 2007-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by NickArgyle on 2007-12-09
I recently installed Gutsy and am having only two problems: 1. random freezes (which I will work on later) and 2. My usb ports.
If my devices are plugged in before booting the kernel the devices work fine, be it usb mous/keyboard, flash drive, hardrive, whatever they all work fine. That is, until I unplug them. If i plug them back in, or plug anything else in, nothing happens. The lights on the devices don't even come on.

Anyone have any ideas?

I am running 2.6.22-14-generic
Gutsy 64bit on amd turion 64 x2
Nvidia GeForce go 6150
Broadcom wireless (ndiswrapper)

---

### Post by NickArgyle on 2007-12-09
:popcorn: bump

---

### Post by John Jason Jordan on 2007-12-09
> **NickArgyle said:**
> :popcorn: bump
What kind of computer is it?

---

### Post by NickArgyle on 2007-12-09
hp dv9000, worked fine in feisty though, although that was 32 bit.

---

### Post by dampbuffalo on 2007-12-09
yup i have a dv6000 amd and it also has the same problem 

the memery card reader works fine but my usb hubs dont work 

only when i boot up with the usb device pluged in, then it works

---

### Post by John Jason Jordan on 2007-12-10
> **NickArgyle said:**
> hp dv9000, worked fine in feisty though, although that was 32 bit.
The reason I asked is because I have a new Thinkpad T61 that has the same problem. That is, there are two USB ports at the back of the right side that die exactly as yours do. They work fine if something is in one of them when I boot, but removing the device later kills both ports. Strangely, there is a third port in the middle of the left side that works perfectly. 

It has been reported as a bug somewhere, but I didn't save the link. Google should turn it up though. Might be interesting to see if these computers have something in common that might be causing the problem.

---

### Post by NickArgyle on 2007-12-10
> **John Jason Jordan said:**
> The reason I asked is because I have a new Thinkpad T61 that has the same problem. That is, there are two USB ports at the back of the right side that die exactly as yours do. They work fine if something is in one of them when I boot, but removing the device later kills both ports. Strangely, there is a third port in the middle of the left side that works perfectly. 

It has been reported as a bug somewhere, but I didn't save the link. Google should turn it up though. Might be interesting to see if these computers have something in common that might be causing the problem.
Yeah, that's interesting. It doesn't bother me too much until I need to transfer a file to my jump drive. Have either of you, or anyone else, had experience with this problem on 32bit gutsy? I am assuming it is a strictly 64bit problem.

---

### Post by dampbuffalo on 2007-12-11
no i do have a 64 bit amd but io installed ubuntu 7.10 32bit on my laptop 
and i need it exacly to transfer files to thumb drives
so yeah 

heeeeelllppppp mmmmmmmmmmeeeeeeeee!!!!!!!!!!!
thank you

---

### Post by John Jason Jordan on 2007-12-11
> **dampbuffalo said:**
> no i do have a 64 bit amd but io installed ubuntu 7.10 32bit on my laptop 
and i need it exacly to transfer files to thumb drives
so yeah 
1) Does your laptop have more than one USB port? If so, try different ones. 
2) Try inserting the USB drive in the port before booting the laptop. 

It should work without requiring (1) or (2) above, but if either of the above get it working at least you have a temporary workaround. It also might make it easier to figure out what is wrong. If neither of the above help, then post back with the make and model of the computer. Add also the results of the following from a command line (open a terminal window and copy and paste these commands into it):

1) uname -a
2) dmesg | tail - run this right after inserting the drive, and again after removing the drive.
3) mount - also run before and after inserting, and again after removing
4) lsusb - ditto
5) lspci - on this command search through for any lines that might have something to do with USB - don't bother posting all the rest.

If any of the above commands say "permission denied" insert "sudo" in front of the command and then give it your root password when prompted.

After you post back the results from the above someone here might be able to tell what is going on and be able to tell you how to fix it.

---

### Post by jcaveman on 2007-12-12
If your booting with the noapic option, you might want to add irqfixup to the boot options.  Without this option, my DV6119us would disable the usb ports shortly after bootup if nothing was plugged into the port.  A message would appear about IRQ 7 and nobody cared.  Adding irqfixup to the boot options kept the usb ports from being disabled.

---

### Post by NickArgyle on 2007-12-12
> **jcaveman said:**
> If your booting with the noapic option, you might want to add irqfixup to the boot options.  Without this option, my DV6119us would disable the usb ports shortly after bootup if nothing was plugged into the port.  A message would appear about IRQ 7 and nobody cared.  Adding irqfixup to the boot options kept the usb ports from being disabled.

Oooh, thanks for the suggestion, I am booting with noapic so I will have to try this out.

---

### Post by NickArgyle on 2007-12-12
> **NickArgyle said:**
> Oooh, thanks for the suggestion, I am booting with noapic so I will have to try this out.

Yes! it worked. Muchos gracias.

---

### Post by dampbuffalo on 2007-12-14
thank you so much the irqfixup works like a charm and its going to help me soo much 
thanks all for helping

---

### Post by NickArgyle on 2007-12-15
> **dampbuffalo said:**
> thank you so much the irqfixup works like a charm and its going to help me soo much 
thanks all for helping

I think it stopped my random freezes too! :guitar:

---

