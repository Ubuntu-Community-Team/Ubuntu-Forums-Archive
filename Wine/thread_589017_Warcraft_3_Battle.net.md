---
title: "Warcraft 3 Battle.net"
date: 2007-10-23
forum: Wine
---

### Post by EtrnlApocaplypse on 2007-10-23
With the latest version of Wine a bug has appeared where the game won't connect to battle.net it just idles at the Initializing step. I googled and saw that someone had released a couple of patches which fixed this but I'm not too handy with compiling it with the patches and such and was wondering if anyone else had this problem and happened to make a .deb of the latest wine with the patches in it. Much thanks in advanced if someone happens to have one!

---

### Post by evozniak on 2007-10-23
I am Experienced the same bug. The game try to connect to battle.net but never connect.
wine version 0.9.45 works fine with warcraft and battle net, but in my new gutsy install my arch is x64 and .45 packages for x64 not exists.
Someone can create 0.9.45 packages or patch newers versions?

Thanks

---

### Post by karth on 2007-10-24
The Wine dev team is aware about it, I guess it'll be fixed in later versions.

Still, the winsock replacement code in Wine has still a long way to go before being complete

---

### Post by EtrnlApocaplypse on 2007-10-31
:( 0.9.48 still seems to have the battle.net bug, bummer

---

### Post by biriachan on 2007-10-31
> **EtrnlApocaplypse said:**
> :( 0.9.48 still seems to have the battle.net bug, bummer

Been waiting a few days now for a 0.9.48 64bit Deb from WineHQ..... and Battle.net is still broken when I try in WC3.

I was able to use the ubuntu 7.04 (64bit) Wine 0.9.45 package installed and working.

Currently running Gusty 64bit

---

### Post by Colro on 2007-10-31
Just use [version 0.9.43](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.43~winehq0~ubuntu~7.04-1_i386.deb), it works fine with battle.net.

---

### Post by EtrnlApocaplypse on 2007-11-10
Wine 0.9.49 still has battle.net broken for all those wondering.... :-?

---

### Post by stfury on 2007-11-10
I have ubuntu 7.10 (gutsy) and the lowest version of wine offered is 0.9.47 - 

so is it true that i cannot play unless i downgrade to 7.04?

cheers stfury

---

### Post by EtrnlApocaplypse on 2007-11-10
No you dont need to downgrade ubuntu, you just need to get an earlier version of Wine they should work....i really do hope they fixed the b.net problem in a new version soon....

---

### Post by Colro on 2007-11-10
The version of WINE I linked works fine with Gutsy.

---

### Post by minhdinh on 2007-11-10
hellp me!! i installed the version of wine from ur link and it can play starcraft broodwar fine in single player but it still wont let me log in to battle.net. it gives me the exact same message that i get when i tried logging into battle.net with the newest version of wine. tell me wat u did to make it work please or link another version of wine that i can download n install

---

### Post by stfury on 2007-11-11
thanks for the help guys.

but when i click on battlenet now (after i installed 0.9.43) it says error, unable to validate game version

please help!

cheers,
stfury

---

### Post by stfury on 2007-11-11
Please Note, 
 
I have the latest  version (1.21 ) and have installed a nocd patch called acid loader (w3l.exe) even though i have a LEGAL copy of the game because i dont want to put the cd in each time. i have tried before and after patching and it gives me the same error - 

unable to validate game version.

Please help,
stfury

---

### Post by mikerobinson on 2007-11-19
> **stfury said:**
> Please Note, 
 
I have the latest  version (1.21 ) and have installed a nocd patch called acid loader (w3l.exe) even though i have a LEGAL copy of the game because i dont want to put the cd in each time. i have tried before and after patching and it gives me the same error - 

unable to validate game version.

Please help,
stfury

Hmm that reminds me, I applied some sort of No-CD patch to my WC3 too so that I didn't have to put the CD in every time and upon upgrading to 0.9.46 it stopped connecting to Battle.net. Did everyone else who's having problems with Battle.net do something similar, applying some sort of patch or crack to the game? If so, it would just be a matter of reinstalling.

---

### Post by sgtbug on 2007-11-19
i hav tried it through cedega.. it works perfectly.. i suggest u buy cedega.. wine gave problems to me too..

---

### Post by EtrnlApocaplypse on 2007-12-02
Latest version of Wine finally fixed battle.net :) Yay.

---

### Post by frolle on 2007-12-05
Sounds great. I will look into this when im home :)

---

### Post by AsoSako on 2007-12-05
Yeey for Battle.Net on Linux :D

---

### Post by jav_ on 2007-12-06
can anyone else confirmbattle.net works on 0.9.50?
thanks

---

### Post by psycho5 on 2007-12-16
Has anyone run the battle.net private server [[COLOR="Blue"]Blueserver[/COLOR]]("http://blueserver.org/?s=noobpack") with the latest version of wine? 

I've tried running it, it doesn't load up. I play on that server because of the anti-hack support and the ability to report game abusers.

---

### Post by jav_ on 2007-12-23
hey guys im running wc3 with wine 0.9.51 and during the game..i cant see a lot of ppl type... is anyone else having the same problem?

---

### Post by 0g_Trans_Fat on 2007-12-23
I am running warcraft 3 on wine v0.9.51 and it works well on battle.net, however i have one problem while joining some custom games.  If the custom game is not able to be joined, then the program freezes, and i must kill it.  Also, if the host leaves durring the countdown, it also freezes.  Other then that, it works great.

---

### Post by jav_ on 2007-12-23
> **0g_Trans_Fat said:**
> I am running warcraft 3 on wine v0.9.51 and it works well on battle.net, however i have one problem while joining some custom games.  If the custom game is not able to be joined, then the program freezes, and i must kill it.  Also, if the host leaves durring the countdown, it also freezes.  Other then that, it works great.


i have the same problem with the freezeing when it wont join the game as well...havent had any host leave before it starts though...can you see everyone typing? or u prolly dont notice..

---

### Post by jav_ on 2007-12-26
hey guys i have my network set to static ip and opened port 6112 but i still cant host...is it a bug from the new version? i remember hosting on the older version..

---

### Post by jordank on 2008-01-04
Hey the version of wine linked above is for 32bit.

Does anyone have a link to the older version of wine that works on 64 bit?

---

### Post by jackmo on 2008-01-17
> **Colro said:**
> Just use [version 0.9.43](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.43~winehq0~ubuntu~7.04-1_i386.deb), it works fine with battle.net.

sorry to be a nub, but can anyone please give me some pointers on how to go about uninstalling wine and installing an old version? I managed to get wine installed and load wc3, but after finding these threads I've had little success in figuring out how to uninstall wine and then install an older version.

---

### Post by yxrkt on 2008-01-17
don't konw what you're all talking about, i have latest version of wine and it works fine with gutsy =\. i did install the patch that someone made (posted on this forum i think) but i'm not sure if bnet was working before that

---

