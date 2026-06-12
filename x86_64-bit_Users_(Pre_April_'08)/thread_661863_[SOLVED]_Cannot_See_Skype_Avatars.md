---
title: "[SOLVED] Cannot See Skype Avatars?"
date: 2008-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by CyberAngel on 2008-01-08
Hello!

A problem that I realized on my Skype...
I cannot see the avatars of my contacts!
My contacts can see mine.

Is anyone experiencing this problem with skype on 64bit or it is just me?

---

### Post by wanis on 2008-02-28
Your are not alone :confused: I now use Skype beta 2.0.0.43 and cannot see my or others avatars

---

### Post by CyberAngel on 2008-02-28
of course the problem still exists to me :(

---

### Post by Kimm on 2008-03-15
I have a fix for it. As far as I can tell, its a problem with Qt4.

**You need to download the static version of skype: **
[http://www.skype.com/go/getskype-linux-static](http://www.skype.com/go/getskype-linux-static)

Then move the contents of the folder to somewhere discrete. I recomend /opt/Skype

**Uninstall the installed version of skype:**
sudo dpkg -r skype

**Make a script to launch Skype from the directory it is in:**
sudo gedit /usr/bin/skype

write this in it:

```

#!/bin/bash

cd /opt/Skype
./skype

```

**Then do this in terminal:**
sudo chmod +x /usr/bin/skype

**You need to copy the launcher from the Skype directory to the applications directory, do this in terminal:**
sudo cp /opt/Skype/skype.desktop /usr/share/applications/skype.desktop

open the file like this: 

sudo gedit /usr/share/applications/skype.desktop

and change it from this:

> 
[Desktop Entry]
Name=Skype
Comment=Skype Internet Telephony
Exec=skype
**Icon=skype.png**
Terminal=0
Type=Application
Encoding=UTF-8
Categories=Network;Application;


to this:

> 
[Desktop Entry]
Name=Skype
Comment=Skype Internet Telephony
Exec=skype
**Icon=/opt/Skype/icons/SkypeBlue_48x48.png**
Terminal=0
Type=Application
Encoding=UTF-8
Categories=Network;Application;


And now it should work. It should have a menu item too. If you need to update, just download the static version again and replace the files in /opt/Skype

---

### Post by Kimm on 2008-03-24
Works for anyone else?
The Topic should be marked "[SOLVED]"

---

### Post by CyberAngel on 2008-03-24
> **Kimm said:**
> Works for anyone else?
The Topic should be marked "[SOLVED]"

I will check this soon and report back here! :)
I was on vacations so I haven`t checked it yet!

---

### Post by Ag_Smith on 2008-07-01
It work for me!! very good!!

---

