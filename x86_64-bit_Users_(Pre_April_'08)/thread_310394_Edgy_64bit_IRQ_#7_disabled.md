---
title: "Edgy 64bit IRQ #7 disabled"
date: 2006-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by hainesr on 2006-12-01
Hi all,

Can't seem to find any other posts about this so here goes:

Each time I boot into Edgy 64bit I get a message telling me that IRQ #7 has been disabled. This message appears a random amount of time after booting (ie, sometimes within the first minute, sometimes 10 minutes into use). The message is always accompanied by a beep (which is how I spotted that it was being printed on tty1). One time the message even said something like, "Disabling IRQ #7 as nobody cared".

This seems to have no effect to the operation of my machine, but it still bothers me for some reason. Is it a problem, or should I just ignore it?

My specs:
AMD Athlon X2 Socket AM2
Asus M2N32-SLI Deluxe Motherboard
2Gb RAM
SATA hard disks
IDE DVD
NVidia 7900 PCI-e graphics

Thanks for any help/info!

Cheers,
Rob

---

### Post by Didjit on 2006-12-01
Do you still have sound after you see this message? I ran into this issue too a while back, but I thought it was caused by Alsa/Sound Card. I havn't seen it since I fixed my sound.

Didjit

---

### Post by hainesr on 2006-12-01
Yes I still have sound. It's an on-board sound card that I've never come across before (can't remember the name of the top of my head and I'm at work at the moment) but it seems to work fine.

Like I say, there doesn't seem to be anything wrong, but it just feels wrong!

Thanks,
Rob

---

### Post by jcaveman on 2006-12-01
I have a similar problem on my HP Pavilion 6119.  It seems to disable the USB port, as I can't load a flash drive after the machine tells me its disabled IRQ 7 and dmesg reports an error with ehci.  I tried booting with the irqpoll kernel parameter, but it locks up during boot.

---

### Post by hainesr on 2006-12-01
Ah ha, you've tweaked my memory! I couldn't get a flash drive to be seen in the front usb port of my machine the other day. I didn't try any of the rear ports at the time but now I think about it I did have a problem with a usb keyboard (plugged into one of the rear ports): it stopped working after I left the machine alone for a while. I've had to go back to my crappy old PS2 keyboard as a workaround.

Maybe the IRQ gets disabled if nothing happens through the usb ports for a while? It was always after the screensaver kicked in that my keyboard was dead...

If this is the problem, does anyone know the solution? I've not tried irqpoll myself yet - I'll try it over the weekend.

Cheers,
Rob

---

### Post by hainesr on 2006-12-03
So I booted in to Edgy today and immediatly inserted my usb flash drive and it worked perfectly. Then I removed it and sure enough, five minutes or so later, I got the IRQ #7 disabled message in my terminal. dmesg said this:

```
[  416.982164] irq 7: nobody cared (try booting with the "irqpoll" option)
[  416.982169] 
[  416.982170] Call Trace: <IRQ> <ffffffff802b68a5>{__report_bad_irq+53}
[  416.982192]        <ffffffff802b6b20>{note_interrupt+544} <ffffffff880c8bb8>{:usbcore:usb_hcd_irq+40}
[  416.982222]        <ffffffff802b6190>{__do_IRQ+224} <ffffffff802737e2>{do_IRQ+66}
[  416.982231]        <ffffffff80271f00>{default_idle+0} <ffffffff80265d08>{ret_from_intr+0} <EOI>
[  416.982240]        <ffffffff80232690>{unix_poll+0} <ffffffff80232690>{unix_poll+0}
[  416.982251]        <ffffffff80271f29>{default_idle+41} <ffffffff8024ecfe>{cpu_idle+158}
[  416.982260]        <ffffffff8027d34d>{start_secondary+1165}
[  416.982277] handlers:
[  416.982279] [<ffffffff880c8b90>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  416.982293] Disabling IRQ #7
```

So I tried by usb flash drive again with no luck. dmesg now said this:

```
[  765.011476] usb 1-8: new full speed USB device using ohci_hcd and address 5
```

Something obviously spotted the flash drive being inserted, but I couldn't mount it and the light on it stayed off.

So I rebooted with the intention of adding the "irqpoll" option to the boot line but spotted that I had a "noapic" option in there already. I'd had to add the "noapic" option to get Edgy to boot until I updated the BIOS on my motherboard, then obviously forgot to take it out once I had. I removed the "noapic" option and decided to boot without "irqpoll" and it has been working fine since! 

Fingers crossed that's fixed it for me now. If you're seeing this IRQ #7 Disabled message and you're using the "noapic" boot option when you don't need to, try removing it!

I'm going to try my USB keyboard and mouse again now...

Cheers,
Rob

---

### Post by Didjit on 2006-12-03
I was able to reporduce this error on my box. On my box it screws up sound. Way I work around it is disable my second SATA controler in the BIOS. 

IRQ's seem to be messed up. Curious to see what you find out...

Didijt.

---

### Post by Alabaster on 2006-12-03
Hi, I have an identical system to you and was getting the same error message intermittently, as well as a HAL fail error after GNOME login. 

In addition, I was unrecoverably losing my USB keyboard and mouse after a suspend which was really bl**dy irritating! I updated the BIOS, disabled legacy support for USB ports and, like you say, removed the noapic option from the boot line, which I had to include to get Edgy to boot first time. 

Presto! All fixed! :-D

Should add tho, I using 32 bit Edgy on an AMD64-bit chip...don´t ask me why

---

### Post by hainesr on 2006-12-04
So I have run my machine with a USB keyboard and mouse after removing "noapic" and had no problems at all so far!

> **Alabaster said:**
> I have an identical system to you and was getting the same error message intermittently, as well as a HAL fail error after GNOME login.

I have to say I'm glad I've not seen any HAL errors on my machine!

> **Alabaster said:**
> In addition, I was unrecoverably losing my USB keyboard and mouse after a suspend which was really bl**dy irritating! I updated the BIOS, disabled legacy support for USB ports and, like you say, removed the noapic option from the boot line, which I had to include to get Edgy to boot first time.

I've not disabled legacy support for USB on mine and things appear to be fine still. If you do that do you lose keyboard operation for things like the BIOS menus and so on? I never understood what legacy USB support did, but thought it was something to do with low level mouse and keyboard operations...

I think where we are concerned we have a relatively new motherboard and there were some teething problems under linux that, fair play to Asus, they fixed pretty quickly.

I guess the best advice to others with this problem is to check your BIOS. If it's not the latest version, upgrade and all might be fixed!

> **Alabaster said:**
> Should add tho, I using 32 bit Edgy on an AMD64-bit chip...don´t ask me why

Makes doing quite a lot of stuff easier (flash, video codecs, etc). I considered 32bit as well, but now I know there are similar problems I'm going to keep the faith with 64bit...

Cheers,
Rob

---

### Post by s1ptome on 2006-12-06
@ jcaveman: I had the same problem on my HP Pavilion dv9001. I fortunately solved it recently by booting with  "irqpoll noirqdebug" instead of "irqpoll" alone.

hope this might help you,
s1ptome

---

### Post by jcaveman on 2006-12-07
s1ptome,

Thanks, the noirqdebug option seemed to resolve the problem with the notebook locking up when I used irqpoll.  It boots fine now and the USB port seems to recognize and mount flash drives now when I plut them in.

jcaveman

---

### Post by ckoester on 2007-02-15
I'm getting the same error on my HP Pavillion dv6000, AMD64 Edgy install.  I think I've tried every combination in this thread.  Here's the dmesg output:

[  241.659431] irq 7: nobody cared (try booting with the "irqpoll" option)
[  241.659437] 
[  241.659438] Call Trace: <ffffffff802b6875>{__report_bad_irq+53}
[  241.659463]        <ffffffff802b6af0>{note_interrupt+544} <ffffffff880c8bb8>{:usbcore:usb_hcd_irq+40}
[  241.659502]        <ffffffff802b6160>{__do_IRQ+224} <ffffffff802737a2>{do_IRQ+66}
[  241.659515]        <ffffffff80271ec0>{default_idle+0} <ffffffff80265cd0>{ret_from_intr+0}
[  241.659531] handlers:
[  241.659534] [<ffffffff880c8b90>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  241.659555] Disabling IRQ #7

And if I try inserting a flash drive later I get the following messages:

[ 2982.658340] usb 1-2: new high speed USB device using ehci_hcd and address 7
[ 2988.436012] usb 1-2: device not accepting address 7, error -110
[ 2988.496019] usb 1-2: new high speed USB device using ehci_hcd and address 8
[ 2994.273756] usb 1-2: device not accepting address 8, error -110
[ 2994.331753] usb 1-2: new high speed USB device using ehci_hcd and address 9
[ 2999.543481] usb 1-2: device not accepting address 9, error -110
[ 2999.599481] usb 1-2: new high speed USB device using ehci_hcd and address 10
[ 3004.813826] usb 1-2: device not accepting address 10, error -110

---

### Post by Lifeboat on 2007-02-20
I have 4 new boxes running on Edgy. About a week ago, after running with almost no problems at all for a few weeks, I found that 1) My usb ports all were going dead to every kind of device I could test with, within some few hours of being re-booted. (which solved the problem immediately, but only for a few hours).

Three of these rigs run without a monitor or keyboard/mouse, doing computationally intensive protein folding for Folding @ Home. 

Anyway, some time after the usb ports went dead, the protein simulation program running in just a terminal window, would also stop working.

It appears the problem was I had loaded the "Optimized Defaults" in the Phoenix BIOS. As soon as I changed that back to the non-optimized BIOS selection, they were good to go,

It seems the "Optimized Default" setting in the BIOS, checks the usb ports, etc, and when there is nothing in them for a while, shuts them off. :(

It's been 2 1/2 days (running 24/7), and everything is working correctly, and no usb ports have been found dead, yet. :)

---

### Post by upro on 2007-02-23
It's a permission problem. 

With all the same messages form /var/log/syslog and dmesg I figured out that I could mount a camera and import images by doing

sudo gnome-volume-manager-gthumb

It wouldn't work as user.

So, just check persmissions...

Hope that helps,

upro

---

### Post by s1ptome on 2007-03-15
i've found another option that might help one of you, or may also be of some interest for others whose problem has already been solved...

i was booting, as i said earlier, with both options "irqpoll noirqdebug"
i have replaced that couple by "irqfixup" only. It seems to be as successful, maybe it's worth a try? (i hope this might solve another problem on my computer, i have seen some variations in my dmesg)

s1ptome

---

