---
title: "How run shake 4.1 on a 64 bit!"
date: 2007-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Madj on 2007-12-01
[COLOR="Black"][B]I think this could be very interisting to a lot of people to solve this problem/
How make shake 4.1(32 bit) working on a 64 bit.?[/B][/COLOR]

I ve follow these command i found on the forum to install shake 4.1 but it s still not working:
So i ve made first that :To create a lib 32 bit on ubuntu:

sudo apt-get install dpkg-dev
cd ~/Desktop/usr/lib
cp -r ./* /usr/lib32/

And then i try to install the program shake 4.1.tar.gz:

First i ve Unpack shake and create dir. /usr/appl
then : gksu nautilus
then i move upacked folder to /usr/apple
install csh and tcsh
chmod 755 * /usr/apple/shake.../bin
csh shake

and when i do sudo shake or csh shake the terminale respond:

/usr/apple/shrank/shake4/bin# csh shake
/usr/apple/shrank/shake4/bin/shkx.exe: Command not found.



[B]Can someone  help us with his knowledge or give any advice,Thank you in advance.
__________________[/B]

---

### Post by Kilz on 2007-12-01
My first bit of advice is not [to double post]("http://ubuntuforums.org/showthread.php?t=628427") questions before you get an answer. The second bit of advice is that .exe is a windows format and will not run nativly under linux.

---

### Post by Madj on 2007-12-01
Yes you re right i ll not do this again!

About this file shk.exe i saw on some other forum, where they manage to install it , with other version of linux that it  s normal but strange  it s a file wich his part of the application.

Seems to be really complicate to install for a newbie!

Help!

---

### Post by maxikiri on 2007-12-09
Sorry I wrote my first message in french, miust have been very tired ;-) so here comes the english version:

I unfortunately I cannot help you so much, as i am experimenting the same issue, however i have some info.

I am running shake 3.5 on three linux box running dedora core 4 32 bit and didn't have any problem installing or running shake on them. To install you just have to move the nreal folder to the place of your choice, standard been to move it to /usr/nrreal
Then in the bash you create an alias, but you can run it with /usr/nreal/bi/shake. This work on all distro i have seen, but not on the fedora 8 x64 I've just install.

if somebody succeed to run shake on x64 linux distro I am interested.

thanks,
antoine.

(hello malheureusement je ne peux pas tellment t'aider vu que j'ai plus ou moins le même problème, par contre je peux quant même éclairer un peu le sujet.

J'ai shake 3.5 qui tourne sur 3 pc tournant fedora core4 32 bit et j'ai jamais eut de problème à le tourner, ni à l'installer (l'install se résume à mettre le dossier nreal où tu veux, mais le standard c'est dans /usr/nreal).
Ensuite tu set le bash avec un alias ou shake pointe sur /usr/nreal/shake3.5/bin/shake
et normalement ça marche, mais là j'ai fedore 8 x64 et cela ne prends pas.

ach, je suis preneur de conseil pour un shake tournant sur une distro de linus x64.)

merci,
antoine

---

### Post by Madj on 2007-12-10
To have shake working on a x86 64 bit you have to create a lib 32 and make sure all thie lib  link correctly.
Here is the tutorial to create a lib 32 on a x86 64 and make shake working : [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)  

So let me know if it works ?

---

### Post by Explodicide on 2008-07-15
I hate to drag an old thread up from the depths, but I'm having the same issue getting Shake running on my friend's XPS laptop, 64 bit.  I've installed Shake and csh, as well as the libs needed to get it running on Hardy, but whenever I run the main launch script `shake` I get the same as above:

/usr/shake/bin# csh shake
/usr/shake/bin/shkx.exe: Command not found.

Before anyone says anything about it being an .exe file, it's just named that way.  It IS a proper linux binary executable, it's just named that way, probably because the developers were too lazy to change the names of the executables when they wrote the linux variant.  I've got Shake working on 2 other (32-bit) Hardy systems, not to mention every compositing station at my school has the same setup.

Also, my environment variables and everything else is set up fine, and the file that it's trying to reach is in that path.

Has anybody managed to figure out what Shake needs to run properly in a 64-bit environment?  I tried reading through this:
> **Madj said:**
> To have shake working on a x86 64 bit you have to create a lib 32 and make sure all thie lib  link correctly.
Here is the tutorial to create a lib 32 on a x86 64 and make shake working : [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

but that script doesn't work properly.  The shake application isn't set up in the same format as standard repository apps, and doesn't come in a .deb package so that might be why.

Has anyone gotten this working?

---

