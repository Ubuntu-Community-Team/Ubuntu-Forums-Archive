---
title: "Crash at the last step"
date: 2013-04-04
forum: Wine
---

### Post by ceil210 on 2013-04-04
I am following the instructions at [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu) and everything works until I hit the last step.  When I type *sudo apt-get install wine1.5* I get the following error:

```
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.26-0ubuntu1) but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: fonts-droid but it is not going to be installed
           Recommends: fonts-horai-umefont but it is not going to be installed
           Recommends: fonts-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
           Recommends: winetricks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```


Other than that, everything is okay...

---

