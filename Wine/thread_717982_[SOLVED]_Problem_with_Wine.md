---
title: "[SOLVED] Problem with Wine"
date: 2008-03-07
forum: Wine
---

### Post by yao_man on 2008-03-07
I installed wine, and installed Warcraft III using wine. It worked fine at first, but then it stopped. I uninstalled wine, but there is still a wine folder on my main menu, but it doesn't contain all of the things it contained before. Now all it has is the programs-games-warcraft III which doesn't work. I tried to reinstall, but after I did, I tried to click browse C;/ drive and it didn't work. It returns the message, "Unable to run the command specified. The file or folder file:///home/username/.wine/drive_c does not exist." I went into my /home/username folder and the /.wine folder does not even exist. I don't know how to fix this, either remove wine completely from the computer or reinstall it successfully, any help would be appreciated.

I am using kubuntu on gutsy 7.10 and wine 0.9.46 if that information makes any difference. Thanks in advance

---

### Post by LoneWolfJack on 2008-03-07
Open synaptic and find the wine package... uninstall it, refresh the package list and then mark wine for installation (personally, I don't trust the auto reinstall thing).

if it still desn't work, things will be a bit more complicated.

---

### Post by yao_man on 2008-03-07
That didn't work for me either. Instead, I downloaded, compiled, and replaced my old version with the newest version of wine manually, and now everything is working ok. Thanks for your help anyway.

---

