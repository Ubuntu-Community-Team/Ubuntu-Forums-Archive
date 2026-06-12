---
title: "64bit, but where?"
date: 2007-05-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by midkin on 2007-05-19
where to i change my screen color quality?
I have just installed the 64bit version of ubuntu, plz help!

---

### Post by shad0w_walker on 2007-05-19
Why do you need to change your colour depth?

---

### Post by midkin on 2007-05-19
i just want to see if there is a 64bit choice!
Man its the 1st time in my life i bot an OS with 64bit i want to SEE it!!!

---

### Post by shad0w_walker on 2007-05-19
There is no such thing as 64bit colour depth and even if there was, the human eye wouldnt be able to tell the difference between it and 24bit colour.

The 64bit refers to the CPU not graphics.

---

### Post by midkin on 2007-05-19
ok, where can i set the color quality, just like in windows XP that when u right click on the screen u can press "properties" and then "settings" and change the color quality between 16bit and 32bit.
Where should i go to change the color quality in ubuntu?
thanks in advance..

---

### Post by shad0w_walker on 2007-05-19
There shouldn't be any need to change your colour depth, Ubuntu automatically sets up the highest colour depth your computer can manage during setup.

---

### Post by midkin on 2007-05-19
OMG....i dont really care if there is a need or not of changing it!
My question is simple, do u know where do i change it?

---

### Post by midkin on 2007-05-19
Plz some1 can help me?
Thanks.

---

### Post by midkin on 2007-05-19
Nobody there that can help?:confused::(

---

### Post by insane_alien on 2007-05-19
go edit your Xorg.conf that has the colour depth. if you change anything with the colour depth you'll likely be reducing it which seems a bit silly.

---

### Post by rsambuca on 2007-05-19
Enter this code in a terminal to open a file called xorg.conf.  Inside that file you will see the settings for your display.  To open a terminal, go to Applications -> Accessories -> Terminal.

Once the terminal has opened, enter the following command, keeping in mind that linux directories are case sensitive.```
gedit /etc/X11/xorg.conf
```This will open the xorg.conf file in a text editor called gedit (note:  this will open in Read Only mode - if you want to edit the xorg.conf, add the word gksudo in front of the gedit command from above.  I wouldn't recommend changing anything at this point as it sounds like you are more likely to harm your system than help it at this stage).

---

