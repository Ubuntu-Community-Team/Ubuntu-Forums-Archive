---
title: "Mac"
date: 2008-10-01
forum: Wine
---

### Post by ASPCartman on 2008-10-01
Hi everyone. I'm sorry, i don't know where should i place this thread, so please move it where it should be. Thx)

I have a little issue. I wanna play SkechFigher. It's 2d game for mac. It's download able in .dmg file. I don't now anything in macosx. (as u thought - i don't hace it). is there any emulation software (or some implementation like wine is) to help me? Thx)

---

### Post by asdfoo on 2008-10-01
> **ASPCartman said:**
> Hi everyone. I'm sorry, i don't know where should i place this thread, so please move it where it should be. Thx)

I have a little issue. I wanna play SkechFigher. It's 2d game for mac. It's download able in .dmg file. I don't now anything in macosx. (as u thought - i don't hace it). is there any emulation software (or some implementation like wine is) to help me? Thx)


No, Wine is for Windows programs only.

---

### Post by ASPCartman on 2008-10-01
I know that. Please read carefully

---

### Post by aoanla on 2008-10-01
Well, a dmg file is some kind of Mac HFS disk image file.

So, at the very least, you should be able to look at the files in it by doing something like:

mkdir ~/macdisk
sudo mount -t hfs -o loop myfile.dmg ~/macdisk

---

### Post by asdfoo on 2008-10-01
> **ASPCartman said:**
> I know that. Please read carefully

ok, sorry if I was dismissive. Your post is in the Wine section.

---

### Post by ASPCartman on 2008-10-03
> **aoanla said:**
> Well, a dmg file is some kind of Mac HFS disk image file.

So, at the very least, you should be able to look at the files in it by doing something like:

mkdir ~/macdisk
sudo mount -t hfs -o loop myfile.dmg ~/macdisk

Thanks, but i wanna play this thing, not look ^^ MAybe some simple emulators?

---

### Post by aoanla on 2008-10-03
Indeed, but if it's compiled for x86 Macs, you might be able to do something with the game if you extract it from the dmg to your home.

---

### Post by ASPCartman on 2008-10-06
aspcartman@aspcartman-laptop:~$ sudo mount -t hfs '/home/aspcartman/Desktop/sketchfighter.dmg' ~/macdisk -o loop
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



So? :(

aspcartman@aspcartman-laptop:~$ dmesg | tail
[126274.223787] rtc: lost 1 interrupts
[126302.045894] rtc: lost 1 interrupts
[126440.118964] rtc: lost 1 interrupts
[126444.738532] rtc: lost 1 interrupts
[126459.016400] rtc: lost 1 interrupts
[126687.871933] rtc: lost 1 interrupts
[126901.650609] rtc: lost 1 interrupts
[126931.160374] loop: module loaded
[126931.178809] hfs: can't find a HFS filesystem on dev loop0.
[126952.844395] hfs: can't find a HFS filesystem on dev loop0.

---

