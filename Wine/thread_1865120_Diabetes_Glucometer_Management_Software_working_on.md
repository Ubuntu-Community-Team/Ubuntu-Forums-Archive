---
title: "Diabetes Glucometer Management Software working on Wine+Ubuntu 11.04"
date: 2011-10-19
forum: Wine
---

### Post by DM1 on 2011-10-19
Hello to everybody

I was looking for a software allowing me to download blood sugar level data from a glucometer, using Ubuntu 11.04.

So, I started collecting the software provided free of charge by some manufacturers, either online or by traditional mail, and tried to install it in Ubuntu+Wine.

A few companies do actually provide software that installs out-of-the-box in Ubuntu+Wine. I shortlisted these companies and I started contacting them to get their glucometer, so to try the software in practice.

Tonight, I can say that a glucometer called "Glucomen LX PLUS" works on my Ubuntu (11.04) + Wine (1.3.29) with their software ("GlucoLog", available online) and a cable that I got for free by requesting it to the company distributing the glucometer. 

Their software seems to be some kind of server, provided with a java runtime environment. It is bulky but it worked straight out-of-the box.

To have the software detect the glucometer connected with a USB cable, I  used the following commands to tell Wine that a COM port (COM3) was a USB device (/dev/ttyUSB0): 

```
$ cd ~/.wine/dosdevices
$ ln -s /dev/ttyUSB0 com3
```

and then the software could find the glucometer at com3 when trying to import data. :)

Of course I hope that all those who manufacture glucometers will read this post and provide an honorable solution for using both their products and Ubuntu!!! :p

---

### Post by DM1 on 2011-10-24
Alas, after upgrading to Ubuntu (11.10) + Wine (1.3.30), the software stopped working. The GUI never comes up... :mad:

---

