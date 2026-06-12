---
title: "[SOLVED] Copy Installed Wine Program"
date: 2008-11-22
forum: Wine
---

### Post by Sable683 on 2008-11-22
This may sound a little odd, so please bear with me for a minute...

I have a laptop that has Quicken 2006 Basic installed on it through wine. My goal is to copy this whole program from this laptop to a usb drive and copy it to my new Acer Aspire One laptop (this computer has no cd drive). My question is what do I have to copy from one computer to get this program to work in  the other computer? I did not want to experiment with this on my own because I don't know where wine installs other parts of the programs (like the dll files).

Any help is appreciated!

~John

---

### Post by Mze on 2008-11-22
Wine is a hidden folder

Bring up Nautilus and press "CTRL + H" and you should see your hidden folders.

---

### Post by themusicalduck on 2008-11-22
You should be able to just copy the folder containing the program to /home/username/.wine/drive_c/Program Files and it should in theory work without having to do anything else (apart from maybe reset any specific wine settings for the program you made).

Then you can make a custom launcher in the menus or on the panel with the command "wine /path/to/exe/"

---

### Post by Sable683 on 2008-11-22
Okay... I copied the folder for the program from one "Program Files" folder to the other and it did not work. I checked and noticed that I was copying from Wine 1.1.9  to Wine 1.0.1. Since there was not an update for Wine in the update manager... I decided to just copy the whole **.wine** folder... 

And success!!!! Mark This one as SOLVED!!!

Thank you to those who helped!

~John

---

