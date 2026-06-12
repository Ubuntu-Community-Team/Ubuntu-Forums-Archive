---
title: "Android SDK problem solved in ubuntu 9.10 AMD64"
date: 2009-11-06
forum: x86 64-bit Users
---

### Post by yashpatel on 2009-11-06
Failed to get the adb version: Cannot run program "/home/yash/devtools/android/android-sdk-linux_x86-1.6_r1/tools/adb": java.io.IOException: error=2, No such file or directory

steps:

1. install getlibs from [http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb)
2. open terminal and go to your android folder and then platforms/android-1.6/tools 
3. run this command from terminal 
           getlibs aapt
4. you will see this 

yash@yash-Notebook:/media/STUDY/android-sdk-linux_x86-1.6_r1/platforms/android-1.6/tools$ getlibs aapt
[sudo] password for yash: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32v4l-0
  lib32z1 libc6-i386
Suggested packages:
  lib32asound2-plugins
The following NEW packages will be installed:
  ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6
  lib32v4l-0 lib32z1 libc6-i386

6. go to eclipse and refresh and clean the project.

This should work for you :)

---

### Post by here.david on 2009-11-08
> **yashpatel said:**
> Failed to get the adb version: Cannot run program "/home/yash/devtools/android/android-sdk-linux_x86-1.6_r1/tools/adb": java.io.IOException: error=2, No such file or directory

steps:

1. install getlibs from [http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb)
2. open terminal and go to your android folder and then platforms/android-1.6/tools 
3. run this command from terminal 
           getlibs aapt
4. you will see this 

yash@yash-Notebook:/media/STUDY/android-sdk-linux_x86-1.6_r1/platforms/android-1.6/tools$ getlibs aapt
[sudo] password for yash: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32v4l-0
  lib32z1 libc6-i386
Suggested packages:
  lib32asound2-plugins
The following NEW packages will be installed:
  ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6
  lib32v4l-0 lib32z1 libc6-i386

6. go to eclipse and refresh and clean the project.

This should work for you :)

THANK YOU! So easy when you have friendly help...was worried I had to go back to 9.04...ADB working like it should...:lolflag:

---

