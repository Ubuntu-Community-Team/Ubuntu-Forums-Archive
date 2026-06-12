---
title: "chroot to md0 for &quot;rescue&quot; from live CD???"
date: 2005-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by f1d094 on 2005-06-13
By way of not having Pin preferences set properly, I just accidentally upgraded my libc6 library to "breezy" and have fuX0red my system.

My mistake was instantly obvious. Any references to the filesytem failed...the system slowly imploded and eventually locked when I tried to switch to tty1.

Selecting an older kernel or (recovery mode) results in a kernel panic as soon as it goes about 15 lines or so then:

[FONT=Fixedsys]VFS: Cannot open root device "md0" or unknown-block(0,0)[/FONT]

...this is for my oldest kernel "Ubuntu, kernel 2.6.10-5-amd64-generic (recovery mode)".

My most recent kernel "Ubuntu, kernel 2.6.11-1-amd64-k8 (recovery mode)" rocks along until:


[FONT=Fixedsys]mdadm: /devfs/md/0 has been started with 4 drives.
Stopping tasks: ====|
Freeing memory... done (1174 pages freed)
Restarting tasks... done
kjournald starting. Commit interval 5 seconds
EXT3-fs: mouned filesystem with ordered data mode.
exec: 428: chroot: not found
Kernel panic - not syncing: Attempted to kill init![/FONT]

And that's it folks.

I am booting off of a USB drive and have root on md0 raidset (raid 5, 4 drives) with tmp and swap being separate LVMs spanned across the same drives in separate partitions.

I understand that I could *reinstall* from scratch...but I'm fairly certain that their should be a way to boot off of a "Live CD" mount/chroot my actual root dir on /dev/md0 and then "roll back" my boo boo.

I think I'm heading in the right direction, but I could really use some handholding, as I'm nervous as hell to have to start over...it took me a month and a half of weekends to get it to the state where it is (my first desktop!):

AMD64 3800+ 4x SATA 250GB NVidia Geforce 6800 Ultra, Dual Head video, transcode working, mplayer all custom scripted up with home brew perl interface to handle "deregionized" lite-on DVD players and adjust according to language, region, and format (pal vs ntsc), mythtv running the whole show...

I really really really really wanted to show this at the next LUG meeting (my first!)

Help me out here guys and show me how tight the Ubuntu community is! Help me to share my (few but tasty) morsels of knowledge!

:-)

---

### Post by skylark on 2005-06-14
I'm only a Ubuntu newbie myself, migrating from a short stint with Debian so I doubt I have the answer. But I found an interesting thread on the Gentoo forums which might give you some ideas:  [http://forums.gentoo.org/viewtopic.php?p=930991](http://forums.gentoo.org/viewtopic.php?p=930991)

If it was just some config issue you could boot from CD using the AMD64 Ubuntu liveCD, try mounting your array, fix the issue then reboot as normal. The old package that provided libc6 probably exists on your original ubuntu install CD so you might be able to achieve it this way, although I'm not sure exactly how.

---

### Post by FluffyElmo on 2005-06-14
I just had this *exact* same problem..took some time yesterday to figure out how to fix it. Basically, you just have to update initrd from the Breezy repositories as well and it will boot normally. Here are the steps I followed:

First, boot from the 64bit Live CD and run a root terminal. You can't chroot from the 32bit Live CD into a 64bit system, you get an 'exec format error'. 

Mount your existing install and chroot into it. For my install on /dex/hda2 I did the following from the root terminal:
```

mkdir /mnt/hda2
mount /dev/hda2 /mnt/hda2
chroot /mnt/hda2
```

Then, still in the chroot, and with your /etc/apt/sources.list pointing to the Breezy repositories install initrd-tools and reconfigure your kernel to generate the initrd. 

```
apt-get install initrd-tools
dpkg-reconfigure linux-image-2.6.11-1-amd64-k8
exit
umount /dev/hda2

```

Finally, reboot and it should work. I'm still running 2.6.10-5 with the Breezy libc though, so if you still have trouble try the same procedure with the previous kernel.

---

