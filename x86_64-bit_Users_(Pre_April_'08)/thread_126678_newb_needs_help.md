---
title: "newb needs help"
date: 2006-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Laxflip on 2006-02-07
ok i know this has been posted and asked over and over but i searched through and read and tried it on my own but i have no clue now....

my computer is a "generic" amd 64 and i have an ATI 800xt card. I read around and tried the fglrx (i think) driver thats included in the breezy badger install and now i get a module load failure when i try to start xserver i tried to switch back to the vesa drivers and nothing i get the same error.
So my question in short is how can i get my install to work again and hwo can i finally install the ati drivers???

also i have a soundblaster platinum sound card but the install continues to use my onboard is there a way i can change this?

---

### Post by Teroedni on 2006-02-07
Ucomment(#) the following(demo)

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        #Load    "dri"
        Load    "extmod"
        Load    "freetype"
       # Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

when you done that 
Install the fglrx driver according to this site
[http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

As for the sound
Brezzy probably have installed both .
Its loading the onboard as first and your pci as second
You have to make a asoundrc file to change it or you can just tell the program your using which soundcard to load.

---

### Post by Laxflip on 2006-02-07
man im a total nub i have no clue hwo to do any of what you just said... :( please help

---

### Post by jon_gunnar on 2006-02-08
[QUOTE=Laxflip]ok i know this has been posted and asked over and over but i searched through and read and tried it on my own but i have no clue now....

my computer is a "generic" amd 64 and i have an ATI 800xt card. I read around and tried the fglrx (i think) driver thats included in the breezy badger install and now i get a module load failure when i try to start xserver i tried to switch back to the vesa drivers and nothing i get the same error.
So my question in short is how can i get my install to work again and hwo can i finally install the ati drivers???

also i have a soundblaster platinum sound card but the install continues to use my onboard is there a way i can change this?[/QUOTE]

Have you looked at this too:
[http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378)
[http://www.ubuntuforums.org/showthread.php?t=75382](http://www.ubuntuforums.org/showthread.php?t=75382)

---

