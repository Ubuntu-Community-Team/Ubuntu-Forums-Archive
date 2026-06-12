---
title: "amarok wont play"
date: 2005-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by luckyaba on 2005-10-12
When i play an mp3 in amarok it skips the song as if it was only a second long track. i tried it with the engines i got but some dont work... is it an engine problem or something else?

---

### Post by adwait on 2005-10-12
I had that problem with juk, and it was an engine problem. Try using other engines, if they don't work. Try installing the arts engine......that should work since that's the default KDE engine.

---

### Post by catskin on 2005-10-12
What other engines are there? I'm also not having any success with mp3 and other mpeg files.

---

### Post by luckyaba on 2005-10-12
I have arts and i just switched to it and it still skips right through the songs..... baahhhh this is frustrating.. i love amarok and hate it at the same time

---

### Post by adwait on 2005-10-12
Have you installed the gstreamer engine?

---

### Post by luckyaba on 2005-10-12
yes and also xine but none seem to work?

---

### Post by luckyaba on 2005-10-12
I fixed it. there is a missing package that wasn't installed.


gstreamer0.8-plugins

after installing that not only did my amarok sound start playing but my movies had sound as well.

---

