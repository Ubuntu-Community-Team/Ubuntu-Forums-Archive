---
title: "world of warcraft Black screen help"
date: 2008-06-17
forum: Wine
---

### Post by rabidzeus on 2008-06-17
i recenetly as in last night got linux and its great, i hav installed latest wine update, and i have downloaded WoW to play, and it wasnt running right so i installed my Nvidia graphics drivers  i beleive any who, idk if i did it right and activated Nvidia card, and now when i log on to WoW it comes up w/ a black screen but i can hear the music, and a screen pops up saying that theirs an error and would you like to report it to blizzard. i say no... but anyone have an idea how i can fix it.. 


thanks

         -chet

---

### Post by pedro_orange on 2008-06-19
How are you launching WoW? 

Try and launch it from the terminal. So you can see whats going on. 

The command you want will be something like:

wine 'path/to/WoW.exe' -opengl

This will force WoW to use OpenGL instead of DX.

Make sure you refer to the community documentation regarding WoW on Ubuntu it's very thorough.
Just google Warcraft Ubuntu and it will probably be the top page.

---

### Post by paule100 on 2008-08-23
Thanks. Without the  option -opengl WoW did start with black screen and sound.

---

### Post by ooobuntooo on 2008-08-23
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

---

