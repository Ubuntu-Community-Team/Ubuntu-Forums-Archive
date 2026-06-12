---
title: "Screen Resolution Problem"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by mmoscosa on 2007-06-03
Hello, I  have just installed Ubuntu and am quite happy with it, only one or two problems, but so far the most annoying problem is that I have a low screen resolution, first I thought it would be because my Xorg.conf but the file says that I can run 1440x900

I have a 7950GT-KO Nvidia card and a 19" Widescreen AOC Monitor, so I am completely sure I can use those displeays.

but I cant set it up. any idea?

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Solved, just had to re-install the nvidia Driver and re-edit the xorg.conf

---

### Post by wikiguy on 2007-06-03
Sure man i had the same thing a copule of weeks ago , so you must install the nvidia driver , im guessing that your system is X64 so , download this 


[http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/NVIDIA-Linux-x86_64-1.0-9755-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/NVIDIA-Linux-x86_64-1.0-9755-pkg2.run)



after downloading the package in terminal type:

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

then

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common

finally you must type this command

sudo rm /etc/init.d/nvidia-*


after finishing all these stuff press   CTRL +  ALT + F1   log in , and type this simple command

sudo /etc/init.d/gdm stop

it should display.............................OK :D

then you downloaded your file to Desktop so:

(NOTE :JUST TYPE THIS AND PRESS TAB IT SHOULD COMPLETE THE INSTRUCTION:p) 

sudo sh Nvi

THEN ALL FROM HERE IS JUST , NEXT , NEXT :lolflag:

OK, THEN FINALLY TYPE THIS 

sudo /etc/init.d/gdm start

Now you have nvidia drivers runnin, plus ·d acceleration enabled plus  good resolution and u get rid of that horrible choppy windows


GREETINGS;)

---

### Post by Sockerdrickan on 2007-06-03
Really good how2.

---

### Post by wikiguy on 2007-06-06
thxs :p , try it and if you dont know something , ask it inmmediatly :lolflag::guitar:.


CHEERS;)

---

### Post by Sockerdrickan on 2007-06-07
:popcorn:

---

### Post by YaAqoB on 2007-06-25
wikiguy you are a legend. I have been trying for weeks to get the NVidia drivers running and 1440x900 running. I have tried every howto guide in here. Your one worked!!!!! LEGEND.

---

