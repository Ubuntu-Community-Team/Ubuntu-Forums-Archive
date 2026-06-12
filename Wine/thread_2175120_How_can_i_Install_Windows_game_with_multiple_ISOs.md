---
title: "How can i Install Windows game with multiple ISOs?"
date: 2013-09-17
forum: Wine
---

### Post by protoss96 on 2013-09-17
Hi,

I have two ISO images, game i want to install is Disciples 2: Rise of the Elves(My favorite ^^). Now created two folders in mount folder:

- CD1
- CD2

Now i mount CD1 iso and CD2 iso into that folders with this command:

- sudo mount -o loop ~/Desktop/Folder/ISO1/2 /mnt/CD1/2

Third one, i set up cd drives in winecfg. D drive is /mnt/CD1 and E drive is /mnt/CD2. But i have problem.

When i run setup wizard install everything from CD1 and when it need to take content from CD2 it shows me "Insert CD2". But i already mounted CD2 into /mnt/CD2
and registered that folder into winecfg. I know this is complicated i some way but, can someone help me solve the problem. 

I think that wine somehow doesn't see E drive and /mnt/CD2.

And btw i can use Team Viewer for additional help, thank you!

---

### Post by SamTarling on 2013-09-20
Hey there,

Have you tried unmounting CD1 and mounting CD2 when it asks for the second disk?

You could always burn the ISOs to CDs if possible - that would simplify things quite a bit..

Sorry that's not very useful! :)

---

### Post by protoss96 on 2013-09-21
I burned ISOs to CDs, that worked quite well, thank you.

---

