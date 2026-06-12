---
title: "dpkg hates me, getting very annyoing"
date: 2008-08-18
forum: x86 64-bit Users
---

### Post by Nysomin on 2008-08-18
Well here it is, I'm running Ubuntu 8.04 on a reasonable OC'ed amd64 with both Gnome and KDE 4 installed.  I use Gnome for, well, everything since it uses(or at least it seems like it) less system resources.  KDE 4 is mainly just to play with, see how pretty I can make it.  I've been having a problem lately that I can't seem to fix.  Whenever I try to update any package, or even install a package, from either the Update manager or Adept Manager it gives me an error that tells me I have to run 'dpkg --configure -a' manually so I can install or update anything.  The only way I got this to work was to boot into recovery mode and then 'drop to a root shell', but now even then it gives me an error saying it was interrupted.

If anyone can help it would be great!  Oh, and if anyone knows why this happens and what I should avoid to prevent it, it would be a great help.  Thanks!

---

### Post by ibuclaw on 2008-08-18
Have you tried running:
```
sudo dpkg --configure -a
```
Manually?

Open up a console and copy and paste the above.
It's usually just a package that didn't quite finish installing/configuring.

Regards
Iain

---

### Post by Nysomin on 2008-08-18
Yes, I've tried that, and it never works.  It used to give me a error saying dpkg was interrupted, but now this is what it says:

```
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-20-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-20-generic
dpkg: subprocess post-installation script returned error exit status 1

```

So I guess I'll look into making some room.

---

### Post by ibuclaw on 2008-08-18
Interesting.
You don't suppose that you made a separate partition for the /boot folder, now, did you?

Type in
```
df -h
```
to show your mounted partition layout.

Regards
Iain

---

### Post by Nysomin on 2008-08-18
I did, I gave it 200 mb.  the folder is only saying 57 used, but only 3.4 free.  I also found that I have 3 kernels versons, 16,19 and 20.  I've been running in 19 while getting updates for 20...  20 doesn't boot correctly, won't let me into anything but low-graphics mode.  I think the problem stems from my attempt to install Grub 2.  I would like to try to start from scratch grub wise.  Know of any good ways to remove all that is grub and grub 2, and only install grub 2?

---

### Post by drs305 on 2008-08-18
> **Nysomin said:**
> I did, I gave it 200 mb.  the folder is only saying 57 used, but only 3.4 free.  I also found that I have 3 kernels versons, 16,19 and 20.  I've been running in 19 while getting updates for 20...  20 doesn't boot correctly, won't let me into anything but low-graphics mode.  I think the problem stems from my attempt to install Grub 2.  I would like to try to start from scratch grub wise.  Know of any good ways to remove all that is grub and grub 2, and only install grub 2?

Time to check the trash? I actually don't know in hardy if the trash would go in root's trash or into a /boot trash bin since it's a separate partition...
```
sudo find /boot -iname *Trash* | grep Trash
or more generally
sudo find / -type d -iname *Trash* | grep Trash
```

---

### Post by Nysomin on 2008-08-18
Alright, well here is my boot trash:

```
/boot/.Trash-0
/boot/.Trash-0/info/fiesta.xpm.gz.trashinfo
/boot/.Trash-0/info/gnome-debblue.xpm.gz.trashinfo
/boot/.Trash-0/info/CRW_7206_14.xpm.gz.trashinfo
/boot/.Trash-0/info/gnucheese.xpm.gz.trashinfo
/boot/.Trash-0/info/gunhole.xpm.gz.trashinfo
/boot/.Trash-0/info/firework.xpm.gz.trashinfo
/boot/.Trash-0/info/menu-sta.xpm.gz.trashinfo
/boot/.Trash-0/info/biosplash.xpm.gz.trashinfo
/boot/.Trash-0/info/debian_grey1-14col.xpm.gz.trashinfo
/boot/.Trash-0/info/debian-moreblue-swirl.xpm.gz.trashinfo
/boot/.Trash-0/info/guitar.xpm.gz.trashinfo
/boot/.Trash-0/info/gentleblue.xpm.gz.trashinfo
/boot/.Trash-0/info/bike_gua.xpm.gz.trashinfo
/boot/.Trash-0/info/debblue.xpm.gz.trashinfo
/boot/.Trash-0/info/mummy.xpm.gz.trashinfo
/boot/.Trash-0/info/debsplash.xpm.gz.trashinfo

```

I had tried to install a few boot splashes.  none of them worked.  Since I couldn't remember to terminal command to delete files I booted in single user mode, dropped into a root shell, startx, and I was free to remove whatever I wanted.  So now I am able to run dpkg fine.  So my initial problem is solved.  Next it's time to clean up my system, get rid of things that are just getting in the way(I love to play with KDE 4, but kdm and gdm aren't getting along right now).

Interesting side note.  I had been struggling for a while to be able to get into init3 to install nvidia drivers with no success.  Well, I didn't know that you could get into a root shell by the rescue boot.  Now I have no problem installing the latest nvidia drivers.

---

### Post by drs305 on 2008-08-18
> **Nysomin said:**
> Since I couldn't remember to terminal command to delete files I booted in single user mode, dropped into a root shell, startx, and I was free to remove whatever I wanted.  So now I am able to run dpkg fine.  So my initial problem is solved.  

You can run nautilus or another file browser with root privileges without leaving the normal session. Open it with the following and you can navigate and delete anything on the system, (including trash!):
```
gksu nautilus
```

The command you were probably thinking of was "sudo rm -rf" but it's a dangerous command to use, especially when you are using it around system folders ;-)

---

### Post by ibuclaw on 2008-08-18
Well, you can start by purging the proposed kernel.
```
sudo aptitude purge linux-image-2.6.24-20-generic
```
then try running
```
sudo dpkg -configure -a
```
again.

If you are still having problems, you may need to boot into your LiveCD and use GParted (Disk Partitioner) to resize your partitions round and grow the size of the /boot filesystem.

Try the "-configure -a" command again, then repeat the purge to clean your system of it.
Oh, and for future reference. I advise that you'd disable the "hardy-proposed" from your sources list. It is in proposed for a reason, and that reason doesn't have stability in it... ;)

Regards
Iain

---

### Post by Nysomin on 2008-08-19
Thanks!  I was thinking about doing that.  There were a few reasons why I have the proposed packages in update, one was KDE 4, and there were a few other ones, one had to do with nvidia and Blander and Yafray, but I forget why I need it for them.  Anyway, thanks for everyone's help.

---

### Post by Jouke74 on 2008-08-20
Seems like your partition is too full to run all updates.
Two other ways I know how to get more space with apt are:

sudo apt-get autoclean
sudo apt-get autoremove

First one cleans out / erases all the downloaded update DEBs from your harddisk. The second one erases all non-required dependencies. 
The second one is useful if you have installed packages, and afterwards erased them again.

---

### Post by Nysomin on 2008-08-21
Very cool, that'll help out.  Oh, one more side note, totally unrelated, how can you get Cairo-Dock to start automatically?

---

