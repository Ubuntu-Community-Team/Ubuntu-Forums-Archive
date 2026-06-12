---
title: "ATi 1250 Problem with Ubuntu Fiesty Fawn"
date: 2007-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by rajeshgovindan on 2007-06-08
I am havin ATi 1250 Onboard graphics (AMD X2 5600+)

I am unable to install Ubuntu 7.04 

32 Bit Edition shows a blank screen after the Menu select screen
While 64 Bit Edition shows xorg error

Plz. help

Screenshots:

[http://img14.imgspot.com/u/07/158/03/0P1020799.JPG](http://img14.imgspot.com/u/07/158/03/0P1020799.JPG)

[http://img14.imgspot.com/u/07/158/03/0P1020800.JPG](http://img14.imgspot.com/u/07/158/03/0P1020800.JPG)

[http://img14.imgspot.com/u/07/158/03/0P1020801.JPG](http://img14.imgspot.com/u/07/158/03/0P1020801.JPG)

***Rajesh***

---

### Post by renzokuken on 2007-06-08
thats usually a result of ubuntu not using the correct driver.

when that blue/grey error message comes up press Ctrl+Alt+F1 to get to a tty terminal screen. then login. we are now going to manually change the driver. run the code

```
sudo dpkg-reconfigure xserver-xorg
```

this will enter a wizard to edit your xorg.conf. leave everything as it is (default options) until you get to the **drivers** section. select the **"vesa"** and then carry on just leaving the options as they are. exit and reboot and see what happens.

since you have an ATI card, you could also try the **"ati"** driver or the **"radeon"** driver.

good luck

---

### Post by renzokuken on 2007-06-08
ok, so  just read the error in a bit more detail and it appears you are already using VESA and the problem is to do with screens.

try the **ati** and **radeon** drivers first and if they dont work then we will need to see your xorg.conf itself

---

### Post by rajeshgovindan on 2007-06-08
In the 32 it Edition of Feisty Fawn....when I Press Ctrl+Alt+F1.....It says "Loading please wait..."

Only in the 64 Bit Edition I get the error "Xserver Error"....

---

### Post by renzokuken on 2007-06-08
weird, have you tried Ctrl+Alt+F2/3/4/5/6

---

### Post by rajeshgovindan on 2007-06-08
Yes tried them too....but in vain


***Rajesh***

---

### Post by Nikos.Alexandris on 2007-06-18
Check on this thread... 

[http://ubuntuforums.org/showthread.php?t=396751&highlight=ati+1250&page=5](http://ubuntuforums.org/showthread.php?t=396751&highlight=ati+1250&page=5)

Greetings!

---

