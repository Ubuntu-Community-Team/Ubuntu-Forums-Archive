---
title: "Diablo 2 expansion disk not found"
date: 2006-07-23
forum: Wine
---

### Post by daniel of sarnia on 2006-07-23
Hi all, I'm trying to install diablo 2 LOD, and I got as far as getting diablo 2 installed ok.
    When I try to install the expansion the disk mounts fine but when I run the install.exe a window comes up saying "please insert the diablo ii cd labelled 'expansion disc.'" and the disk is in fact in the drive and mounted.

Help pleas. I'm using wine 0.9.17 and kubuntu 6.06.

---

### Post by Ziox on 2006-07-23
don't know if this would help, but it's worth a try.  

do winecfg, and under the drives tab, create a new drive and link it straight to your cdrom folder...should be something like /media/cdrom0

---

### Post by daniel of sarnia on 2006-07-24
I'll try that.

---

### Post by daniel of sarnia on 2006-07-24
It worked, thanks so muck. I did winecfg; hit the drives tab and all I had to do was hit the auto detect button and it linked to /media/cdrom0 and all my other drives to.

Thanks again but I still wonder why it only did that with the expansion install. Oh well.

---

### Post by Ted_Kazynski on 2010-12-19
I have a similar problem. I have installed D2 but can't play it with the "play disc"  ISO mounted. so I figured I'd install the expansion and then the no CD patch would fix it. so D2 installed fine and the LOD installs all the way up to the end and it states to insert the expansion disc. but it's already mounted. I am using a netbook so im not using my OG copies.... Im using Gmount ISO and  tried to unmount it and remount but it just blinks to insert the disc.....
then I config Wine to the directory that I had the ISO mounted to (does the ISO have to mounted somewhere besides a desktop folder?).....but nothing changes. I'm pretty useless in the terminal but tried the "wine eject" but it just says couldn't find drive. Ive tried everything I could find in the forums but nothing has worked yet.


So whats wrong?
Why does wine install everything fine but then cant recognise the change out the cd's?

sorry for the small novel.

---

### Post by Perfect Storm on 2010-12-19
Necromancing. Thread Closed.

---

