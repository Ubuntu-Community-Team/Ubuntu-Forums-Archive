---
title: "How does one stop apt from killing grub conf?"
date: 2007-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Inuyaga on 2007-04-16
Ok so anytime I get kernel update or anything that redoes grub my box is rendered unbootable and I am forced to remake grubs config file. (kopts do no work with my setup.) This is unacceptable. Is there a way to tell apt NOT TO F with my custom config files? Im also havening issues with some other configs as well. Im thinking something like the way portage works with merging configs interactively. If there isn't I would like to know so I can cut my losses at this point <_<

---

### Post by John Jason Jordan on 2007-04-16
> **Inuyaga said:**
> Ok so anytime I get kernel update or anything that redoes grub my box is rendered unbootable and I am forced to remake grubs config file. (kopts do no work with my setup.) This is unacceptable. Is there a way to tell apt NOT TO F with my custom config files? Im also havening issues with some other configs as well. Im thinking something like the way portage works with merging configs interactively. If there isn't I would like to know so I can cut my losses at this point <_<
When you say your "custom config files," what files are you referring to? Do you mean the menu.lst file?

The reason I ask is that every time I update a kernel I have to go into /boot/grub/menu.lst and change the partition back to the correct one. There are two ext3 partitions on this computer and Ubuntu is on hda2. For some reason kernel updates change that to hda3 (hd0,2 in grub-ese). The computer won't boot until I manually edit menu.lst to change it back to hda2.

Luckily for me I know how to do this. But I did not always know how to fix it and I remember the first time it happened I had to use a Windows computer to get on the net and learn how to edit menu.lst. It took me the better part of a day to get my computer booting again. If Ubuntu is to be easy for beginners, this is not acceptable.

---

### Post by Inuyaga on 2007-04-16
What needs to happen is either a much smarter menu.lst manager needs to be created or a conf merge system needs work.

I propose the use of entry template scripts.
So when doing an initial install of grub the installer asks the user if they want to set advanced options. Setting advanced options then sets up a script file.

In the script file define some vars along the lines of

NOTE NOT ACCL SCRIPT...

KOPTS = "root=/dev/hdc1"

#if root is defined in KOPTS set this to 1
ROOTNOSPEC = 1

#other options
NOSPLASH = 1
VERBOSE = 1

mabe some other nice options.....

Then have that call a another script file that generates a single entry. Incoming vars would be
TITLE = "title"
KERNEL = "kernel file"
INITRD = "initrd file"
KROOT = "generate root"

then generate the template entry like this.
print TITLE

KLINE = KERNEL

if not ROOTNOSPEC
    KLINE += " " + KROOT

KLINE += KOPTS

print KLINE
print INITRD

... print other options..

Then all of the above script is called for each entry in a gen script.

Anyway thats my 2 cents.

Well ill spend some time with the grub package and see if I can put something along thoes lines into it. If it works mabe it will be offical. God knows we need something better.

---

