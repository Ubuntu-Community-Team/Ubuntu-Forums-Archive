---
title: "USB drive trouble in ubuntu 7.10 64 bit"
date: 2008-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by kingleer on 2008-02-08
I am running Ubuntu 64 bit 7.10. 

EDIT: Originally, I was having trouble mounting a drive. Turns out I was just doing stuff veeery wrong in the CLI. I now know the correct way to mount stuff. 
Everything works perfectly.

I accidentally disabled my USB 2.0 support and regressed to USB 1.0 speeds. I woudl like to reverse this now...badly.

---

### Post by chrisdeckard on 2008-02-08
Does anything show up in /var/log/messages?  Look for error messages.  Have you tried the drive on another computer?

-Chris

---

### Post by kingleer on 2008-02-09
> 
Does anything show up in /var/log/messages? Look for error messages. Have you tried the drive on another computer?
 

Hello, thanks for trying to help me, but I solved my previous problem (there was no problem). 

My new problem:

I accidentally disabled usb2.0.

By typing the following in the terminal

> 

sudo modprobe -r ehci_hcd

Test if the copy/write process is stable, and if you want to disable USB 2.0 upon boot, type:

sudo sh -c 'echo blacklist ehci_hcd > /etc/modprobe.d/blacklist-ehci'
sudo update-initramfs -u -k `uname -r`


I would now like to reverse this, because USB 1 is slow as hell.

---

### Post by cdtech on 2008-02-09
> **kingleer said:**
> Hello, thanks for trying to help me, but I solved my previous problem (there was no problem). 
My new problem:
I accidentally disabled usb2.0.
By typing the following in the terminal
I would now like to reverse this, because USB 1 is slow as hell.

**sudo modprobe ehci_hcd**
[B]
lsmod | grep ehci[/B]
see if its loaded

To return back to USB2 speeds. Be sure you didn't blacklist it or you wont have it on reboot.

---

### Post by kingleer on 2008-02-09
I did black list it though. 

How do I undo the blacklist?

---

### Post by cdtech on 2008-02-09
> **kingleer said:**
> I did black list it though. 

How do I undo the blacklist?

**sudo pico /etc/modprobe.d/blacklist**

Look to see if its listed in this file if so just comment it out or remove it.

If you followed the command line from your previous post, it may be blacklisted as blacklist-ehci.
If you have a blacklist-ehci file just rename it : **sudo mv /etc/modprobe.d/blacklist-ehci /etc/modprobe.d/blacklist-ehci-old** and be sure its not listed in your **blacklist** as well.

---

### Post by kingleer on 2008-02-09
> 
blacklist-ehci.
 

I can't find this there. Is this proof positive it's not blacklisted?

---

### Post by cdtech on 2008-02-09
> **kingleer said:**
> I can't find this there. Is this proof positive it's not blacklisted?

I would try it out, see if its faster now and after reboot.

"sh -c string" is the same as putting that string in a file and running it as a script :
[B]echo 'echo hello there' > test.script
sh test.script
hello there[/B]

Be sure to update the initramfs to update the  initrd.img:
**sudo update-initramfs -u -k `uname -r`**

---

### Post by kingleer on 2008-02-09
> 
I would try it out, see if its faster now and after reboot.
 

Right now I'm formatting an external drive usb partition ext3... 

It's doing it, but kinda slowly imo... I'll get back to you but it doesn't look like it was fixed.

---

### Post by cdtech on 2008-02-09
> **kingleer said:**
> Right now I'm formatting an external drive usb partition ext3... 

It's doing it, but kinda slowly imo... I'll get back to you but it doesn't look like it was fixed.

Does it show to be loaded?
**lsmod | grep ehci**

---

### Post by kingleer on 2008-02-09
> 
lsmod | grep ehci
 

I enter the above in a terminal and get nothing at all.

---

### Post by cdtech on 2008-02-09
> **kingleer said:**
> I enter the above in a terminal and get nothing at all.

Then the module isn't loaded, did you :
**sudo modprobe ehci_hcd**
Then lsmod | grep ehci

---

### Post by kingleer on 2008-02-09
> 
Then the module isn't loaded, did you :
sudo modprobe ehci_hcd
Then lsmod | grep ehci
 

No, because that would load the module if it wasn't loaded at boot. I kinda want it to be automatic. 

here's the output of sudo pico /etc/modprobe.d/blacklist

> 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist bcm43xx


---

### Post by cdtech on 2008-02-09
First off, you removed the module and created a startup script to blacklist the module on boot ("sh -c string"). By doing the "sudo modprobe ehci_hcd" you reinstall the module, which you didn't do. You also have to update your initimg with the module loaded, since you "sudo update-initramfs -u -k `uname -r`" with the made blacklist script and removed module.

---

