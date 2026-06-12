---
title: "How to make my furius mounted CD visible to the game?"
date: 2019-08-14
forum: Wine
---

### Post by shag00 on 2019-08-14
Kubuntu 19.04. and wine 4.13

I have an old game installed through wine, one that requires that the CD be mounted, and if it is mounted in the physical CD drive everything works as expected. If I create an ISO image from the CD and mount it using Furius the game cannot find the image. I have attempted to change the PATH in Windows with regedit without success (this may be a wine issue) without success. I use a virtual drive in Windows with an ISO image so I know that there is no problem with the ISO file itself.

I assume there is some setting somewhere which will make it visible, does anyone know what it is?

---

### Post by howefield on 2019-08-14
Thread moved to the "*Wine*" forum, probably a better fit.

---

### Post by 5c0rch3r75 on 2019-10-21
Hmmm,furious iso mount never was a friendly program when i installed it.
Lets change the board,install acetoneISO (this one is a native ISO program),and go to winecfg.
After that go to drives and assign a drive like D: to the ISO you mounted on the acetone,so the system recognises it as a mounted cd rom or drive.
That should do the trick,please post the results of the operation.
That could work with the furious but i dont trust it...

---

### Post by shag00 on 2019-10-21
Tested both Furius and Acetone, same result. The program can't find the Cd - please mount. I note that Acetone mounts the image as "1" and not as the image name, possibly the reason?

---

### Post by 5c0rch3r75 on 2019-10-22
Then its the game cd key check which fails to detect the cd,no matters how you workaround it.
Normally old games comes without DRM which makes this strange.Did you download it through GOG.com or some site like it?
Sometimes winehq.com recommends to get a no cd crack to remove the old security protocols which dont work on anyomre as intended,but this only must be used on legally bought games.
[URL="https://wiki.winehq.org/Copy_Protection"]
https://wiki.winehq.org/Copy_Protection[/URL]

"Piracy is not an option..."

---

