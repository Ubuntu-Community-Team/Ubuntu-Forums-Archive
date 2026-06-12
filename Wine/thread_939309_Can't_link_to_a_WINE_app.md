---
title: "Can't link to a WINE app"
date: 2008-10-05
forum: Wine
---

### Post by Xonara on 2008-10-05
I've been trying to link to a windows executable for a while but I haven't had much success. I've tried many different things but I usually get some sort of permissions error or an error saying that the program failed to execute. The only thing that worked is dragging the app to the top panel, but I'd really rather not put every single windows program in an unorganized mess up there. I want to have an entry in the main bar but I keep getting errors when I launch it from the main bar.

I'm really confused and I think the only thing that'll help me is explicit instructions because I've tried setting the launcher to open it normally, setting the launcher to open it in the terminal, making the main menu item EXACTLY like the launcher on the panel, toggling "execute file as program" on the app on and off, making a shell script that launches the file via sudo and then linking to THAT... All in all I'm pretty frustrated, I don't even remember most of the results of my different attempts X_X

Three smiley faces holding popcorn are going to whoever can help me out on this.
:popcorn::popcorn::popcorn:

---

### Post by Xonara on 2008-10-06
bump

---

### Post by alynx on 2008-10-06
Hello mate , hope this will solve your problem if i got this right.

right click your main bar and press panel menu. Add a program to the panel then add a non KDE program to the panel.

Then you will get an image like this 

[http://img184.imageshack.us/my.php?image=skjermbilde3vv0.png](http://img184.imageshack.us/my.php?image=skjermbilde3vv0.png)

Browse to your windows application and then on the command line argument write wine 

Sorry for the norwegian on the pic , but hopefully this would work out for you.  Please tell me how this went.

Sorry for this beeing in KDE if you use Gnome for example.  But i guess it is possible to do the same there allthough with different names.  Anyone with Gnome able to verify that ?

Good luck

---

### Post by imbjr on 2008-10-06
A word of caution: running wine under sudo is not advised.

---

### Post by alynx on 2008-10-06
> **imbjr said:**
> A word of caution: running wine under sudo is not advised.

fixed post.  Thanks

---

### Post by Sef on 2008-10-06
1) moved to WINE forum.

2) Do not bump unless 24 hours have gone by.  Thank you.

---

### Post by david_kt on 2008-10-06
> **Xonara said:**
> I've been trying to link to a windows executable for a while but I haven't had much success. I've tried many different things but I usually get some sort of permissions error or an error saying that the program failed to execute. The only thing that worked is dragging the app to the top panel, but I'd really rather not put every single windows program in an unorganized mess up there. I want to have an entry in the main bar but I keep getting errors when I launch it from the main bar.

I am not sure what you want to do. Do you want to create launcher on your menu for application run in wine? If yes, the easy way is:


System> Preference > Main menu

It will open menu editor. On menu editor:

Wine > Programs

or wherever you want to put your launcher. Make sure the focus is on the item column and click:
 + New Item.

It will open a new launcher. What you have to do is to fill up as you like, but on the command, follow below step:

1. Click browse and navigate to the exe file you want to launch. If the hidden folder not appear, press <ctrl> <H>.
2. After you have locate and select the exe file, move your cursor to the begining of the command, and insert wine. So, you command should become something like below:

```
wine "/home/david/.wine/drive_c/Program Files/example.exe"
```

It would create a launcher in your menu and should be able to launch your program.

Please let me know if I misunderstood you question.

DK

---

### Post by DaVince21 on 2008-10-06
About symbolic links: don't link it, it'll try to read/write data from the folder where your link is instead. Make a script that CD's to the actual app dir and runs it from there, or make a link that runs wine + the app in the right path instead.

---

### Post by Xonara on 2008-10-09
Sorry I didn't check back for... 3 days. Anyways, linking to a shell which changes to the app's directory and then opens it up in wine seems to work. Meh, guess I was making it more complicated than it really was or something...

Oh, and here's the 3 smiley faces holding popcorn. The popcorn's theirs though :D

:popcorn::popcorn::popcorn:

---

