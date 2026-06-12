---
title: "can't permanetly change screen resolution"
date: 2007-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by demonbro on 2007-08-23
hi everyone, i have ubuntu 7.04 installed, but the default screen resolution has everything big , and clumbsy looking, so i used automtix to install the 64 bit nvidia drivers, it then will allow me to go in the nvidia settings and change the screen reolution to what i want, which i can do, and it looks much better, i then click save to xconfig file, which saves the changes, but when i reboot its back to the clumbsy default resolution! What the hell, I also have the restricted drivers enabled,  I do i have it permantely save the changes?  ANy thoughts, figured this has to do w/ the drivers


thanks
erik

---

### Post by Butthead on 2007-08-23
Well, you have to have "root" privlidges (or how ever that word is spelled? :confused: ) enabled for any changes to be saved, so (if I remember how I did it?), hit Alt. + F2 key (to bring up the run dialog box), then type in "gksudo /usr/bin/nvidia-settings" into the text box.  After hitting the "OK" key (I think it was?), you will be presented with another box that you have to type your root password into again (and maybe a bunch of screen artifacts (ignore them)).  Then make your screen resolution changes in nvidia-settings and click the "save to X configuration file" key to save your changes.

Now if you restart X windows (Alt. + Ctrl. + Backspace key, I think?) your newly saved screen resolution changes should come up.

---

### Post by demonbro on 2007-08-23
thanks, i did what u said, but it still didnt change it, but then i was able to go to screen reolution screen under system and numerous diferent reolution were listed than before, picked 1 and it worked,  Thanks
erik

---

### Post by Butthead on 2007-08-24
Glad you got it working. :guitar:

---

### Post by Ruazinn on 2007-08-25
Hmmmm... This fix worked for me, but I have a couple of unusual side effects.  On the top panel strip, the volume icon is now where the shutdown icon used to be.  On the bottom strip, the trash icon is 1/3 the way from the left, and the little alternate desktop icons are in the lower left corner.  

See the attached captures:

There's probably some simple way to change the structure of these panels, but I wonder why this only happened when I saved the configuration?  Other times when I temporarily changed the resolution, everything was fine.

---

### Post by Ruazinn on 2007-08-25
I fixed the screwed up panels by right-clicking the items that were out of place and selecting "remove from panel".  Then I just added them back where they were supposed to be.  Still weird that it happened though..

---

### Post by Sockerdrickan on 2007-08-25
You could have changed their position too

---

### Post by saru411 on 2007-08-25
the correct way to fix this issue is to enter "sudo nvidia-settings" in terminal and then configure the resolution you want. then apply. then save to xconfig. then restart x by holding cntrl, alt and pressing backspace

---

### Post by Sockerdrickan on 2007-08-25
We know

---

