---
title: "installed wine, got nothing."
date: 2017-05-29
forum: Wine
---

### Post by selittl on 2017-05-29
Im using Ubuntu Budgie 17.04. added the new ppa for wine and installed stable version via CLI. installation seemed to progress fine but no .wine folder was created and I cannot access wine anywhere. rebooted. still nothing. windows installers do not associate with wine when right clicked. when i try to start via command line bash tells me that wine needs to be installed. should I remove and reinstall? try installing from the software store? any ideas?

---

### Post by kc1di on 2017-05-29
I would remove the PPA and install wine form the Ubuntu repositories. Software store will work or you can use the terminal. 
```
sudo apt-get install wine
```
If you need a newer version of wine than is available in the regular channels.  Then install playonlinux ```
sudo apt-get install playonlinux
```
 it's a front end for wine and allows using up to version 2.8 of wine at the moment.  It also has the advantage of installing each program in it's own little Virtual folder and you can use different version of wine for each app depending upon which one works best for that particular app. It will be found in the games section. Good Luck.

Hope this helps.

---

### Post by selittl on 2017-05-29
I removed it and reinstalled using: apt install winehq-stable
seems to be working now. will try playonlinux.

thanks

---

### Post by kc1di on 2017-05-29
Glad it's working for you :)

---

