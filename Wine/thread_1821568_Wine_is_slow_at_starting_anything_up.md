---
title: "Wine is slow at starting anything up"
date: 2011-08-09
forum: Wine
---

### Post by Kairyuka on 2011-08-09
Hi there, I have a strange problem with Wine. It has worked properly for me since I got Kubuntu, but suddenly it is slow at starting anything up, if at all it starts the program. As an example I tried to start up Winetricks, which took about ten minutes. I ran it in Konsole with the simple command "winetricks" which, as I said, after ten minutes caused this message:" > err:process:__wine_kernel_init boot event wait timed out" and then booted Winetricks. Some games and programs that seem to work for others don't work for me, not even after waiting; my example here is the game Recettear, which seems to work for most people in Wine, but it won't boot for me.
I use Kubuntu Natty 11.04 and I use Wine1.2-gecko.
Could any of you help me?

EDIT: Another thing I can see is, that if I run a program in Wine in a konsole, I have a marginally higher chance of actually getting the program to run. I wonder why

---

### Post by disabledaccount on 2011-08-09
Usually such low system performance is caused by problems with harddisk - so I would suggest You to check logs for scsi/md problems and to check SMART reports (if any of "Raw Data" values is not perfect then it should be investigated)

---

