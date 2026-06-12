---
title: "[SOLVED] a simple one - cannot unmount usb flash drive (device is busy???)"
date: 2008-06-23
forum: x86 64-bit Users
---

### Post by bluepowder7 on 2008-06-23
ok, i'm stumped on this simple one.  i have a 4G sandisk flash drive dangling off the front of the machine, and xubuntu 8.04-64 refuses to unmount it.  i'm not reading or writing to it, i emptied the trash, there's no other file browser accessing it.

if i try to right-click eject (unmount) it, i get a:

[IMG]http://i106.photobucket.com/albums/m244/GregR7/screenshots/cannot-unmount.jpg[/IMG]


and if i try to sudo umount it from the terminal, i get a:

[IMG]http://i106.photobucket.com/albums/m244/GregR7/screenshots/cannot-sudo-unmount.jpg[/IMG]

---

### Post by John Jason Jordan on 2008-06-23
> **bluepowder7 said:**
> ok, i'm stumped on this simple one.  i have a 4G sandisk flash drive dangling off the front of the machine, and xubuntu 8.04-64 refuses to unmount it.  i'm not reading or writing to it, i emptied the trash, there's no other file browser accessing it.
I do not know what the cause is, but I have a suggestion: Use the -l option. The -l option stands for "lazy," although that is kind of misnamed. What it means is "unmount this damn thing now and I mean it."

Another thing to look into is the Sandisk U3 crapware that they put on their thumb drives. On Windows it pops up a file browser window that has all kinds of Sandisk advertising on it. Sandisk thinks you want this. Sandisk can eat my shorts. If you want to get rid of it you have to go to their web site. Here is a link to it:

[http://kristagrothoff.wordpress.com/2006/08/24/removing-u3-and-associated-bundled-software-from-the-sandisk-cruzer-micro-usb-flash-drive/]("http://kristagrothoff.wordpress.com/2006/08/24/removing-u3-and-associated-bundled-software-from-the-sandisk-cruzer-micro-usb-flash-drive/")

---

### Post by bluepowder7 on 2008-06-23
sweet!  that -l option did the trick.  one thing i just noticed - the right-click menu of Thunar didn't say "unmount", only "eject".  is that where i hit the snag, or is it pretty well one and the same?  right after successfully doing the "sudo umount -l /media/disk" but before physically pulling the flash drive out of the usb port, the right-click menu on Thunar gave me the option of "eject" or "mount" - as if there were separate mount/unmount and load/eject commands.

actually, that sandisk never saw the u3 crapware.  as soon as i got it, i formatted the whole thing to ext2.  on the odd chance i actually fire up windows (last time was february), it sees nothing related to u3, just my files.  :)

---

### Post by jpryor68 on 2008-06-24
I don't know about the Thunar unmount-vs-eject. But one thing you can try if you encounter this again: in the Terminal type:

```
lsof | grep /media/disk

```

That will show you which applications have open files on that drive.

---

### Post by bluepowder7 on 2008-06-24
> **jpryor68 said:**
> 
I don't know about the Thunar unmount-vs-eject. But one thing you can try if you encounter this again: in the Terminal type:

```

lsof | grep /media/disk

```

That will show you which applications have open files on that drive.



thanks!  that's a good command to know - i was just thinking of asking exactly that.  gonna add it to my "lil' book of useful commands to know".

---

### Post by soxs on 2008-06-25
> **bluepowder7 said:**
> thanks!  that's a good command to know - i was just thinking of asking exactly that.  gonna add it to my "lil' book of useful commands to know". me too^^

---

