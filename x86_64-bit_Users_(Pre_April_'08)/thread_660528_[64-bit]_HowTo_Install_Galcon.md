---
title: "[64-bit] HowTo Install Galcon"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cappy on 2008-01-06
Galcon is an awesome high-paced multi-player galactic action-strategy game. The demo includes online play and a single player AI to play against.
Available from [http://www.imitationpickles.org/galcon/index.html](http://www.imitationpickles.org/galcon/index.html)

[IMG]http://www.imitationpickles.org/galcon/content/36.png[/IMG]

Extract Galcon
Install getlibs from here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
Run
```
sudo apt-get install lib32stdc++6 libc6-i386 lib32gcc1; sudo getlibs -p python2.4 libsdl-image1.2
```
Change to the directory where you extracted Galcon and run
```
./galcon
```
to play.

---

