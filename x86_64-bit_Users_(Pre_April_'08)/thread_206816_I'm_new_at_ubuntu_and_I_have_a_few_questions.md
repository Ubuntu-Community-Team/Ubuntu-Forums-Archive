---
title: "I'm new at ubuntu and I have a few questions"
date: 2006-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by jaimz on 2006-06-30
ok so I saw that I can install mac os x themes to ubuntu
but I keep getting "file format is invalid" when I try to install it 

[http://users.utu.fi/ljtaim/ubuntuosx.php#themes]("http://users.utu.fi/ljtaim/ubuntuosx.php#themes")

the themes on there is what I want to install

Also

I would like to know if I could get into my other hdd's
that are ntfs format or whatever

I have most of my music, images, movies and stuff in there
and I was wondering if there's a way to get in it to probably use them

and one more thing
I downloaded the latest ATI drivers and when I tried to install in the terminal
I got this message saying only super user can do that 0_o
I'm the only user for this so I was wondering if there's a way to set myself as super user >_<

---

### Post by Sef on 2006-06-30
> I would like to know if I could get into my other hdd's
that are ntfs format or whatever


You need to reformat to another file system, e.g., ext3, reiferfs, etc.  Ubuntu can read ntfs, but can't save to it.  If you want to share files, then set up an ext2, ext3, or fat32 partition.


> I have most of my music, images, movies and stuff in there
and I was wondering if there's a way to get in it to probably use them

Depends on if the are DRMed or not.  If not, then most likely, you could play them.

> I downloaded the latest ATI drivers and when I tried to install in the terminal
I got this message saying only super user can do that 0_o
I'm the only user for this so I was wondering if there's a way to set myself as super user >_<

You should be set up as administrator.  Root is disabled by default, but sudo should do the trick.  If you don't have administrator rights, then most likely either the install was bad, or you set up a second account without administrative priviledges.  

[Read up on Root-Sudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by jaimz on 2006-06-30
ok thank you

---

### Post by PhilOSparta on 2006-06-30
[QUOTE=jaimz]
I would like to know if I could get into my other hdd's
that are ntfs format or whatever

I have most of my music, images, movies and stuff in there
and I was wondering if there's a way to get in it to probably use them
[/QUOTE]

You can mount and then read your ntfs formatted hard drives, but Ubuntu will not be able to write to them.  I understand that it is possible to write to them if you go through certain procedures, BUT you run the risk of corrupting or deleting data on the ntfs drives/partitions.

---

### Post by jaimz on 2006-06-30
[QUOTE=PhilOSparta]You can mount and then read your ntfs formatted hard drives, but Ubuntu will not be able to write to them.  I understand that it is possible to write to them if you go through certain procedures, BUT you run the risk of corrupting or deleting data on the ntfs drives/partitions.[/QUOTE]
well I don't plan to write anything on it from ubuntu

just wanted to get some files from them into ubuntu

I get this can't mount error

---

