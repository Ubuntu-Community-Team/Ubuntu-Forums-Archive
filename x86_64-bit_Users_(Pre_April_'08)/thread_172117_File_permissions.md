---
title: "File permissions"
date: 2006-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Izza on 2006-05-08
I'm trying to change permissions on a folder, and all of it's subfolders & contents, but I keep getting errors saying I'm being denied.

I've seemingly tried everything... nothing is working.

Anyone know what to do here? Is there some way to force permissions?

---

### Post by Parkotron on 2006-05-08
How exactly are you trying this? Exactly what error are you getting?

Are you the owner of the files you're trying to change the ownership of? To change file ownership you must either have root priviliges or own the files ot begin with.

---

### Post by Izza on 2006-05-08
I'm the owner of the folder and contents... I've tried as root as well, and I keep getting an error saying it cannot delete the file, access denied, and I cannot write to the folder either, it also says access denied. I've tried overwriting the files using Ark (run both as root and user), and selecting the file to be overwritten and deleting in Konqueror... with both of those methods failing, I attempted to set permissions, to no avail. It says access denied each time.

---

### Post by Parkotron on 2006-05-08
The files aren't, by any chance, on a filesystem that's been mounted read only, are they? Can you copy the files? Can you open them in the appropriate application?

Could you please post the exact terminal contents you get when trying to move, delete or chown the files?

---

### Post by Izza on 2006-05-08
I got it figured out... my account being part of the group root, and sudo, screwed things up. Fixed that, and now I can modify files just fine.

Thanks for the responses!

---

### Post by charleseddy on 2006-12-24
ok, i have the same problem, but i *am* trying to change permissions to a filesystem mounted as read-only.  Is there any way to mount it with write permission every time the OS starts up?  When I installed Ubuntu I had it mount the filesystem every time, but I didn't select a read-only option.  Any way to change this.  It is NTFS.

---

### Post by taurus on 2006-12-24
If you want to write to ntfs filesystem, then you need to install ntfs-3g instead of ntfs...

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

