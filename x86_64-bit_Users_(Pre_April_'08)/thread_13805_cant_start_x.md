---
title: "cant start x"
date: 2005-02-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by smb2004 on 2005-02-02
yesterday i was trying to apt-get install k3b, was unsucsessful, so install xcdroast.  today when i tried to boot into linux, i cant.  it goes to the gdm screen and when i try to log into gnome, it says that the loginsession lasted less then 10 seconds and all of that.  i can log into the failsafe terminal but thats it.  i've fooled around with linux before, but am still a noobie in need of help.  i've had to boot into windows for the first time in 3 weeks!

---

### Post by AndersAA on 2005-02-02
sudo chown $USER ~/.ICEauthority

try that logged in as user (or alternatly chown <your user name> /home/<your user name>/.ICEauthority as root :) ).

---

### Post by smb2004 on 2005-02-03
sudo chown $user ~/.ICEauthority fixed it.  it's amazing how one line like that can fix it all.  if you dont mind what execatily did i do?  i've used the chown command beofre but dont know what it does,

---

### Post by AndersAA on 2005-02-03
[QUOTE=smb2004]sudo chown $user ~/.ICEauthority fixed it.  it's amazing how one line like that can fix it all.  if you dont mind what execatily did i do?  i've used the chown command beofre but dont know what it does,[/QUOTE]

chown sets who owns the file.
it can be chown user file, or chown user:group file.

And I've seen that bug mentioned when installing/running kde apps, that's why I knew ;)

---

### Post by LongTooth on 2005-02-03
AndersAA, you saved my life! After trying K3B before and having the same problem, I though I'd give it another shot. Got the same problem. Did a search and found your solution: sudo chown $user ~/.ICEauthority.  Worked like a charm. 

I'm using XCDRoast for ISO burning but would like to try something easier. I guess I"ll have to wait until Hoary comes out. I hope it has a CD burning app. Anyone know if it does? Anyway, thanks.

---

### Post by rust on 2005-02-04
I had the exact same symphtoms my self..

I quickly found this little fix but nothing helped med out, after a while i realised I had mounted a SMB share through fstab into my homedir which apparently made root owner of the folder...

Stupid me...but hey, Im still learning!

Well, I removed it and now it works! :)

Just thought I should write it somewhere in the forum since I didnt find anything about this searching for a fix myself...

---

