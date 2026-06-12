---
title: "New to linux.. help"
date: 2005-07-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Boggles3 on 2005-07-13
hi.. my first question is should i be running 64.
i looked into it and it seemed as though i should be..
im running a dual xeon 3.0 machine wif 2 gigs ram audigy 2 sound and nvidia quaro 1300 graphics card..

secont question is.. i want to install the upgaded driver..(the one in nvidia downloads)
because my card is very powerfull and im not ganna settle for generic nvidia-gfx stuff

ive downloaded the driver for it and am trying to install it but i cant seem to get it to work .

nvidia suggests lowering the runlevel to 3 in order to instal the driver.
all i know how to do is shut down x server so that no gl is running.
wich so far i have to do because if im running xserver and try to run the driver install it ses there seems to be an xserver running and i need to kill it..

ok so i do that and kill it. then i run it from console and i get error saying it needs to be run from root or NVidia needs to be root or something like that..

i think maybe i can get it to work if i can figure out how to edit the runlevel..

can anyone help.. ](*,) 
thanx alot

---

### Post by trivialpackets on 2005-07-13
[QUOTE=Boggles3]hi.. my first question is should i be running 64.
i looked into it and it seemed as though i should be..
im running a dual xeon 3.0 machine wif 2 gigs ram audigy 2 sound and nvidia quaro 1300 graphics card..

secont question is.. i want to install the upgaded driver..(the one in nvidia downloads)
because my card is very powerfull and im not ganna settle for generic nvidia-gfx stuff

ive downloaded the driver for it and am trying to install it but i cant seem to get it to work .

nvidia suggests lowering the runlevel to 3 in order to instal the driver.
all i know how to do is shut down x server so that no gl is running.
wich so far i have to do because if im running xserver and try to run the driver install it ses there seems to be an xserver running and i need to kill it..

ok so i do that and kill it. then i run it from console and i get error saying it needs to be run from root or NVidia needs to be root or something like that..

i think maybe i can get it to work if i can figure out how to edit the runlevel..

can anyone help.. ](*,) 
thanx alot[/QUOTE]
 I believe to change runlevel just go to terminal, type in sudo init 3, not even sure if sude is necessary.  In addition, to run the software, run sudo NVIDIA-blahblah......sh to install.  Good luck, I hope you get it running so I can hate you for having that system running.  j/k.  :)  Also, if you have too many issues, give 32 bit a try.  It runs fine for me iwth the linux-k7 kernel.  Good luck.

---

### Post by fistfullofroses on 2005-07-13
[QUOTE=Boggles3]hi.. my first question is should i be running 64.
i looked into it and it seemed as though i should be..
im running a dual xeon 3.0 machine wif 2 gigs ram audigy 2 sound and nvidia quaro 1300 graphics card..

secont question is.. i want to install the upgaded driver..(the one in nvidia downloads)
because my card is very powerfull and im not ganna settle for generic nvidia-gfx stuff

ive downloaded the driver for it and am trying to install it but i cant seem to get it to work .

nvidia suggests lowering the runlevel to 3 in order to instal the driver.
all i know how to do is shut down x server so that no gl is running.
wich so far i have to do because if im running xserver and try to run the driver install it ses there seems to be an xserver running and i need to kill it..

ok so i do that and kill it. then i run it from console and i get error saying it needs to be run from root or NVidia needs to be root or something like that..

i think maybe i can get it to work if i can figure out how to edit the runlevel..

can anyone help.. ](*,) 
thanx alot[/QUOTE]
 Ok. not a hard problem to help you with.
First, when in console (no xserver running) type in sudo -s
This will prompt you for your password, so type it in.
You are now the "root" user.
the type " ./NVIDIA........... -sh "
that will run the install shell script.

---

### Post by Boggles3 on 2005-07-13
ok thanx alot guys.. i wasnt writing sudo infront of my sh nvidia.... .run file(likr an idiot but im new so forgive me...
i went through and it couldnt install because kernal was wrong or something. 

something about installing gcc and checking if cc is in path..
??

not sure but the read me from nvidia made it seem as though its a regular thing you gatta do if your not running redhat..

is this correct? and if so any particular place i should go to get this gcc file

thanx alot for the help again :)

---

### Post by fistfullofroses on 2005-07-14
[QUOTE=Boggles3]ok thanx alot guys.. i wasnt writing sudo infront of my sh nvidia.... .run file(likr an idiot but im new so forgive me...
i went through and it couldnt install because kernal was wrong or something. 

something about installing gcc and checking if cc is in path..
??

not sure but the read me from nvidia made it seem as though its a regular thing you gatta do if your not running redhat..

is this correct? and if so any particular place i should go to get this gcc file

thanx alot for the help again :)[/QUOTE]
 gcc and cc... I have the same problems quite often... try google for deb sources... or apt-get install gcc... or something. not sure. I will fish around and get back to you.

---

### Post by jon_gunnar on 2005-07-14
[QUOTE=Boggles3]ok thanx alot guys.. i wasnt writing sudo infront of my sh nvidia.... .run file(likr an idiot but im new so forgive me...
i went through and it couldnt install because kernal was wrong or something. 

something about installing gcc and checking if cc is in path..
??

not sure but the read me from nvidia made it seem as though its a regular thing you gatta do if your not running redhat..

is this correct? and if so any particular place i should go to get this gcc file

thanx alot for the help again :)[/QUOTE]
You got an excelent guide at [http://ubuntuguide.org/](http://ubuntuguide.org/) that will help you a lot
And you will probably need to installl the build-essential. Get it like this:
sudo apt-get install build-essential
You may need the kernel source too.
Find your'e kernel version with:
uname -r
Then 
sudo apt-get install linux-source-2.6.x

I would strongly suggest having a look at the Ubuntu guide. It is very helpfull.

---

### Post by Boggles3 on 2005-07-14
ok so i installed the build-essentials and ran the sudo apt-get install linux-source thing and it installed but now when i try to install nvidia drivers i get this error
unable to find kernel source tree for currently running kernel

whats this all about i thought thats what i just did?? ](*,) 

thanx again for ur efferts all of you. its really appritiated

---

### Post by fistfullofroses on 2005-07-14
[QUOTE=Boggles3]ok so i installed the build-essentials and ran the sudo apt-get install linux-source thing and it installed but now when i try to install nvidia drivers i get this error
unable to find kernel source tree for currently running kernel

whats this all about i thought thats what i just did?? ](*,) 

thanx again for ur efferts all of you. its really appritiated[/QUOTE]
 you can "apt-get install gcc"

---

### Post by varunus on 2005-07-14
I think you need to apt-get install the package "linux-headers-" for your kernel version too, not just linux source.

Good luck.

---

### Post by Boggles3 on 2005-07-14
ok thanx alot guys ive succesfully installed the 7667 driver..

really i appriciat all your help im sure i will be posting many more problem i have...
since im new to linux :) 

again thanx for your help all \\:D/

---

### Post by fistfullofroses on 2005-07-14
[QUOTE=Boggles3]ok thanx alot guys ive succesfully installed the 7667 driver..

really i appriciat all your help im sure i will be posting many more problem i have...
since im new to linux :) 

again thanx for your help all \\:D/[/QUOTE]
 You are welcome... though may I suggest this as well:::: write down everything you do, keep a log of it you know??? you may need to do something similar again later down the line

---

### Post by DancingSun on 2005-07-14
[QUOTE=Boggles3]ok thanx alot guys ive succesfully installed the 7667 driver..

really i appriciat all your help im sure i will be posting many more problem i have...
since im new to linux :) 

again thanx for your help all \\:D/[/QUOTE]
Now that you have your brand new driver, be sure to post your glxgears score to [this](http://ubuntuforums.org/showthread.php?t=39349) thread!  Just open a terminal and type "glxgears".

---

