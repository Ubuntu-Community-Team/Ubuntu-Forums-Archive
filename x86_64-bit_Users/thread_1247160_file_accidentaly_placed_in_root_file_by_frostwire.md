---
title: "file accidentaly placed in root file by frostwire"
date: 2009-08-22
forum: x86 64-bit Users
---

### Post by jojom271 on 2009-08-22
i have some music files that were placed in root folder byfrostwire and now i am unable to access them.
how do i change them to my home file. i have tried going thru my file system but it wont let me. i have tried going to it by changing my user to root and it wont let me.

also i am thnking of loading vista or xp as a secondary how much space should i make for a partition

my comp is a  toshiba sat m305 s 49052   32/64bit 4gib  susing ubuntu64 9.04

---

### Post by JOHNNYG713 on 2009-08-22
Hi open a terminal and type "   sudo nautilus "     and navigate to your files copy and past them to where you want them, That terminal command gives you root permisions, Use it wisely! after you have put files away, You my delete the root copies of those files.

---

### Post by jojom271 on 2009-08-22
it is telling me 
jojom271@jojom271-laptop:~$ sudo nautilus
[sudo] password for jojom271: 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:4819): WARNING **: Unable to add monitor: Operation not supported

it did pop up the folder where the music is i tried dragging it to the folder i wanted and it says i dnt have permission.

---

### Post by jojom271 on 2009-08-22
jojom271@jojom271-laptop:~$ sudo nautilus
[sudo] password for jojom271: 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:4819): WARNING **: Unable to add monitor: Operation not supported
Init nautilus burn plugin
Init pidgin plugin
Init removable-devices plugin
Init gajim plugin
Init evolution plugin

(nautilus:4819): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs

/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha

** (totem:5093): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

--- Hash table keys for warning below:
--> file:///root/Desktop
--> file:///
--> file:///root/FrostWire
--> file:///root/NewFolder
--> file:///root/FrostWire/Saved
--> file:///root
--> file:///root/FrostWire/Shared

(nautilus:4819): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 7 elements at quit time (keys above)

(nautilus:4819): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 7 elements at quit time
jojom271@jojom271-laptop:~$ ///root/frostwire
bash: ///root/frostwire: Permission denied

---

### Post by JOHNNYG713 on 2009-08-22
Try " sudo su"  then in root try  "nautilus"  Or  'sudo natilus '  the command "su" puts you in administrative or absolute root, be very careful !

---

### Post by jojom271 on 2009-08-22
it still will not let me 

root@jojom271-laptop:/home/jojom271# sudo nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6884): WARNING **: Unable to add monitor: Operation not supported
what is error 255

---

### Post by JOHNNYG713 on 2009-08-22
Go to this link and see if it helps you seem to have a samba shares issue .
[http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by Yellow Pasque on 2009-08-23
Use gksudo (not sudo) for graphical applications.

> what is error 255
If you're not using Samba shares, then don't worry about it.

Also, the bigger issue here is how frostwire got permission to write to a root directory in the first place. Are you running it with root permissions?

---

