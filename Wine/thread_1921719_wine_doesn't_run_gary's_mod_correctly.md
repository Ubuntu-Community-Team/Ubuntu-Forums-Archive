---
title: "wine doesn't run gary's mod correctly"
date: 2012-02-07
forum: Wine
---

### Post by bobman321123 on 2012-02-07
When I run it, it starts up, and the menu is fine (the font is a little messed up for the loading screen, but no biggie). But as soon as I get to the main menu, the entire background is black. It's almost as if the interface is there, but it's not rendering anything. The same happens when I get ingame. It refuses to render anything (it's all black) but the rest of the interface is there.
Help?

I'm running a AMD phenom IIx6 
8gb of RAM
Nvidia GTS 450
Ubuntu 11.10 (with gnome 3)

---

### Post by japzone on 2012-02-07
Here's it's WineHQ AppDB page you can look at for tips and known bugs: [**http://appdb.winehq.org/objectManager.php?sClass=version&iId=20687**]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20687")

I've never played before so I can't do anything but point you in the right direction, Sorry.

---

### Post by bobman321123 on 2012-02-07
Thanks for the link, but I already found that and it doesn't give a "how to", tutorial, or how to fix bugs. It just says how many people got it to work and how many did not. :P

---

### Post by CharlesA on 2012-02-07
Moved to the Wine forum. Wine isn't the same as Virtualzation. :)

---

### Post by bobman321123 on 2012-02-09
Oh, sorry. I looked for the wine section, but I didn't see it. 
That could either be me hallucinating, or reaaaaally tired :P

---

### Post by uh20 on 2012-02-10
try these launch options from steam
-nod3d9ex -dxlevel 81
theres also a requires font

but before doing any of this, go into terminal and type wine steam.exe and then run through garrys mod to post the crash

even while my garrys mod is stable, it still randomly crashes sometimes, without the dxlevel i heard that any time you died to a prop the game crashes, hehe

---

### Post by bobman321123 on 2012-02-11
Oh, perfect. -dxlevel81 fixed the problem. 
Also, what does -nod3d9ex do?

(I can't post the crash, because it doesn't crash. It runs, it just used to be totally black where it should render gameplay)

Thanks!
Josh

---

### Post by moshkubean on 2012-09-25
Hi, im trying to get my garrys mod to work with steam on wine/playonlinux. i have both wine and playonlinux installed, but when i try to start up garrys mod, it say, preparing to launch garrys mod, then the message will go away, and my mouse will dissappear, and nothing. i can only turn off my pc and start it again to get out of this. i just want to play garrys mod, will anyone help me? plzzzzzz??????????? ive been trying forever.

---

### Post by buntupanda1 on 2012-10-04
can someone post a picture on where you have to change dx level. i cant find it

---

### Post by WizardofOS on 2012-12-28
simply go to the games section and in the right hand side of the window you will see your games. right click on the one you want to add the options (parameters) to and select "properties". from there click "set launch options" and type in the options(parameters).

---

