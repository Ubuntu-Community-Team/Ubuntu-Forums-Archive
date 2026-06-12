---
title: "A tip for installing all versions of wine"
date: 2015-01-13
forum: Wine
---

### Post by Mike_Walsh on 2015-01-13
To whom it may concern:-

I have found, over the course of installing Wine into several different distros over the last 8 months or so, that installation works FAR more satisfactorily via the terminal, than doing so through the Software Center. 

Through the Software Center, it will sometimes hang, or just not install AT ALL.

Installation via the terminal is almost always 100% trouble-free; and the one time it refused to play ball, I realised the error was my own fault anyway.....for getting my spelling wrong, and incorrectly entering the Wine version number! By NOT making a similar mistake, you SHOULD find installation goes VERY smoothly.

```
sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine 1.x.x
```

where x.x corresponds to your version numbers.


Regards,

Mike.

---

### Post by zombifier25 on 2015-01-13
If I may recommend a more convenient approach: PlayOnLinux (available in the repos) is a GUI front end for Wine that allows you to manage multiple Wine drives to handle multiple applications, and each drive can even have its own Wine version of your own choosing, so no need for manual installation if a certain application will only work with a certain Wine version.

You can learn more here: [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

