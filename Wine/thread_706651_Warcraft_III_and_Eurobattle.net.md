---
title: "Warcraft III and Eurobattle.net"
date: 2008-02-24
forum: Wine
---

### Post by mad_max0204 on 2008-02-24
Is there anyone that plays on eurobattle.net ??
I installed both warcraft and frozen throne with no problems. Game runs fine.
Problem is that I cant connect to eurobattle.net. There is a eurobattle installed but that doesnt seems to work.
Anyone got this working ??


Thanks

---

### Post by Toffeeapple on 2008-02-24
Seems to be working fine for me... 

Gutsy 7.10 and wine 0.9.55 game and expansions patched to latest version.

What exactly is your problem? 

Hangs when connecting to battle.net? does not accept password? game just crashes? ....what's happening?

Have you read through [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1177") ?

If it makes you feel any better or at the very least fills you with hope.... it all works just fine for me : )

---

### Post by mad_max0204 on 2008-02-25
I install game just fine, expansion too, then I patch it with 1.21a patch and nocd and install that eurobattle.net loader. When I run the game and try to connect it says something about the game version and that I have to install the latest patch manually. When I patch the game with 1.21b and install the loader (same as the 1.21a but without nocd files) and I try to connect to "battle.net" it says that I'm trying to connect to invalid battle.net server bla bla bla. Theres just no way I can connect to eurobattle.net. What did you do to get it working ? What game version u using ? Where did you download loader or how did you edit bnet server ? Any info would be usable.

Btw I dont know if this makes any change but I'm using 64bit system.


Thanks

---

### Post by Toffeeapple on 2008-02-25
It may be because you have patched it with the nocd crack thing... which you don't actually need as V1.21b does away with the cd check.

I'm using the V1.21b.. Gutsy 7.10 and wine 0.9.55.. mine is 64 bit too.. I'm on a home network but I haven't had to forward any ports to get it to work, I just basically installed it then installed the expansion then when I tried to connect to battle net it automatically updated the game...

try without nocd crack but patched to latest version..

: )

---

### Post by Toffeeapple on 2008-02-25
I don't know what this loader you are talking of is??? why do you need to edit battle net servers?

---

### Post by mad_max0204 on 2008-02-25
Because I'm not playing on Battle.net. I'm trying to play on eurobattle.net. Thats different

---

### Post by mad_max0204 on 2008-02-26
Anyone ? I still didnt solve this problem

---

### Post by mad_max0204 on 2008-02-27
*bump

---

### Post by running_wild on 2008-03-14
You dont need install the loader.
Install the game and the pach 1.21a
them go [http://www.eurobattle.net/](http://www.eurobattle.net/) to get the files to enter on the server, its a small pach.

---

### Post by mad_max0204 on 2008-03-14
> **running_wild said:**
> You dont need install the loader.
Install the game and the pach 1.21a
them go [http://www.eurobattle.net/](http://www.eurobattle.net/) to get the files to enter on the server, its a small pach.

Well u just said 2 things that dont go together. LOADER = SMALL PATCH

Anyways, I removed everything related to wine, installed newest again and installed WCIII and all the patches and it worked. Just had to edit few registry entries and desktop icon and loader worked. Wine is getting better and better every day.

---

### Post by running_wild on 2008-03-14
> **mad_max0204 said:**
> Well u just said 2 things that dont go together. LOADER = SMALL PATCH

Anyways, I removed everything related to wine, installed newest again and installed WCIII and all the patches and it worked. Just had to edit few registry entries and desktop icon and loader worked. Wine is getting better and better every day.

Ok its the same thing, but its works. This loader/pach its available on the forum of eurobattle, i installed and play without problems.

---

### Post by Lorgend on 2009-05-06
hi gays.i am playing in the eurobattle.net pvpgn server.until yesterday i was playing normaly without any problems but today i cant connect and when i am triyng to connect to the servers wedsite it says tha it cant connect too.plz help!!!!!!!

---

### Post by krypel on 2009-05-15
So I installed everything with no problems, I can play with no problems but I can't connect to eurobattle.net cause its just not listed in servers list.. Any idea ?

Ubuntu 8.04
wine 1.0
newest euroloader from [www.eurobattle.net](www.eurobattle.net)
patch for version 1.23a

---

### Post by fdm on 2009-06-25
when you run the installer, it adds eurobattle.reg into your war3 directory and imports it. the problem is eurobattle.reg itself is unicoded as well as the data it contains. wine does not have unicode support(with the stable version at least), so it will not work. here is a simple alternative that i slapped together to remedy the situation.

[http://pastebin.com/f40954a0a](http://pastebin.com/f40954a0a)
or
[http://pastebay.com/24702](http://pastebay.com/24702)

just paste the registry information into a text editor and save it as a .reg file. next use wine's regedit to import it. after that, load euroloader(with -opengl) and choose the eurobattle.net server and connect.

---

### Post by Hairy_Palms on 2009-06-26
> **Lorgend Says**
hi gays.


:lol::lol::lol::lol::lol:

im mature honest

---

