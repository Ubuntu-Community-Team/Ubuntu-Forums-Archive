---
title: "[SOLVED] How to Uninstall.."
date: 2008-09-06
forum: Wine
---

### Post by k1ngb0b0 on 2008-09-06
Hello..I recently installed Microsoft .net framework in wine to try to get a game to work (OSU!) 

I still couldn't get the game to work but now all my other games and wine load very slowly.  I'm not quite sure how to uninstall the framework so my wine works like it used to.

To install it, winehq suggested I run this script:

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks corefonts dotnet20

I'm not sure how to install this.  Can someone help me?

---

### Post by k1ngb0b0 on 2008-09-06
No one can help me?  I'm just really new to Ubuntu and wine and not sure how to go about this..

Wine use to load my programs very quickly but now it takes like 30s-1 minute before it will load anything.  Sometimes it throws a error message at me.

I just need to uninstall that .net framework and it should be fine..

---

### Post by k1ngb0b0 on 2008-09-07
Still getting lag when I try to run programs in Wine.

Anyone know what I could try to fix this?

---

### Post by lordadi on 2008-09-07
I think that the easiest way would be to reinstall wine (provided you have ALL original install media for whatever you want to wine). In this case, you could ```
sudo apt-get remove --purge wine
``` which will remove EVERYTHING associated with wine (including conf files) and then ```
sudo apt-get install wine
```will reinstall for you. But the reinstall of the stuff you want to wine will take time. And don't forget to skip .NET 1.1 (or whatever) this time!

If I misunderstood and you WANT to install dotnet20, then you click the link you have provided and copy the text on screen to a new file in your Home directory which you call "winetricks.sh" (no quotes). Then, in a terminal type ```
chmod +x ./winetricks.sh
``` followed by ```
sh ./winetricks
``` and then you select the progs you want to install (corefonts and dotnet20) and hit apply (or something like that).

Cheers,


Lordadi.

---

### Post by k1ngb0b0 on 2008-09-07
I used the commands you suggested but when I went back to my wine directory nothing had changed.  I tried running programs and it was still very slow.

All the config files and programs remained for some reason.

---

### Post by lordadi on 2008-09-07
Did you try the winetricks set of instructions, or the others? If you tried the others and want to remove wine for a reinstall, try going to your home folder in nautilus and try deleting the .wine directory. To see it hit ctrl+H, delete it and when done hit ctrl+H again and close nautilus. After that try reinstalling wine.


Cheers,


Lordadi.

---

### Post by k1ngb0b0 on 2008-09-07
Finally got it.  Thank you very much :)

---

### Post by lordadi on 2008-09-08
No problem. Glad to help.

Please mark as solved.

---

