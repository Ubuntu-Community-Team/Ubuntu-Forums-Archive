---
title: "Playing Games (DOTA2 mainly) on Ubuntu"
date: 2013-01-10
forum: Wine
---

### Post by LinuxBill on 2013-01-10
Im looking to shift over to Linux even more, currently I have my windows machine primarily for gaming. I rarely use it of anything else. I have installed ubuntu 12.10 on my Macbook and i would like to transistion to this machine for my general needs as much as possible. It has a ATI 512MB GPU which is pretty powerful and good enough to play games at the macbook resolution. I have not been playing much else other than dota on my PC so this is the main game i would like to move over if possible. My questions are as follows:
[LIST]
[*]Does anyone have experience playing DOTA2 in wine/playonlinux ?
[*]Is the 3D performance in Virtualbox good enough to play games, i would just use virtual machine if it is ?
[/LIST]Any help on this would be a great help. 
 
Thanks
Bill

---

### Post by dud3r on 2013-01-10
I've been looking into the same thing. DOTA2 is the only reason I still run Windows. Apparently Steam is in open beta on linux and a DOTA2 client is expected.

---

### Post by mastablasta on 2013-01-10
> **LinuxBill said:**
> 
 
Does anyone have experience playing DOTA2 in wine/playonlinux ?
 
 
according to wine application database it has platinum rating = everything works:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13522](http://appdb.winehq.org/objectManager.php?sClass=application&iId=13522) 
also STEAM has a linux client now...
 
> 
Is the 3D performance in Virtualbox good enough to play games, i would just use virtual machine if it is ?

 
as i know 3D in vbox is experimental. also it's not so good. i would go with wine in this case and also many others. wine will use the GPU and GPU more propperly than vbox since **W**ine **I**s **N**ot an **E**mulator.
 
edit make sure oyu have good drivers available for the AMD card you have. radeon HD 2xxx,3xxx,4xxx suport was dropped in 12.10. maybe also 5xxx not sure here.

---

### Post by Sofox on 2013-01-10
Valve will probably port DOTA2 to Linux in the long term, it runs on the Source engine and Valve have been clear about their Linux strategy. However, it could be a while before this happens (especially with Valve Time) so you're probably better off going with an interim solution.

---

### Post by LinuxBill on 2013-01-10
Thanks guys. I did think DOTA2 would come eventually, but like Sofox said it might be a while. Ill go with WINE then. Never set it up before but i reckon it cant be that hard, and there must be some guides kicking about. Cant remember the exact name of the ATI GPU in the laptop but its a 2011 Macbook Pro so im sure the drivers will still be supported.

---

### Post by ZombieApocalypse on 2013-01-10
> **mastablasta said:**
> edit make sure oyu have good drivers available for the AMD card you have. radeon HD 2xxx,3xxx,4xxx suport was dropped in 12.10. maybe also 5xxx not sure here.

5xxx is still supported.

---

### Post by MontrealCorp on 2013-01-10
i know dota2 isnt exactly WC3 dota, but wine with dota play great no doubt about it.
 
my main problem tho is this, my mouse seem to keep lagging 1 sec, i moved it but the cursor doesnt follow has quickly has i want it too. 
so playing those games that need speed with the mouse isnt there yet for me.
 
i try find a solution on a lot of sources, even try some changes i learned about and end up crashing my OS :)
 
yes i did made drivers updates and all about my video card .
 
anyway the game is working great if u dont have the mouse problem i have :(.
 
if anyone got any fix please tell me :)

---

### Post by mentorious on 2013-01-11
I installed this game with Crossover and works fine! Without nerves, tricks etc. It's really better than "clear" wine. to run windows games. 

I play currently in Dota 2, Portal, Counter Strike: GO, PES 2013 and ETS using this app.

---

### Post by holastickboy on 2013-01-11
> **mastablasta said:**
> according to wine application database it has platinum rating = everything works:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13522](http://appdb.winehq.org/objectManager.php?sClass=application&iId=13522) 
also STEAM has a linux client now...
 

 
as i know 3D in vbox is experimental. also it's not so good. i would go with wine in this case and also many others. wine will use the GPU and GPU more propperly than vbox since **W**ine **I**s **N**ot an **E**mulator.
 
edit make sure oyu have good drivers available for the AMD card you have. radeon HD 2xxx,3xxx,4xxx suport was dropped in 12.10. maybe also 5xxx not sure here.

The older Radeon HD support was actually dropped by AMD/ATI.  It's in the same state on Windows (stuck at Catalyst 12.6).  Was a real point of controversy, especially because a few of the HD 4xxx series share the same architecture as the supported HD 5xxx series. Still, grab an Nvidia card for Linux WINE gaming if you can!

---

