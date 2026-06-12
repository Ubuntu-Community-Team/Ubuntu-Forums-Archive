---
title: "Windows Mounts on Desktop"
date: 2005-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by pailhead on 2005-08-12
Ok, I've got 3 windows ntfs mounts setup in my /media/music 1 and a few others. Well for some reason my mounts are not showing up on the desktop. My DVD does when I instert a disk into it but the mounted drives do not.  Is there something I need to do to add them?  They showed up after I installed the 64bit dvdcss library but after a reboot they were now gone. 

Is there a way to get them onto the desktop?

Thanks..

---

### Post by amohanty on 2005-08-12
Use the Places->Network Share (or something to that effect) menu item to set them up. they will show up. Thats the easiest way. 

Do you mount them in your fstab?

AM

---

### Post by pailhead on 2005-08-13
[QUOTE=amohanty]Use the Places->Network Share (or something to that effect) menu item to set them up. they will show up. Thats the easiest way. 

Do you mount them in your fstab?

AM[/QUOTE]
 Yeah they aren't network shares really.. but they are mounted in my fstab.  They are seperate partitions on my one disk.

---

### Post by NickB on 2005-08-13
The easiest way is to make a symlink in the Desktop folder in your home directory.  Barring that, navigate to the folder in the GUI, middle click and drag the folder to the desktop, and select "Link here."

Nick

---

### Post by pailhead on 2005-08-14
[QUOTE=NickB]The easiest way is to make a symlink in the Desktop folder in your home directory.  Barring that, navigate to the folder in the GUI, middle click and drag the folder to the desktop, and select "Link here."

Nick[/QUOTE]
 Yeah I tried that but the icon then has a lock on it (visibly) and the shortcut icon.  I'd like to have the icons sans the lock icon.. is that a root thing?

---

### Post by NickB on 2005-08-14
The lock means it's read only.  That can happen if root owns the files, or you've mounted read-only (which is what I do, as I don't quite trust linux not to destroy my Windows NTFS).  You have a few choices here:

1. Use mount options to set the uid and gid to your login's uid/gid.
2. Use mount options to keep the uid as root, but the gid as a group you are in, then set the umask to allow group write.
3. Keep it mounted as root, but set the umask so it's writable by everyone (not recommended, even though you may be the only one using your system.

Type "man mount" and look for the ntfs options for more details.

Nick

---

### Post by varunus on 2005-08-14
Also, make sure your fstab passes it the "user" option.  This will make your drives show up in the "computer" place.

---

### Post by fistfullofroses on 2005-08-16
[QUOTE=pailhead]Yeah I tried that but the icon then has a lock on it (visibly) and the shortcut icon.  I'd like to have the icons sans the lock icon.. is that a root thing?[/QUOTE]
 to get rid of the "read only" / "lock icon" go to your terminal
type in "sudo -s"
enter your pw
then type "nautilus"
after that navigate to your desktop via "cd /home/your user name/Desktop
then right click on the icon in the nautilus window and change the permissions to rw

---

