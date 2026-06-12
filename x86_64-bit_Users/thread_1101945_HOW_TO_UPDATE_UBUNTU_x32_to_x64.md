---
title: "HOW TO UPDATE UBUNTU x32 to x64"
date: 2009-03-20
forum: x86 64-bit Users
---

### Post by Art3mis on 2009-03-20
Hi, everyone,.

Because i ordered my Ubuntu disk, i got the x32 bit release. Can anyone pls tell me how to update to an x64 bit version, because i want to use all my ram

---

### Post by Yellow Pasque on 2009-03-21
You can't "update". You have to reinstall with a 64-bit CD/image.

---

### Post by 3Miro on 2009-03-21
> **Temüjin said:**
> You can't "update". You have to reinstall with a 64-bit CD/image.

Correct. You need to back up all your files (especially the important personal ones that you might have), then download the 64-bit CD from the Ubuntu web-page and make a clean install.

---

### Post by dcstar on 2009-03-22
> **Art3mis said:**
> Hi, everyone,.

Because i ordered my Ubuntu disk, i got the x32 bit release. Can anyone pls tell me how to update to an x64 bit version, because i want to use all my ram

Download the 64-bit version from the Ubuntu web site, search out the instructions for creating a separate /home partition and do that (to preserve all of your user data) and then install using the 64-bit image you have now burnt to CD.

Because all of your user data is in a separate /home any fresh install will leave that as it is (including new Ubuntu versions).

---

### Post by Cracauer on 2009-03-22
This isn't quite true.

You can install an alternate userland into a non-standard place. Then boot from a 64 kernel telling it to use an init-like program in that tree, shuffle around enough libs to run a shell and off you go.

---

### Post by SunnyRabbiera on 2009-03-22
Its not really a true "upgrade" or "update" like going from Windows 98 to say 2000, its the same kernel just made for different systems.

---

