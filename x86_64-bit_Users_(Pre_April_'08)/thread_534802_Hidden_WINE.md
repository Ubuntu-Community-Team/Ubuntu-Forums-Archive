---
title: "Hidden WINE"
date: 2007-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by groeswenphil on 2007-08-25
Hi,
I appear to have downloaded and installed WINE.........using cd ~/Desktop 
sudo dpkg --force-architecture -i wine_*_i386.deb
to get it to work on AMD64

Now, If I look at ADD/REMOVE, then WINE is listed there, but it doesn't appear on my Applications list.

What should I do next?
Phil

---

### Post by RavanH on 2007-08-25
> **groeswenphil said:**
> Hi,
I appear to have downloaded and installed WINE.........using cd ~/Desktop 
sudo dpkg --force-architecture -i wine_*_i386.deb
to get it to work on AMD64

Now, If I look at ADD/REMOVE, then WINE is listed there, but it doesn't appear on my Applications list.

What should I do next?
Phil

What if you right-click a windows .exe file? Does "Wine Windows Emulator" not show as an option in the 'Open with...' list?

---

### Post by Kilz on 2007-08-25
> **groeswenphil said:**
> Hi,
I appear to have downloaded and installed WINE.........using cd ~/Desktop 
sudo dpkg --force-architecture -i wine_*_i386.deb
to get it to work on AMD64

Now, If I look at ADD/REMOVE, then WINE is listed there, but it doesn't appear on my Applications list.

What should I do next?
Phil

Wine isnt an application on the in a list, its an application layer. It helps run windows applications. You can call up its configuration pannel with ```
winecfg
```, but its not useful to you in actually running the applications, it just configures wine.  
If when you click on an exe nothing happens, right click on it and choose Open with Other Application, the application list will pop up, at the bottom click on Use a custom command, type in wine in the box that opens.
Another thing you may not know is that wine isnt perfect. There is no guarantee that the application will run, or that it will be easy to get working. A trip to the [Wine application Database ]("http://appdb.winehq.org/")is your best resource for instructions on running or setting up most applications.

---

### Post by mckryptyk on 2007-08-25
It isn't required to do things this way as wine has repos available for i386 and amd64.

Follow this link to winehq with instuctions:

i386 (also this is for amd64 if using feisty or newer such as gutsy-development)

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

amd64 (only use this one if your running older than feisty fawn)

[http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64)

Then its just a "sudo apt-get update" && "sudo apt-get install wine"

Be sure to type winecfg into terminal after install

Cheers.

---

