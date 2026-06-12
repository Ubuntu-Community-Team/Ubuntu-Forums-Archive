---
title: "Volume Name has Changed...?"
date: 2008-10-28
forum: x86 64-bit Users
---

### Post by wetling on 2008-10-28
I have a HDD with multiple volumes.  One volume has Ubuntu, one has WindowsXP, and one is used for sharing files between the operating systems.

I haven't used XP recently.  

A few days ago, I booted into Ubuntu 8.04 and opened /media/.  Normally, I see Data (the label for the volume for shared files) but on this day, I saw Data and Data_.  I clicked on Data and there was nothing in it.  I clicked on Data_ and saw the normal volume contents.

I didn't have time to dig into the issue at that time so I did my work and shut down.  The next day, I logged in and opened /media/Data_ and saw two copies of everything.

Though I haven't used XP recently, I thought that maybe when it was shut down, it didn't do so properly which could maybe cause this issue (?) so I loaded up XP and then shut it down but Data_ still exists.

Two additional pieces of information:
1. This happened a few days ago so I don't remember if I loaded XP before or after I saw two copies of the contents of Data_
2. I cannot move any of the files from Data_ to Data.  If I right-click a file and selected copy, when I right click in Data, the paste option is grey.

What gives?  Thanks.

---

### Post by wetling on 2008-10-28
So...I guess Ubuntu created an auto-mount for this volume.  Could the problem be that Ubuntu is trying to mount the same volume twice (thus the "_").  If you think that's plausible, how can I clear that up?

---

### Post by wetling on 2008-12-16
I'm still not quite sure why, but it looks like this happened when I added a few lines to /etc/fstab.

I have a NAS with some shares I'd like to mount automatically when I log in and that seemed like the best way.  A UNIX admin I work with says that's no good though, because if the NAS is unavailable at login (or boot?), Ubuntu won't login (or boot?).

It probably warrant's its own thread, but if anyone can suggest a better way for me to map several CIFS shares at login, I'd like to know.

Thanks.

---

