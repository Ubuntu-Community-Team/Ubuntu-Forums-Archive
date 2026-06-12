---
title: "World of warcraft . FPS problem."
date: 2007-01-12
forum: Wine
---

### Post by k0d0 on 2007-01-12
Hello, i have a problem with running WoW with Cedega in Ubuntu.


My FPS is much worser in Ubuntu compared to Windows XP.

I have tried to change the settings in Cedega a little bit. 
But i dont know how to get best performance.

:) please help

I have an nvidia graphic card. And drivers

---

### Post by pay on 2007-01-12
Don't rely on Cedega to perform aswell as Windows does. But try using opengl mode. That might help.

---

### Post by hikaricore on 2007-01-12
worser...

---

### Post by Ferrat on 2007-01-12
AFAIK wine preforms better with WoW right now than Cedega, might wanna try that?

---

### Post by justin whitaker on 2007-01-12
Did you try the config file and registry fixes here?

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Silentheero on 2007-12-11
Thanks justin. I was looking for help for this problem and that did the trick. 8)

---

### Post by paw158 on 2008-02-27
I hope that this piece of advice helps people who are having fps issues with WoW.  There are just such an abundance of threads all over the internet regarding this. 

I was suffering from 10-15fps screen lag for several weeks after trying all of the tweaks for WoW and Wine.  I FINALLY found the problem this evening.  Here it is:

In HKEY_CURRENT_USER - Software - Wine - Direct3D, I used an incorrect value for the VideoMemorySize item.  I used 512 instead of 256!  At the time, I thought my video card memory was 512MB for some reason when in fact it is 256!  Who would have thought that something so small would be so bad?

This small change increased my fps by 15 in major cities and by 35 outdoors!!  (totalling about 25-30fps inside and about 55-70fps outside) That's huge!

If anyone has ANY idea why something so stupid would have had such a negative impact on my performance, please feel free to enlighten me!  

I hope this little tid bit of information helps someone.

---

### Post by Mushed on 2008-03-28
For me it seems like a strange RAM type problem. If I run some programs before deciding to play WoW, like browse firefox, listen to music etc. and my computer has been on for a while - my fps is terrible like 5 - 10. But if I restart my computer and don't do anything before running WoW I get really good fps 30-40 in cities and 50 -60 outdoors. So maybe is there anyway to clear my RAM without restarting - if that is indeed the culprit. Thanks

---

### Post by jacob01 on 2008-03-30
check your system monitor when you start up and tehn after its been on and end the things that you dont want/need running.

---

