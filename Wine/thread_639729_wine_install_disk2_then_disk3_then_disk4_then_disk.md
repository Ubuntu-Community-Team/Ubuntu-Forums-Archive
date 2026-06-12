---
title: "wine install disk2 then disk3 then disk4 then disk5 (which doesn't exist in the game)"
date: 2007-12-13
forum: Wine
---

### Post by ShanghaiTeej on 2007-12-13
I'm using Gutsy and the latest wine from the winehq repos.  I've installed Warcraft III with no problem and run it with opengl, but Baldurs Gate II is giving me some trouble.

I tried to install the game with wine, but when the intsaller got to disk2, I couldn't eject disk1.  So i burned every cd into a ISO image and am using Gisomount to mount all of them.  

So, I tried to install everything again from the mounted iso images.  When I get to disk2, i locate the mounted iso (i mounted these drives on winecfg as well) and then it immediately asks to put in disk3...then when i put that in...disk4 and then disk5 which baldurs gate II does not have.  I'm kind of stuck.  Any help would be awesome.

---

### Post by cogadh on 2007-12-13
Not sure why it is going beyond the right number of disks, but to eject a disk in Wine, you sometimes have to use the "wine eject" command from the terminal. When it gets to the end of the first disk, just open another terminal session and enter "wine eject D:" (or whatever your actual CD drive letter is).

BTW - There is now a Wine subforum for questions like this:
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

