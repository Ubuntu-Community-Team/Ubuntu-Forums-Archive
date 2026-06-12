---
title: "HDD's device names changing randomly"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by rev_b on 2008-05-05
This is very annoying and I don't remember this happening with 32-bit kernels.
I have 3  hardrives, 2 internal (1 sata and 1 IDE) and one USB, problem is Ubuntu seems to randomly change the /dev name! Sometimes drive 1 is /dev/sda and drive 2 is /dev/sdb, and it randomly changes!. The usb drive does have a new name every boot, but it automounts itself anyway in /media/disk.

That's very annoyng because I have /etc/fstab with /dev/sd* identifying partitions and sometimes boot is halted with a error message because partition /dev/sd* does not contain a valid ext2 filesystem; gess what, it doesn't because doing fdisk -l shows that drive 1 is now /dev/sdb and drive 2 is /dev/sda!

I rewrote fstab using UUID to see what happens, but this is kind of annoying...

Any ideas?

---

### Post by nix4me on 2008-05-22
This is happening to me too.  How do I get UUID of each drive?

---

### Post by Yellow Pasque on 2008-05-22
```
cd /dev/disk/by-uuid/; ls -la
sudo lshw -businfo -C disk
```

---

### Post by Snarl on 2008-05-23
This is also affecting me, and it's infuriating.  HPFS partitions have *no* UUID or label.  JFS partitions formatted in OS/2 do not have unique UUIDs.  So using UUIDs in fstab is not only ugly, but also useless.

If the system can't enumerate the drives the same way each time (which it's incapable of), then I'm just going to delete it and find a linux distro that works.

---

### Post by chrisccoulson on 2008-05-23
> **nix4me said:**
> This is happening to me too.  How do I get UUID of each drive?

```
sudo blkid
```

Snarl: As for no UUID's or labels with JFS/HPFS - I'm not sure how you get around it. Switching distro's probably won't help, as UDEV dynamically allocates device nodes in pretty much the same way across distro's. If you want persistent device nodes, you'll have to learn how to write UDEV rules.

Please search on the forums for people with similar issues with JFS/HPFS. I'm sure you're not the only person on here that uses them

---

### Post by Snarl on 2008-05-23
No, but switching distros would allow me to specify the device *name* in fstab and be sure the same drive mounts each boot.  That's what Ubuntu can't do.

---

### Post by chrisccoulson on 2008-05-23
You can do the same in Ubuntu as in all the other distro's. What are you trying to do? You can identify a device in your fstab by LABEL, UUID or device node, like you can in any distro. You should use UUID or LABEL to identify a device, as it is well known that device nodes (/dev/sdxx) are not always persistent - and that applies across all distro's. I assume you're having problems with changing device nodes. To fix that, you'll need to add UDEV rules to make them persistent if you want touse these device nodes in your fstab to identify your disks- and you'd have to do that with any distro.

---

### Post by Snarl on 2008-05-23
Well known? By whom? Since when?  I have 5 different linux versions currently installed going back to RH7, and I've been dabbling with linux since ca. 1995.  I've *never* seen this problem before Ubuntu 8.04.

---

### Post by mannheim on 2008-05-23
I've never used jfs, but the [manpage of jfs_tune]("http://jfs.sourceforge.net/project/pub/jfs_tune.html") seems to imply you can set and change the UUID or label on a jfs volume with this command-line utility.

---

### Post by Snarl on 2008-05-23
> **mannheim said:**
> I've never used jfs, but the [manpage of jfs_tune]("http://jfs.sourceforge.net/project/pub/jfs_tune.html") seems to imply you can set and change the UUID or label on a jfs volume with this command-line utility.

That's true, I did use jfs_tune and it works.  But I still have an important HPFS partition on /dev/sdc3, and it won't mount reliably because it's not *reliably* on /dev/sdc.  And that's ridiculous.

---

### Post by aaron.d on 2008-05-23
> **Snarl said:**
> Well known? By whom? Since when?  I have 5 different linux versions currently installed going back to RH7, and I've been dabbling with linux since ca. 1995.  I've *never* seen this problem before Ubuntu 8.04.

for the curious, here is some reading on udev/devfs:

[http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev_vs_devfs](http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev_vs_devfs)

[http://www.kroah.com/linux/talks/ols_2003_udev_paper/Reprint-Kroah-Hartman-OLS2003.pdf](http://www.kroah.com/linux/talks/ols_2003_udev_paper/Reprint-Kroah-Hartman-OLS2003.pdf)

---

### Post by Yellow Pasque on 2008-05-23
FWIW, Ubuntu Feisty/Gutsy/Hardy never changed /dev mapping, but Arch Linux does for me.

---

### Post by buntunub on 2008-05-23
Interestingly, I have an external USB HD which always mounts as /dev/sdd.. Always. However, it has two partitions on it (ext3 and xfs) which always mount differently. IE. they swap /dev/sdd1 and /dev/sdd2 around. This of course plays havoc on my Mythtv system because I use it for all my recording and ringbuffer groups. Serious pain in the **** to reconfigure Mythtv backend every time I reboot, or am forced to reboot due to updates like yesturdays. How can I ensure that these mount reliably, in the same order, each time?

---

### Post by chrisccoulson on 2008-05-23
> **Snarl said:**
> Well known? By whom? Since when?  I have 5 different linux versions currently installed going back to RH7, and I've been dabbling with linux since ca. 1995.  I've *never* seen this problem before Ubuntu 8.04.

Older versions used devfs, as someone has already kindly pointed out to you. devfs used a static /dev. UDEV dynamically populates the entries unser /dev based on a set of rules and is triggered by events from the kernel. The devices will get allocated in the order that the hardware devices 'appear', so by virtue of the way it operates, you CANNOT guarantee that your devices get the same device node each time you boot, unelss you can guarantee that all of your devices always come up in exactly the same order. This is made especially worse when the system may or may not be booted with removable drives plugged in.

This happens across distro's, which is why most of them identify disks using LABELS and UUID's (not device nodes). It happens, it is real, and if you search on Google you will find other people using other distro's with the same problem, and other evidence that device nodes can and do change between boots. Stop burying your head in the sand and pretending it only happens on Ubuntu.

*Edit: I've done a search for you. Now please back up your claims with some evidence too*
Some examples:
[http://www.linuxquestions.org/questions/linux-general-1/grub-boot-hard-disk-make-root-option-a-variable-devsda1-keeps-changing-525350/]("http://www.linuxquestions.org/questions/linux-general-1/grub-boot-hard-disk-make-root-option-a-variable-devsda1-keeps-changing-525350/")
[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/405007120831]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/405007120831")
[http://wikis.sun.com/display/BigAdmin/Using+Disk+Labels+on+Linux+File+Systems]("http://wikis.sun.com/display/BigAdmin/Using+Disk+Labels+on+Linux+File+Systems")
[http://wiki.archlinux.org/index.php/Persistent_block_device_naming]("http://wiki.archlinux.org/index.php/Persistent_block_device_naming")

---

### Post by Snarl on 2008-05-23
> **aaron.d said:**
> for the curious, here is some reading on udev/devfs:

[http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev_vs_devfs](http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev_vs_devfs)

[http://www.kroah.com/linux/talks/ols_2003_udev_paper/Reprint-Kroah-Hartman-OLS2003.pdf](http://www.kroah.com/linux/talks/ols_2003_udev_paper/Reprint-Kroah-Hartman-OLS2003.pdf)

Thanks, that should help.  It's curious that this never happened to me in SuSE 10.x or Ubuntu 7.x, though.

---

### Post by aaron.d on 2008-05-23
> **Snarl said:**
> That's true, I did use jfs_tune and it works.  But I still have an important HPFS partition on /dev/sdc3, and it won't mount reliably because it's not *reliably* on /dev/sdc.  And that's ridiculous.

I think the point is that this is NOT distro specific, and you may understand better if you familiarize yourself with the history of device naming schemes.

---

### Post by aaron.d on 2008-05-23
> **Snarl said:**
> Thanks, that should help.  It's curious that this never happened to me in SuSE 10.x or Ubuntu 7.x, though.
np.

Therein lies the problem, using the default configuration, it is really luck of the draw (quite literally) with dynamically assigned dev naming. You cant have it both ways, assignments are either dynamic and work on the fly, or they are static, and (generally) require configuration of some sort.

I rely on UUID, but for FS types who dont have the benefit of UUIDs, some further configuration is needed to have a static (read: reliable) setup.

---

### Post by mannheim on 2008-05-23
What does "vol_id" return for an hpfs volume. Eg, assuming that the volume is at /dev/sdd1 today,
```
sudo vol_id /dev/sdd1
```
Is there no uuid listed, and no label either?

Edit: In OS/2, you apparently can change the label of a volume:

```

LABEL drive text
    You can change the name attached to a disk in the specified drive using this command.

```

Does linux not recognize the label?

---

### Post by buntunub on 2008-05-23
> **mannheim said:**
> What does "vol_id" return for an hpfs volume. Eg, assuming that the volume is at /dev/sdd1 today,
```
sudo vol_id /dev/sdd1
```
Is there no uuid listed, and no label either?

Edit: In OS/2, you apparently can change the label of a volume:

```

LABEL drive text
    You can change the name attached to a disk in the specified drive using this command.

```

Does linux not recognize the label?

Each partition has a seperate UUID. Cant remember which atm as im at work, but I do know that much.

---

### Post by Snarl on 2008-05-23
> **mannheim said:**
> What does "vol_id" return for an hpfs volume. Eg, assuming that the volume is at /dev/sdd1 today,
```
sudo vol_id /dev/sdd1
```
Is there no uuid listed, and no label either?

```
~$ vol_id /dev/sdc3
/dev/sdc3: error opening volume

```

> Edit: In OS/2, you apparently can change the label of a volume:


Does linux not recognize the label?

Nope. Nor even on JFS, which is odd.  They must use different fields.  As it happens my JFS drives now have two labels: one written by OS/2, and one written by jfs_tune (along with UUID).

---

### Post by Snarl on 2008-05-23
> **mannheim said:**
> What does "vol_id" return for an hpfs volume. Eg, assuming that the volume is at /dev/sdd1 today,
```
sudo vol_id /dev/sdd1
```
Is there no uuid listed, and no label either?

Sorry, forgot sudo:

```

~$ sudo vol_id /dev/sdc3
ID_FS_USAGE=filesystem
ID_FS_TYPE=hpfs
ID_FS_VERSION=197
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

```

---

### Post by buntunub on 2008-05-23
> **Snarl said:**
> ```
~$ vol_id /dev/sdc3
/dev/sdc3: error opening volume

```



Nope. Nor even on JFS, which is odd.  They must use different fields.  As it happens my JFS drives now have two labels: one written by OS/2, and one written by jfs_tune (along with UUID).

I suspect you got that error because you did not run the command as sudo.

---

### Post by mannheim on 2008-05-23
> **Snarl said:**
> Sorry, forgot sudo:

```

~$ sudo vol_id /dev/sdc3
ID_FS_USAGE=filesystem
ID_FS_TYPE=hpfs
ID_FS_VERSION=197
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

```

That's sad. This is clearly a limitation of vol_id (on which udev depends, I think). Here's some info from the udev source:
```
vol_id will only return successful if the string asked for, is not
empty. All trailing whitespace will be removed, spaces replaced by underscore
and slashes ignored.

fstype                 probe  label  uuid  version
--------------------------------------------------
linux swap             *      *      *     *
ext                    *      *      *     *
reiserfs jr/3.5/3.6/4  *      *      *     *
fat (12, 16, 32)       *      *      *     *
ntfs                   *      *      *     *
jfs                    *      *      *     -
xfs                    *      *      *     -
hfs (plus, wrapped)    *      *      *     -
udf                    *      *      -     -
iso9660                *      *      -     -
ufs                    *      -      -     -
cramfs                 *      *      -     -
sysv                   *      *      -     *
luks                   *      -      *     -
hpfs                   *      -      -     -
romfs                  *      *      -     -
squashfs               *      -      -     -
minix                  *      -      -     *
ocfs (1, 2)            *      *      *     *
vxfs                   *      -      -     *
nss (netware)          *             *     *
gfs, gfs2              *      -      -     -

```

---

### Post by buntunub on 2008-05-23
Well, reading through those posted articles were interesting, and pointed to the fact that namedev needs to be modified somehow to create stable mount points, but beyond that, its really not that helpful. For Snarls case, he could just assign by bus id or placement on the bus. Since my case involves a USB HD, things are a bit different when were talking about partitions on that same drive. It must have a USB serial, plus some type of file id, plus bus id and placement info. As far as I can tell via Google, the command vol_id, really has nothing to do with obtaining the needed info for the task we are trying to accomplish here, although I could be wrong? What is needed, is a command that produces some, or all of the info specified in the articles you posted here, probably something like df -h, or ls (various options here), or fdisk perhaps? Maybe even something like lspci or lsusb (for obtaining bus info). At that point, it sounds like the manual configuration of the file namedev would be in order (wherever that file is), and then perhaps a restart of udev?..

Thats the type of help that is needed at this point, since we now know all about udev and etc. Appreciate any info.

---

### Post by Snarl on 2008-05-23
For my part, this is now solved.  udev is not exactly intuitive, but I've managed to create a symlink in /dev that will ensure the partition is always mounted.

First I wrote 10-local.rules in /etc/udev/rules.d:
```

KERNEL=="sd[a-z]3" ATTR{start}=="13333950" ATTR{size}=="25607610" ATTRS{size}=="976773168" SYMLINK+="os2" OPTIONS+="last_rule"
```

and created /dev/os2.  Then I used that as the device name in fstab. Voila, it works.

It seemed to me safer to describe the partition than the bus enumeration, which may be no more predictable than sysfs's.  I also have two identical Seagate 500GB drives, so using ATTRS{model} would be tricky.

For your problem with USB, I'm pretty sure the answer you need is here: [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

Thanks to whoever posted that, I'll have to go back and look.

---

### Post by buntunub on 2008-05-23
> **Snarl said:**
> For my part, this is now solved.  udev is not exactly intuitive, but I've managed to create a symlink in /dev that will ensure the partition is always mounted.

First I wrote 10-local.rules in /etc/udev/rules.d:
```

KERNEL=="sd[a-z]3" ATTR{start}=="13333950" ATTR{size}=="25607610" ATTRS{size}=="976773168" SYMLINK+="os2" OPTIONS+="last_rule"
```

and created /dev/os2.  Then I used that as the device name in fstab. Voila, it works.

It seemed to me safer to describe the partition than the bus enumeration, which may be no more predictable than sysfs's.  I also have two identical Seagate 500GB drives, so using ATTRS{model} would be tricky.

For your problem with USB, I'm pretty sure the answer you need is here: [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

Thanks to whoever posted that, I'll have to go back and look.

Thanks Snarl. I also found [this]("http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/") for more info.

---

### Post by buntunub on 2008-05-23
K, I thought I would put together a little info block since two of us got through this successfully it seems.

Clickys:

[Writing udev rules]("http://www.reactivated.net/writing_udev_rules.html")
[USB HD specific udev rule guide]("http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/")

Commands of interest:

```
sudo ls -lR /dev/disk
```

This gives all relevant info for your drives and removables as udev sees them. You will need this info to write the rules from those guides.

```
udevinfo -a -p $(udevinfo -q path -n /dev/sd??)
```

This gives SYSFS info for an unmounted drive, which you will most likely also need for writing udev rules.

Many ways to do this, so follow those guides/how to's closely. Also of interest are the two info guides posted earlier in the thread about udev. Seems hard at first, but its really quite the breeze to do. Here is my rules and fstab entries for an example:

/etc/udev/rules.d/10-local.rules

```
## This is my mythtv drive.
BUS=="usb", KERNEL=="sdd2", SYSFS{manufacturer}=="usb-STECH_Simple_Drive_0010101640000000l-0:0-part2", NAME="%k", SYMLINK+="mythdrive"

## this is my storage drive for my kids itunes crap.
BUS=="usb", KERNEL=="sdd1", SYSFS{manufacturer}=="usb-STECH_Simple_Drive_0010101640000000l-0:0-part1", NAME="%k", SYMLINK+="khaleds_drive"
```

and fstab

```
#usb mythdrive
/dev/sdd2 /media/mythdrive xfs rw,user,noauto 0 0
#usb khaleds_drive
/dev/sdd1 /media/khaleds_drive ext3 rw,user,noauto 0 0

```

Note that those drive values are specific to my setup, so you will need to swap some values around to suit your own. Also, when it comes to the rules, read the rules guide carefully, as there are many, many ways to do this. I just chose what I felt was the best suited to my servers setups. Snarl, above, chose a different way, and that suits him. Have fun!

---

### Post by Snarl on 2008-05-23
> **buntunub said:**
> 
```
## This is my mythtv drive.
BUS=="usb", KERNEL=="sdd2", SYSFS{manufacturer}=="usb-STECH_Simple_Drive_0010101640000000l-0:0-part2", NAME="%k", SYMLINK+="mythdrive"

## this is my storage drive for my kids itunes crap.
BUS=="usb", KERNEL=="sdd1", SYSFS{manufacturer}=="usb-STECH_Simple_Drive_0010101640000000l-0:0-part1", NAME="%k", SYMLINK+="khaleds_drive"
```

I suspect you'll have to use wildcards for the KERNEL parameter, since it's the drive enumeration that's the problem.  If you knew they'd be /dev/sdd1 and /dev/sdd2 reliably then you wouldn't need any of this.

> 

```
#usb mythdrive
/dev/sdd2 /media/mythdrive xfs rw,user,noauto 0 0
#usb khaleds_drive
/dev/sdd1 /media/khaleds_drive ext3 rw,user,noauto 0 0

```

Now here you're not accomplishing anything, sorry to say.  You're mounting an explicit device, /dev/sdd1, to a directory in your /media path.  What your udev script has done, however, is to link /dev/sd?? to /dev/khaleds_drive.  So *that's* what you need to mount:

```

/dev/khaleds_drive /media/khaleds_drive ext3 etc,etc
```

---

### Post by Snarl on 2008-05-23
> **Snarl said:**
>  What your udev script has done, however, is to link /dev/sd?? to /dev/khaleds_drive.  

PS, You'll also have to
```
sudo mkdir /dev/khaleds_drive
```

before this will work.

---

### Post by buntunub on 2008-05-23
> **Snarl said:**
> I suspect you'll have to use wildcards for the KERNEL parameter, since it's the drive enumeration that's the problem.  If you knew they'd be /dev/sdd1 and /dev/sdd2 reliably then you wouldn't need any of this.

Well, your right, but in my case, the trouble was not the mount points, but the order they were mounting that was wrecking havoc. sdd1 and sdd2 are both on a USB HD, and mount in whatever order udev sees them first. Sometimes, they mounted as /dev/sdd1 = /media/disk, and sometimes it mounted as /dev/sdd1 = /media/disk-1, and vica verca. This caused alot of problems for me because sdd2 = xfs = mythtv data, and I was forced to reset the mythtvbackend alot to keep synch. This also causes problems with cron jobs like backups for people in that same scenario. It mounts every time as sdd though, so at least I dont have that problem. Anyway, the beauty and the curse of udev is that it mounts things seemingly on the fly, but at least you can easily write rules to specify HOW it does this in userspace. At least thats how I see it, feel free to let me know if im wrong.

> PS, You'll also have to
Code:

sudo mkdir /dev/khaleds_drive

before this will work.

Yes, that is correct. Following the guide I listed, you do that just after adding the fstab entries.

---

### Post by Snarl on 2008-05-23
> **buntunub said:**
> Anyway, the beauty and the curse of udev is that it mounts things seemingly on the fly, but at least you can easily write rules to specify HOW it does this in userspace. At least thats how I see it, feel free to let me know if im wrong.

Well, udev works *all* the time.  Udev is, from my perspective, the source of the problem.  So what your udev script is for is to change udev's behavior.  And indeed, the script you've written links the two usb drives to two static directory names in your /dev directory.  

So I won't quibble about whether they're really /dev/sdd1 and /dev/sdd2 all the time, but I suspect they won't be.  However, unless you specify the names of the symlinks your script creates as the devices to mount, you're not actually doing anything at all with this script.  ;)

---

### Post by buntunub on 2008-05-23
So your saying then that all I really need are fstab entries assuming that the USB HD always mounts as sdd?

---

### Post by Snarl on 2008-05-23
> **buntunub said:**
> So your saying then that all I really need are fstab entries assuming that the USB HD always mounts as sdd?

Yep.

But that's what I've learned you can't assume.  My problem, and the original poster's, is that PATA and SATA drives come up with *different* device names during boot, so this makes it impossible to use "/dev/sdc3" in fstab.  

If your usb partitions are always named /dev/sdd1 and sdd2, you don't need to do anything.  If, however, you find the partition device names are changing on you, that's what you need a udev script for.  And the point of the udev script is to describe the devices by some other means than /dev/sd[a-z][0-9], and link them to static paths in /dev.

---

### Post by buntunub on 2008-05-23
Yea. Makes sense now. I suspect your probably right and this will happen to me on the next reboot. Hasent happened yet by just mounting and unmounting, but well see. If I get what your saying still, then all ill need to do is put wildcards in for the mountpoints and ill be fine for the udev script if that happens.

---

### Post by Snarl on 2008-05-24
Yes.  I'd do it like this:
```

## This is my mythtv drive.
BUS=="usb", KERNEL=="sd[a-z]2", SYSFS{manufacturer}=="usb-STECH_Simple_Drive_0010101640000000l-0:0-part2", NAME="%k", SYMLINK+="mythdrive"

```

You could substitute '[0-9]' for the '2', but I'm guessing that's the 2nd partition on the device, so it will always be enumerated as such.  It's the device name 'sdd' that's most likely to change.

This script will link *whatever* the device name is, be it /dev/sdd2 or /dev/sdz2, to /dev/mythdrive, which is guaranteed to be there.

Then, put this in fstab:
```

#usb mythdrive
/dev/mythdrive /media/mythdrive xfs rw,user,noauto 0 0
```

...because you want to mount the link you just created, not the hit-or-miss kernel name.

---

### Post by nix4me on 2008-05-24
Just wanted to report back.  This was happening to me after every reboot.  All 3 of my drivers were getting mounted as different letters.  I switched to using UUID in the fstab and all is fine now.

---

### Post by buntunub on 2008-05-24
What a great thread this is. Thanks for the updates Snarl, and I hope this thread helps others to fix their setups as well. I hope this thread keeps going as others learn new ways to get things just right. Feel free all to post your setups!

---

