---
title: "Powermac 7500 install success/freeze"
date: 2006-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Yimmy on 2006-04-27
It's so close. I've been working with my G4 upgraded Powermac 7500 oldworld machine for some time.  I finally got past being unable to mount the Mac partition to copy over the vmlinux kernel and the initrd.gz file, during the first half of the install.  Hooray! I had to use the instructions in one of the comments here:
[http://www.applefritter.com/node/8936](http://www.applefritter.com/node/8936)

*EDIT:* It was pretty much as follows, and the tabbing was the key to getting the correct file.
```

mkdir /target/mnt/hfs
mount /dev/(your partition) /target/mnt/hfs -t hfsplus
cp /target/boot/vmlinuz /target/mnt/hfs/System\ Folder/Linux\ Kernels/vmlinuz-Ubuntu-5.10-orig
cp /target/boot/initrd.gz /target/mnt/System\ Folder/initrd-Ubuntu-5.10-orig.gz

```

After I did there was some weird problem with it not finding my linux root even though I knew it was correct.  Doh! (Mine was something odd like hdg8.  Not sure why the letter went all the way to g).  At first it told me that it root= wasn't correct basically.  I changed it to hda8 just to see what it would do.  It dropped into a BusyBox shell that time, and I managed to get it to find the linux root partition after following part of these intructions.

> 
1) From the busybox shell, check if the device you can't access shows up in /dev. If it doesn't, this tutorial is what you're looking for. Figgure out what modules you need to load. Alternate between modprobing and starting udev again until the devices show up.

For OldWorld Macs, try these modules: mesh, mace, sd_mod, mac53c94.

# modprobe mesh
# modprobe sd_mod
# udevstart
# ls /dev

2) mount the root partition and chroot to it

mkdir /mount
mount -t ext3 /dev/YourRootPartition /mount
mount -o bind /dev /mount/dev
chroot /mount /bin/bash
cd


Found it here: [http://www.stuporglue.org/initrd.php](http://www.stuporglue.org/initrd.php)

After that I was able to tell BootX what root= and it found it and went into the second part of the install.  Here's where the new problem started.

At about 57% it just sat there forever.  I could hear it working, so I stayed with it, then finally it vomited a bunch of code on the screen about Bluetooth this and that, and it didn't do anything else after that.  I had to shut down.  I haven't tried to reboot it yet as this was late last night (or early this morning I should say).  Any thoughts on this?  Anybody else experienced something similar?

---

### Post by Yimmy on 2006-04-29
Apparently it's  crapping  out at the 'Preparing to configure gstreamer0.8-tools'.  It's done it everytime now.  Anybody else experienced this?

---

### Post by Yimmy on 2006-05-01
Success!  Installed and updated!  At some point in the next couple days I'll post the complete experience.  The only thing I need to do is figure out how to enable the L2 cache on my G4 upgrade card and do some testing.  Then I'll have to try to get my network up and running and get my pc only Lexmark printer working.

---

### Post by Yimmy on 2006-05-02
It really feels like it's rolling now.  My L2 cache on my G4 upgrade card is working and Ubuntu is smoking fast compared to what it was.  Had to pass in the right key in BootX.  My arguments look something like this.
```
root=/dev/hgd8 l2cr=0x9080000
```

Note for anyone trying to do this, that is NOT my exact code and NOT yours either.  You've got to use an L2 cache config program available online to get that value.  This link [http://www.cpu.lu/~mlan/linux/dev/g3upgrade.html#l2cr](http://www.cpu.lu/~mlan/linux/dev/g3upgrade.html#l2cr) explains alot.

Anyway, now I've just got to install the printer drivers (hmmm sounds not fun) and get the network up and running.  Since this machine will be the file server I'm going to set up the network through Ubuntu.  Not sure how that will work out, since I don't know how that works or how to do it.  I'll search around here, but if anybody has suggestions or can point me in the right direction, it would be greatly appreciated.

---

### Post by roazena on 2006-05-04
You're my hero. I have a G4 upgraded 7500 too, with maxed out memory, 37Gb internal drive and PCI USB card. Are all your keyboard/mouse things still ADB or does Ubuntu recognize aftermarket USB?

---

### Post by Yimmy on 2006-05-04
Right now I'm still using ADB for mouse and keyboard.  Eventually I'll hook up my optical USB Logitech mouse.  So far my experience with my PCI USB firewire card was I hooked up my USB printer and everything froze.  :(  But, the good news is when I rebooted it showed up and everything was fine.  Of course now I have printer driver issues, but it recognized the thing and printed a blank page nonetheless.  So I'd say the USB is working at least to some degree.  I'll continue to post here or on a new howto when I finally get it to where I want it.  Good to see another oldworld user here.

---

### Post by Yimmy on 2006-05-18
Well I had to put this to the side for a bit, but happy to report that my logitech optical usb mouse works "out of the box" so to speak.  No problems at all.  Just plugged it in when the machine was off and started it up.  Bam! It works.  Still no luck on the lexmark Z730 printer, but hopefully that will be resolved soon as well.  One question,  does anybody know how to get Ubuntu to automatically mount my hfsplus partition to the directory I created.  Can you enable drag and drop functionality to that drive once it's mounted, or do you have to use the terminal and cp.

James

---

### Post by xurios on 2006-05-19
> 
does anybody know how to get Ubuntu to automatically mount my hfsplus partition to the directory I created. Can you enable drag and drop functionality to that drive once it's mounted, or do you have to use the terminal and cp.

Add a line like this to /etc/fstab

```

/dev/hd<your partition>	/your/mount/directory	hfsplus rw,user,auto 	0	0

```
People around this forum seem to say that if you disable journaling on the hfs+ partition, you can write to it from the ubuntu side, but I have never tried. I can certainly drag things from my hfs+ directories in the gui.

---

### Post by Yimmy on 2007-01-10
An update on this.  I had the system running fine, tried to update to Dapper when it came out and it killed the system.  Haven't had a chance to look into why.  Not sure what I'll do from here on out.  Stinks that I had the whole thing up and running tried to upgrade and now I have a doorstop again.  Oh well.  If anybody else has had success please post.

---

