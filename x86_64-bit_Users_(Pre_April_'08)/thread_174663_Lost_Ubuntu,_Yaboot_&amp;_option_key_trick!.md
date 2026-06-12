---
title: "Lost Ubuntu, Yaboot &amp; option key trick!"
date: 2006-05-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by xico on 2006-05-12
Hello geeks! I need your skill

G5 dual 1.8. Dapper on sda, OSX on sdb
I've lost Ubuntu, lost Yaboot and the option trick only works for OSX (if I select Linux the blue screen gets corrupted...).

I tried to boot from cd in rescue mode: when I type 
#mount /proc
can't mount
source: [http://ubuntuforums.org/showthread.php?t=102191&highlight=yaboot](http://ubuntuforums.org/showthread.php?t=102191&highlight=yaboot)

I tried to boot from cd and right away type:
cd-linux root=/dev/sdb3
it returns Unknown or corrupted file
source: [http://www.terrasoftsolutions.com/support/solutions/ydl_general/boot_functions.shtml](http://www.terrasoftsolutions.com/support/solutions/ydl_general/boot_functions.shtml)

Could anyone help? Thank you

Francois

---

### Post by imacQ on 2006-05-12
try booting from open firmware

hold down o, f, command and option key all at same time at startup to get to open firmware.

boot hd:<partition# here>,yaboot

whatever partition your yaboot is on.

---

### Post by xico on 2006-05-12
boot: Linux
Please wait, loading kernel...Unkwown or corrupt filesystem!


(and how can I exit this prompt, the box is about to take off with nine fans blowing full power?)

---

### Post by xurios on 2006-05-12
Pressing option at startup or even setting startup disk in system prefs (From OS X) will set the boot-device variable in nvram to something besides the partition used by yaboot. Worse, the startup disk pref won't see your yaboot startup partition, so you can't get back that way. 

My solution to this was, once I had things working the way I wanted, to dump my nvram settings to a file and save it somewhere.

From OS X:

nvram -p > file_name

The key nvram value here is: 

boot-device /pci@f4000000/ata-6@d/disk@0:4,\\:tbxi

(note, yours may use a different partition)

This tells my mac where to boot from. If I change my boot drive from system prefs, it changes boot-device and I now have:

boot-device     pci2/ata-6@D/@0:3,\\:tbxi

to get back to booting from yaboot:

sudo nvram boot-device=/pci@f4000000/ata-6@d/disk@0:4,\\:tbxi

So there is no need to boot into OpenFirmWare, you can always fix you setting in one clean step.

---

### Post by xico on 2006-05-12
Thanks for your answers, but I need you to tell me where I get the information to type after
boot-device=
how do I do this from the mac Terminal? The answer I get now is:
boot-device     hd:,\\:tbxi

I think things are really messed up. I would like to reinstall Yaboot or something to recover my system whithout formatting the whole thing.

I need a more "howto" advise.

Francois

---

### Post by xurios on 2006-05-12
Ok, I think I may have a way for you to figure out what value to put into boot-device:

First, go into the startup disk system pref and change to a working OS X startup volume, then CLOSE THE PREFS WINDOW. It won't write to nvram unless you close the window. Now, do the nvram -p in terminal and see what the value of boot-device is.

Next, still in terminal, do

[font=monaco]
diskutil list disk0
[/font]

My machine gives me this:

[font=monaco]```

:$ diskutil list disk0
/dev/disk0
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *93.2 GB  disk0
   1:    Apple_partition_map                    31.5 KB   disk0s1
   2:        Apple_Bootstrap                    977.0 KB  disk0s2
   3:              Apple_HFS Gato               83.3 GB   disk0s3
   4:        Apple_Bootstrap                    977.0 KB  disk0s4
   5:        Apple_UNIX_SVR2                    9.3 GB    disk0s5
   6:        Apple_UNIX_SVR2                    443.5 MB  disk0s6

```
[/font]

Notice that I have two Apple_Bootstrap partitions. One is the original OS X partition (number 2), the other is the yaboot partition (number 4). It may be that you have only one bootstrap partition, but I could never get Ubuntu to work when I tried to use my OS X bootstarp partition, so I imagine you probably have this setup as well. 

The next thing to do (I tested this) is to simply change the one digit in the current value of boot-device to point at the yaboot bootstarp partition. For my system, the startup disk pref set this into nvram:
[font=monaco]
boot-device     pci2/ata-6@D/@0:3,\:tbxi
[/font]

So I changed it to #4

[font=monaco]
sudo nvram boot-device=pci2/ata-6@D/@0:4,\:tbxi
[/font]

This gets me back into yaboot on startup.

---

### Post by xico on 2006-05-12
thanks for taking the time.

here are my partitions:

/dev/disk0
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *69.2 GB  disk0
   1:    Apple_partition_map                    31.5 KB   disk0s1
   2:        Apple_Bootstrap                    977.0 KB  disk0s2
   3:        Apple_UNIX_SVR2 UNTITLED           65.4 GB   disk0s3
   4:        Apple_UNIX_SVR2                    2.8 GB    disk0s4


/dev/disk1
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *152.7 GB disk1
   1:    Apple_partition_map                    31.5 KB   disk1s1
   2:              Apple_HFS OS X               152.5 GB  disk1s3

now,
G5:~ xico$ nvram -p            replied
boot-device     uata/@0:3,\:tbxi       that I changed to 
boot-device     uata/@0:2,\:tbxi        right? obvious

Doesn't work!

PS: I have access to my ubuntu /  through extfs2hfs  in read only. So I can fetch informations from there...

---

### Post by xurios on 2006-05-12
Hmm, something's fishey. System prefs set 

boot-device uata/@0:3,\:tbxi

to boot OS X, but there is no partition #3 with os x on your machine. That substitution souldn't for you work anyway, since you are using two separate drives for linux and os x, changing to another partition on the os x drive wouldn't help. I think your system is too different from mine (powerbook 1.33) for me to be of much more help, I'll probably just get you in trouble. Maybe you should either

a) Spend some time researching open firmware syntax and figure out how to list your drives and partitions from that environment, then try booting from partition 2, 3, and then 4 from the linux drive and see if you get it back. 

b) Cut your losses time-wise and re-install linux, then list out your nvram settings from os x and keep a copy in a safe place.

---

### Post by xico on 2006-05-12
Thanks for trying anyway!

Francois

---

### Post by xurios on 2006-05-12
New ideas:


Use ext2hfs to read the file at [font=monaco][color=blue]/etc/yaboot.conf[/color][/font] on your linux partition, and you will know what yaboot writes into boot-device for booting linux. Mine looks like this:

```

## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda4
device=/pci@f4000000/ata-6@d/disk@0:
partition=5
root=/dev/hda5
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda3

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

defaultos=macosx
```

So there is my boot drive device id for nvram: [font=monaco][color=blue]device=/pci@f4000000/ata-6@d/disk@0:[/color][/font]
Now I can put the pieces together:

This bit

[font=monaco]boot=/dev/hda4
device=/pci@f4000000/ata-6@d/disk@0:[/font]

Tells me that I should set 
[font=monaco][color=blue]boot-device=/pci@f4000000/ata-6@d/disk@0:4,\\:tbxi[/color][/font]

Which is just what I got from my nvram printout at the beginning of this journey, when I first looked at the setting from the working dual boot setup.

I hope this works. 

Bye the way, the yaboot man page is quite informative about the whole process.

---

### Post by xico on 2006-05-13
Here's my /etc/yaboot.conf:
-------------------------------------------------------------------------
## yaboot.conf generated by yabootconfig 1.0.8
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of: 
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda2
device=/ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@1/disk@0:
partition=3
root=/dev/sda3
timeout=30
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	initrd-size=8192
------------------------------------------------
kind of strange that 
/ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@1/disk@0:
isn't it?

I'd like to write 
uata/@0:2,\:tbxi
instead. But the ext2hfs is read only, how can I chmod it? I think ext2hfs doesn't allow this.
BTW: I don't have access to ubuntu terminal and man yaboot either.

---

### Post by xurios on 2006-05-13
I'm sorry, I meant that you could use the [font=monaco][color=blue]nvram[/color][/font] command from os x to change boot-device, based on what you find in the yaboot.conf file. This is because that file was written by the Ubuntu installer, and presumably has the correct info inside for booting into the screen where you are presented with the choice of booting linux, cd, or OS X. I didn't mean that you should do anything with yaboot.conf other than get some information from it, since if it was working before, then it should still be correct, unless you've moved your drives around or something.

So, judging from what is in *your* yaboot.conf file, I would, from OS X Terminal, try this:

[font=monaco][color=blue]sudo nvram boot-device=/ht@0,f2000000/pci@5/k2-sata-root@c/k2-sata@1/disk@0:2,\\:tbxi[/color][/font]

Which would hopefully be what you need to get into the yaboot boot-screen on startup.

The yaboot.conf man page (on my ubuntu installation) is  at [font=monaco][color=blue]/usr/share/man/man5/yaboot.conf.5.gz[/color][/font]
It's a .gz file, so you'll have to copy it somewhere that you have write privelages so you can write the uncompressed version. Normally, Preview can read man pages, but the pages from ubuntu don't seem to work. It will open with [ManOpen](http://www.clindberg.org) (or any text editor, but it will be full of formatting tags, *ugly*), but hopefully you can now boot into Ubuntu and read whatever man page you like from within linux.

---

### Post by xico on 2006-05-13
doesn't work either!
I'll study the man yaboot pages...
Thanks

Francois

---

