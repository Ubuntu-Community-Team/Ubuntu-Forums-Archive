---
title: "USb and automount no-go anymore"
date: 2005-12-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by jon_gunnar on 2005-12-08
My Breezy system have been running very nice since the install.
I have the backport enabled and I believe that my latest kernel upgrade came from there.

Version 2.6.12-10-amd64-generic.
After this there is no autostart of cd, no mounting of the usb flash, no phone mounting, nothing.

Is it really possible that it is the kernel upgrade that caused this? I cant see any other explanation.
And is there anything I can do to get it back at the right track.

---

### Post by Sutekh on 2005-12-08
Assuming everything is still in order, fstab, and from what you've said, it sounds very much like an issue that has been solved in another thread, I'll quote the steps that solved this issue for me.

[QUOTE=paddyg]the bug fix has been available for some time now.

you've got to enable---for once (then comment the line)--- the following dapper repository in /etc/apt/sources.list

Code:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted


then just use synaptic to download and install

pmount 0.9.6-1[/QUOTE]

Make sure you remove/comment the dapper line once your done.

---

### Post by jon_gunnar on 2005-12-09
[QUOTE=Sutekh]Assuming everything is still in order, fstab, and from what you've said, it sounds very much like an issue that has been solved in another thread, I'll quote the steps that solved this issue for me.



Make sure you remove/comment the dapper line once your done.[/QUOTE]

Thanks a lot for the suggestion. Everything seems like it is in order i fstab. Installed pmount as suggested, but no difference so far. It seems like the whole usb subsystem is dead.
Thanks a lot anyway. Will try to look more at this later.

--EDIT--
Found a solution with the help of a tip at the mailing list.
Re-installed gnome-volume-manager. hal and rebuildt pmount and installed that. And everything worked again.

---

