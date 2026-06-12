---
title: "Internet Explorer"
date: 2008-04-22
forum: Wine
---

### Post by piperdown10 on 2008-04-22
Firefox is a fantastic web browser but I need IE for work. How can I get it up and running? I tried starting it and it said that GECKO was installing but now I get nothing.

---

### Post by cogadh on 2008-04-22
Don't install IE in Wine (it can and will break Wine), use IEs4Linux instead:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by jimoz on 2008-04-22
I need IE for an application that wont take anything else... I installed ies4linux but the app wont detect ie and quits out on install. Are there other registry settings I need to add for it? 
I tried using winetricks fakeie6, but the problem is that when the app links to a webpage through firefox, an incomplete link is displayed (i.e. the domain and path, but not the actual cgi script). I woulda prefered just using the fakeie6 workaround, but figured ies4linux would be easier...

---

### Post by zenwalker on 2008-04-22
Well see what version of IE u need. Coz Ie4linux from tatanka has 5/6 and now 7 also i guess.

---

### Post by cogadh on 2008-04-23
> **jimoz said:**
> I need IE for an application that wont take anything else... I installed ies4linux but the app wont detect ie and quits out on install. Are there other registry settings I need to add for it? 
I tried using winetricks fakeie6, but the problem is that when the app links to a webpage through firefox, an incomplete link is displayed (i.e. the domain and path, but not the actual cgi script). I woulda prefered just using the fakeie6 workaround, but figured ies4linux would be easier...
To get the app to detect IE at install, all you should need to do is add/create the necessary registry entries in Wine that will tell the install that IE is present. See the Wine "Useful Registry Keys" page for details:
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by zami on 2008-04-23
> **jimoz said:**
> I need IE for an application that wont take anything else... I installed ies4linux but the app wont detect ie and quits out on install. Are there other registry settings I need to add for it? 
I tried using winetricks fakeie6, but the problem is that when the app links to a webpage through firefox, an incomplete link is displayed (i.e. the domain and path, but not the actual cgi script). I woulda prefered just using the fakeie6 workaround, but figured ies4linux would be easier...

I had the same problem.  I needed to register Insaniquarium (a Popcap game) which absolutely insists on launching IE6 for registration.  Tweaking the registry just seemed to confuse the registration program further because the regsitry was saying IE was installed when it was not.

Anyhow I *did* eventually get IE6 working in my .wine directory, but I had to delete .wine and START FROM SCRATCH.  It did not work to install IE6 in my existing .wine directory, for whatever reason I could only get it working when starting from scratch.  ::shrug:: I have no explanations!

Anyhow, if that's a route you are willing to take, you need to follow the instructions at WineHQ for IE6SP1
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=469](http://appdb.winehq.org/objectManager.php?sClass=version&iId=469)
They are *not* in great order the but the information is all there.  Follow the threads with the following titles -

-HOWTO Offline Installation (near the top)
-OOPs one more thing for the instructions below (several posts down)
-IE is supported. I got it installed with a few tweaks (also several posts down)

The only thing I did different was, I did a basic "winecfg" to make the regular prefix instead of the alternate prefix command listed in the instructions "wineprefixcreate --prefix ~/.wineIE6"

YOU might want to try the alternate prefix and install IE6 to .wineIE6 instead of .wine, and then just install whatever picky program is asking for IE into .wineIE6 as well.  I just decided to start from scratch with everyything in the .wine directory for the sake of simplicity - plus frankly I don't understand how to install a Windows program and pick which wine prefix it goes to.  A lot of installers just don't show anything "higher up" then what they perceive as "c:"

An easier option would be to buy Crossover Linux!  Just install IE6 and the program that needs it into the same "bottle".  Crossover is an awesome product - I wont bore you with details, their praise is sung all over these forums.  :D

Good luck!

-zami

- oh yeah, when I say "delete .wine", you should actually just rename it .winebackup or something so if the IE install is a total flop you can just put your old directory back into place.  Plus if you have any large installations in there, for example WoW, you can reinstall it, and then move the updated files from .winebackup to .wine instead of updating for 100+ hours.

---

### Post by piperdown10 on 2008-04-29
> **zenwalker said:**
> Well see what version of IE u need. Coz Ie4linux from tatanka has 5/6 and now 7 also i guess.

I installed it with no problems but am having difficulty getting it to run properly. I haven't had much time to mess with it but I will keep at it.

---

