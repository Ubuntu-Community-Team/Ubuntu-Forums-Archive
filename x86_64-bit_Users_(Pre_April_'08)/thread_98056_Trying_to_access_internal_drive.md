---
title: "Trying to access internal drive"
date: 2005-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by tig66 on 2005-12-02
Hi,

Firstly, apologies to all, but I am clueless on unix command line prompts and I'm hoping that someone is able help me.

My PB 15" aluminium internal drive (formatted hfs+ journaled) won't mount and I'm consequently unable to boot up. Trying to run it in Firewire Target Disk mode also doesn't mount the disk for access via another Mac.. basically, the disk is nowhere to be found!

I was told that using Ubuntu Live CD would allow me to change the internal drive from read/write to read only and (hopefully) that would allow the drive to mount.

So far, I've successfully run Ubuntu OK (booted with 'Live') and can now at least see the offending drive via System>Administration>Disks - this shows up on Partition 3 as Device: /dev/hda3 with the Status set as Inaccessible - although trying to enable this has no effect.

My question is, how do I get this drive to mount, in order that I can copy all my data off to an external drive and then reformat using my OSX 10.4 CD?  I have tried mount command lines from this forum but they won't work as I keep getting the message 'only root can do that'

Once again apologies for my naivety, but any advice or run-through of what I need to do would be gratefully welcomed!

Thanks

---

### Post by Entity on 2005-12-02
[QUOTE=tig66]Hi,

Firstly, apologies to all, but I am clueless on unix command line prompts and I'm hoping that someone is able help me.

My PB 15" aluminium internal drive (formatted hfs+ journaled) won't mount and I'm consequently unable to boot up. Trying to run it in Firewire Target Disk mode also doesn't mount the disk for access via another Mac.. basically, the disk is nowhere to be found!

I was told that using Ubuntu Live CD would allow me to change the internal drive from read/write to read only and (hopefully) that would allow the drive to mount.

So far, I've successfully run Ubuntu OK (booted with 'Live') and can now at least see the offending drive via System>Administration>Disks - this shows up on Partition 3 as Device: /dev/hda3 with the Status set as Inaccessible - although trying to enable this has no effect.

My question is, how do I get this drive to mount, in order that I can copy all my data off to an external drive and then reformat using my OSX 10.4 CD?  I have tried mount command lines from this forum but they won't work as I keep getting the message 'only root can do that'

Once again apologies for my naivety, but any advice or run-through of what I need to do would be gratefully welcomed!

Thanks[/QUOTE]

In order to mount this partition you need to be root or you can simply use sudo to do so :

```
sudo mount -t hfsplus /dev/hda3 /mnt
```

If the partition doesn't mount, well maybe the partition is simply corrupted. Did you try anything that has to do with partioning?

---

### Post by tig66 on 2005-12-02
Thanks for this.. OK I've done that and the drive is now showing as enabled - although not actually showing on my desktop or under 'Places' menu?

I can see my folders using the browse button, but am unable to copy or drag anything onto my external drive - should this be possible?

In answer to your question - no, I've not done anything to do with partitioning.

Is there anything else I can do to enable me to copy my files off and then re-format the drive under OSX?

---

### Post by Entity on 2005-12-02
If you can read the data on the internal drive's partition, you will be able to copy its data depending on the files' permissions.

Maybe you can't write to the external drive? Is it HFS+ also? Make sure the external drive isn't mounted read-only and that it's writable by your user.

try the following...

```
sudo cp -a /mnt /media/usbdisk
```

Where "/mnt" is where you mounted your internal drive's partition and /media/usbdisk is your mounted external USB drive.

---

### Post by tig66 on 2005-12-02
My external drive is formatted HFS+ also (firewire drive not usb)

OK.. I tried your suggestion, but then I got about 9 lines of Input/output errors listed in the console ie.:

cp: reading '/mnt/ Log File': Input/output error    etc...

+ a 'Segmentation fault' on the last line?

I entered:
sudo cp -a /mnt /media/LaCie80

Hopefully this was correct, as the only file path showing for my internal drive was /mnt

How do I make sure that my external drive isn't read only?

Thanks for your help so far..

---

