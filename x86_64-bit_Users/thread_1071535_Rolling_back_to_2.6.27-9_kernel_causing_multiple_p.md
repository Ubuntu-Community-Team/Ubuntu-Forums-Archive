---
title: "Rolling back to 2.6.27-9 kernel causing multiple problems"
date: 2009-02-16
forum: x86 64-bit Users
---

### Post by GordonPMartin on 2009-02-16
Hi guys,

A couple weeks ago you helped me when my system stopped booting successfully.  We were able to determine that the new kernel update to 2.6.27-11 was causing the problem and rolled me back to 2.6.27-9.  But that has caused some other problems  :-(

I'm hoping you can give me some leads to solving these:

1) My internal card reading on my HP tx2605ca no longer works.  It doesn't even recognize that media has been inserted (I've tried various types).  It was working before the kernel update.

2) Firefox is loading pages extremely slowly.  It can take 30 seconds or so per page.  It is almost instantaneous on my other computers and used to be instantaneous on this one before the update.

What can I look at/fix?  I'm at a loss.


Thanks,

Gordon

---

### Post by Reeman on 2009-02-16
You might need to re-install the modules that run these devices. You can do it through synaptic...it sounds like the kernel was rolled back but you are not loading the right modules. It could be that the drivers for your hardware are in the restricted modules list and are still installed but not activated by grub. Post your /boot/grub/menu.lst file and let us have a look at it.
Also look at the number of kernels and their corresponding header, and modules. Make sure you have all the corresponding files.
When you get to stage1 grub press escape to see your kernel list rather than just booting directly...it could be that you are booting the wrong combination of kernel/modules!
 
Grub can return no error on boot but still not load what you need. I have had some hair pulling experiences with exactly the same problem you are experiencing. In the past I have had to save my important stuff and do a re-install...not much different than windows but one heck of a lot faster and no serial number nags!;)

---

### Post by GordonPMartin on 2009-02-20
I guess the easy part is showing you my menu.lst file.  Most of it is remmed out.  Here's the useful bit:

[INDENT]title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		6c09fd01-5f49-4259-b72a-cbbb0c28b3dd
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6c09fd01-5f49-4259-b72a-cbbb0c28b3dd ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		6c09fd01-5f49-4259-b72a-cbbb0c28b3dd
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6c09fd01-5f49-4259-b72a-cbbb0c28b3dd ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6c09fd01-5f49-4259-b72a-cbbb0c28b3dd
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6c09fd01-5f49-4259-b72a-cbbb0c28b3dd ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6c09fd01-5f49-4259-b72a-cbbb0c28b3dd
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6c09fd01-5f49-4259-b72a-cbbb0c28b3dd ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6c09fd01-5f49-4259-b72a-cbbb0c28b3dd
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
[/INDENT]

As you can see, Synaptic did well at removing the 2.6.27-11 kernel - but that's all I get from this   :-)

I'll explore the rest of the things you mentioned shortly.

I have a thought about the slow Firefox though...

At about the time that this kernel update hit me, I was also installing OpenVPN and KVPNC.  They have been working great.  The interesting thing is, when I am connected to work through the VPN, my local Firefox is much faster (despite being routed through work).  When I close the VPN, Firefox slows down again.

Something else that may be related...  Long after I disconnect from my VPN, web sites will report that I am still hitting them from my work network.  This shouldn't be happening of course.  I don't think it is related to the slow-down though because Firefox is slow even from the beginning of a fresh session.  

Is there maybe a more appropriate place for me to pursue the Firefox issue?


Thanks,

Gordon

---

### Post by GordonPMartin on 2009-02-20
More confusion for me about the card reader...

Before my initial post, I had tried different media cards and rebooted the machine a few times.

Tonight I experimented again.  I was wondering if the few updates from the past week might have made a difference.

The reader read my card!  But after unmounting it I was unable to mount it or any other cards.  Then after a reboot it seems to be fine now.  I've mounted and remounted an xD and SD card multiple times.

I guess I'll see how long this keeps working...

---

