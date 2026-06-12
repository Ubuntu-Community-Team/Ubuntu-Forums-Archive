---
title: "wine installer problem"
date: 2011-11-27
forum: Wine
---

### Post by *^kyfds( on 2011-11-27
hi. 

i just tried to install a program called 'speccy' on my computer (to find my system specs), using wine (as it was an .exe installer), and it installed to c:/program files (an unchangable location).

once the installation was finished, i selected 'run speccy', and shorty after, i got an error saying something like "wine has experienced a serious error with 'speccy' and has had to close"

i wanted to run speccy again, but i cannot find the location of the install (as the program files folder does not exist)

please help!!  :(

---

### Post by gordintoronto on 2011-11-27
C: is a figment of Wine's imagination, and is best accessed inside Wine.

If you edit the preferences within the file manager to show hidden files and folders, you might be able to browse to /home/(username)/.wine/dosdevices/c:

If you want an exhaustive list of your system specs, open Terminal and enter these commands:
sudo lshw > myconfig.txt
gedit myconfig.txt

I have never seen a Windows program which showed half as much detail.

---

