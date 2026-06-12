---
title: "EBON with wine"
date: 2007-06-17
forum: Wine
---

### Post by jasonbrisbane on 2007-06-17
Hello All,

Has anyone managed to get EBON (Everchanging Book of Names) working with WINE?

It loads the program but doesnt access (or allow access may be?) to the extra files stored in the same directory. I've been playing with the settings but nothing worked. I even chmod ugo+rw all files...

I tried to update to a later version of Wine but the results were worse!
(I had to downgrade to get back some functionality...)

Anyone know how to get this program working?

Thanks in advance..

Regards,
Jason Brisbane
Perth, WA, Australia

---

### Post by Popoi on 2008-07-26
To run Everlasting Book of Names (EBoN 3.4) under Ubuntu 8.04 Hardy Heron, in a terminal do as follows:

Install Wine:
```
sudo apt-get install wine
```

Let Wine create directory and configuration files:
```
winecfg
```

Dowload EBoN 3.4:
```
wget http://www.kolumbus.fi/sami.pyorre/downloads/ebon34.zip
```

Create directory and extract into it:
```
mkdir ~/.ebon34
unzip ebon34.zip -d ~/.ebon34
```

Now, when you execute EBoN.exe, it has to be from the same directory where the program is, this way it can load the chapters. So you can write a script to run it:
```
gedit 
```

Write and save:
```
#!/bin/bash
 
cd ~/.ebon34
wine EBoN.exe
```

Give it run permission:
```
chmod +x ~/.ebon34/ebon-launcher.sh
```

Make a new menu entry (alacarte), you can use [this image]("http://sky.prohosting.com/kurimus/dv3.gif") as icon. In *command* you must write:
```
sh /home/*USERNAME*/.ebon34/ebon-launcher.sh
```

Replace *USERNAME* with your user name.

---

