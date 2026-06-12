---
title: "How to downgrade to 1.7.24"
date: 2014-10-01
forum: Wine
---

### Post by harry29 on 2014-10-01
Could someone tell me how to downgrade to 1.7.24? All the instructions i can find dont seem to work for me !

---

### Post by harry29 on 2014-10-01
I tried install the .deb packages but it fails did to unmet dependencies ... So I run install -f and it removes whatever was installed by the .deb package ... 

I compiled and installed it manually but the system would recognize the install ! 

I used synaptic and although I could get it to show the older version was installed if I did wine --version it would show 1.7.26 or 1.7.27 .... When I was trying to downgrade to 1.7.24!

I have not been able to find any directions that would work ! I see constant references to "it's easy" lol so what am I missing ?

---

### Post by harry29 on 2014-10-02
Ok so through tremendous trial and error It seems i have figured out how to downgrade. This worked for me on 14.04-1 64 bit system
 If you can improve on this please do so...

1) remove the wine/ppa from your sources
- under the other sources tab deselect the wine/ppa lines
```
software-properties-gtk
```

2) go here [http://wine.budgetdedicated.com/archive/binary/](http://wine.budgetdedicated.com/archive/binary/) and download 6 files and put them in a folder together
Notice you will have 4 amd64 files of different sizes 1.1, 2.3, 17, 48 and 2 i386 files 1.1, 17

[http://wine.budgetdedicated.com/archive/binary/wine1.7-amd64_1.7.24-0ubuntu1~ppa1_amd64.deb](http://wine.budgetdedicated.com/archive/binary/wine1.7-amd64_1.7.24-0ubuntu1~ppa1_amd64.deb)  17M
[http://wine.budgetdedicated.com/archive/binary/wine1.7-dbg_1.7.24-0ubuntu1~ppa1_amd64.deb](http://wine.budgetdedicated.com/archive/binary/wine1.7-dbg_1.7.24-0ubuntu1~ppa1_amd64.deb)  48M
[http://wine.budgetdedicated.com/archive/binary/wine1.7-dev_1.7.24-0ubuntu1~ppa1_amd64.deb](http://wine.budgetdedicated.com/archive/binary/wine1.7-dev_1.7.24-0ubuntu1~ppa1_amd64.deb)  2.3M 
[http://wine.budgetdedicated.com/archive/binary/wine1.7-i386_1.7.24-0ubuntu1~ppa1_i386.deb](http://wine.budgetdedicated.com/archive/binary/wine1.7-i386_1.7.24-0ubuntu1~ppa1_i386.deb)  17M 
[http://wine.budgetdedicated.com/archive/binary/wine1.7_1.7.24-0ubuntu1~ppa1_amd64.deb](http://wine.budgetdedicated.com/archive/binary/wine1.7_1.7.24-0ubuntu1~ppa1_amd64.deb)  1.1M
[http://wine.budgetdedicated.com/archive/binary/wine1.7_1.7.24-0ubuntu1~ppa1_i386.deb](http://wine.budgetdedicated.com/archive/binary/wine1.7_1.7.24-0ubuntu1~ppa1_i386.deb)   1.1M 

3)Now you need to run each one in terminal with...
in this format sudo dpkg -i packagename.deb
```
sudo dpkg -i 
``` drag each file into terminal and hit enter

4) Run this comman in terminal... it should fix any dependancy problems
```
sudo apt-get -f install
```

5) Type this into terminal and you should see version 1.7.24
```
wine --version
```

---

### Post by adec2 on 2014-10-04
May i suggest you use playonlinux so you can keep the wine version associated with your program without this hassle again?

---

