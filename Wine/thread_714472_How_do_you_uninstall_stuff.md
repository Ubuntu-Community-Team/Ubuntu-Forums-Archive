---
title: "How do you uninstall stuff?"
date: 2008-03-03
forum: Wine
---

### Post by Hernz on 2008-03-03
hello ubuntu forum go'ers.

i recently installed warcraft iii using wine under ubuntu 7.10 gutsy gibbon. problem is, i don't have video card drivers so it's pointless to try playing. was wondering how i go about uninstalling the game? the wine "uninstaller" doesn't give me the option to uninstall (in fact the list is empty). 

please help a linux noob out :). 

i used the search function i swear!!! but i am prepared to be flamed.

thanks and have a nice day. :popcorn:

---

### Post by fedex1993 on 2008-03-03
you could just delete the wine folder that contains warcraft 3 in /home/<username>/.wine/drive_c/program files/<game file> thats one of the easyest ways to do that

---

### Post by jpeddicord on 2008-03-03
> **fedex1993 said:**
> you could just delete the wine folder that contains warcraft 3 in /home/<username>/.wine/drive_c/program files/<game file> thats one of the easyest ways to do that

Also, if you look inside the folder fedex1993 mentioned, you can probably find an uninstall.exe that may do the trick.

---

### Post by christian130 on 2008-03-03
have u tried to look at the registry and find the name of the game erase it. also u have to erase all those directories which have the game or company of the game.jus like the OS

---

### Post by Hernz on 2008-03-04
how do i "look" through these folders? 

so far i have been going to terminal typing in winefile. i deleted the WC3 directory through there (thanks!)... since running uninstall.exe gave me an error. 

can anyone tell me how to reach registry keys? i normall type run the regedit command wen i'm in windows

cheers:guitar:

---

### Post by Roryking on 2008-03-04
Wine has a registry editor comparable to Windows. Just type "wine regedit" and it should get you started.

---

### Post by christian130 on 2008-03-04
tha wine registry could be found in graphic mode. Just right click on 


system>administrator>"Wine RegEdit"

---

### Post by Hernz on 2008-03-04
thank you guys. super helpful

---

### Post by karth on 2008-03-04
> **jacobmp92 said:**
> Also, if you look inside the folder fedex1993 mentioned, you can probably find an uninstall.exe that may do the trick.
wine provides an uninstaller similar to Remove programs in windows
just type 'uninstaller' in a shell prompt and follow the instructions

---

