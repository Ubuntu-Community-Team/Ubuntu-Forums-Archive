---
title: "Strange problem with PlayOnLinux"
date: 2014-01-19
forum: Wine
---

### Post by sean345 on 2014-01-19
Hey guys, I recently installed PlayOnLinux 4.2.2-1, and whenever I try to run it from the icon, the icon simply flashes a bit, then stops. 
Running it in the terminal yields:
[http://i.imgur.com/IElLxHg.jpg](http://i.imgur.com/IElLxHg.jpg)
This entire piece of text repeats infinitely until Ctrl+C is held down for a few seconds, or the Terminal is closed.
Checking my system monitor, I see this:
[http://imgur.com/a/0WDer](http://imgur.com/a/0WDer)
The program says it's taking up 0 CPU power, when in reality it appears to be driving both cores up to 70.0% - 100.0%.
My OS is Ubuntu 12.04, I have Python 2.7.3 installed, and I've used the Synaptic Package Manager to install and update all of PlayOnLinux's dependencies.

I've Google'd this problem a few times, and read over and tried some solutions, but none worked. I will continue doing so, and if I fix it myself, I'll post the solution here.

---

### Post by PotatoHead007 on 2014-02-01
Try updating and re-installing POL using terminal:

To remove:
sudo apt-get remove PlayOnLinux

To re-install and update:
wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -
sudo wget [http://deb.playonlinux.com/playonlinux_maverick.list](http://deb.playonlinux.com/playonlinux_maverick.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

This has always worked for me when i had an error, maybe it will work for you! If not, please tell me :D

---

