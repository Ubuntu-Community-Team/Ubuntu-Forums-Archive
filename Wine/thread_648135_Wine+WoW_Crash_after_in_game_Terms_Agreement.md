---
title: "Wine+WoW Crash after in game Terms Agreement"
date: 2007-12-23
forum: Wine
---

### Post by Revengeful on 2007-12-23
Hello there,

I am getting the same some users got some months ago reported her ein this forum (like [http://ubuntuforums.org/showthread.php?t=418093](http://ubuntuforums.org/showthread.php?t=418093)).

Now time are changed and I am using different settings like:

UNIX: Ubuntu 7.10
VGA: ATI x800
Wine: 0.9.5.1 (last version)

I am trying to play wow but the game crashes when I press Agree on a new terms agreement windows before loggin (Termination of Service without Prior Notice). This the windows that appers only when you upgrade with the last patch. Indeed I never got a crash during the Terms Agreement of the previous patches (playing without problem).

Is there any news about how fix that problem?

Thanks, Andrea

---

### Post by tombug on 2007-12-23
one easy thing you can do is go to your wow dirc in C: for wine

/home/<name>/.wine/drive_c/Program Files/World of Warcraft

then go into your WTF folder in there, and edit the Config.wtf file

and add these 2 lines in there or replace the ones that might already be there

SET readTOS "1"
SET readEULA "1"

^add that save the file, and then run wow again it will skip the rules and terms stuff and go right to the login screen

of you dont have the Config.wtf file you can just creat one and add them lines in and the game will pick it up as its own

---

