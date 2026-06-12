---
title: "wine uninstaller won't remove window program"
date: 2017-01-12
forum: Wine
---

### Post by newblank25 on 2017-01-12
i downloaded dvd video soft free studio &free Youtube to dvd converter using wine & i now wish to uninstall them. wine uninstaller won't do it. What other way is there to remove a window program? thx

I tried going to terminal & used this.
```
sudo apt-get --purge remove DVDVideoSoftFreeStudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package DVDVideoSoftFreeStudio
```
When I search my computer I see the Icon but nothing is there

---

### Post by howefield on 2017-01-13
Wine uninstaller is the way to do it, but if that isn't listing the software then you could delete the relevant folders in 

```
home/$USER/.wine
```

---

