---
title: "wine not recognizing cd when i run my games"
date: 2008-03-05
forum: Wine
---

### Post by littletinman on 2008-03-05
When i try to run games that recuire a cd, (after a succesful install) i get the "insert correct cd, no cd detected" message. It does this for anything that needs to run off a cd. I need to get wine to make these apps find my cd drive and run the cd from it. How do i do this?

---

### Post by deruberhanyok on 2008-03-05
You need to go to wine's configuration panel. If you've installed Wine from the repository then this should be accessible from your applications/wine menu.

On the "Drives" tab you need to add your CD/DVD drive. Pick a letter - D, for example - and set the path to "/media/cdrom/". That SHOULD set it to recognize when a disc is in; this was all I needed to do to get it working for me.

---

### Post by LoneWolfJack on 2008-03-06
Let me add that among the "advanced" settings on the drives tab there is a dropdown that is set to auto detect the drive type per default. I have found that some programs won't find your drive if this is enabled, so you should select "cd drive" there.

---

