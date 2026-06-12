---
title: "How can i change the hard disk size in a dual boot"
date: 2009-03-30
forum: x86 64-bit Users
---

### Post by tito_drum on 2009-03-30
Hi, I installed Ubuntu last year in dual partition (i think), but im not using it too much. The problem is I divided my hard disk in half, 300 Gigs for Vista and 300 Gigs for Ubuntu. I dont want to uninstall Ubuntu but i want to give more space to my Windows Vista wich is the one me and my wife used more. Is there any way to do that?
Thanks,
Alberto

---

### Post by jelle_ on 2009-03-30
yes, there is a way to do that. be careful to backup all important data

first, boot from the ubuntu live-cd and open partition editor from system -> maintenance and decrease the size of the ubuntu partition. now shutdown and start ubuntu from hard-drive

now you need the program ntfsprogs. enter in terminal:
sudo apt-get install ntfsprogs

now you have to restart your computer, because else this program won't work in gparted. now you can increase the size of the windows partition.

increasing the size of windows will take many time, my computer needed three hours to decrease an windows partition from 130 to 100 GB. you could try an partition editor from windows to speed the last step up, but i haven't tried that. in that case you don't need ntfsprogs.

---

