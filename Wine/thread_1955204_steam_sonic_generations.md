---
title: "steam sonic generations"
date: 2012-04-09
forum: Wine
---

### Post by sonic dude on 2012-04-09
hi! 
I recently downloaded sonic generations in my steam account. Every time I  click play it gives me the option to run the game or the config tool,  both do not work. when I choose either one, it tells me preparing to  launch sonic generations then installing first time set up (step 1 of  1). Closes and then nothing. I tried re-installing steam, re-downloading  the game, opening it from the the steamapps folder, verifing the game  cache, disabling steam community in-game, and closing all other running  apps. However, I don't have enough ram memory required for the game in  my pc, does that have anything to do with it? please help me fix this I  am desperate!!!

wine 1.2.2
ubuntu 10.04

---

### Post by synaptix on 2012-04-09
I'm assuming this is the right one:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25455](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25455)

> **Additional Comments**
You will need to install DirectX and dotnet35 in order to run the game config and play the game.   "If you get a message stating the the configurations do not match the hardware then create C:/user/-yourname-/My Games" Then it should work properly. 

---

### Post by sonic dude on 2012-04-09
how do I download directx and dotnet35

---

### Post by synaptix on 2012-04-09
Use winetricks, open terminal and type:

```
winetricks d3dx9 dotnet35
```

---

### Post by sonic dude on 2012-04-09
it just sais command not found

---

### Post by synaptix on 2012-04-09
Oh, probably don't have winetricks installed (it usually installs with wine as default):

```
sudo apt-get install winetricks
```

Then run the winetricks command again;

```
winetricks d3dx9 dotnet35
```

---

### Post by sonic dude on 2012-04-09
After I download do I have to run the game through a special program or will it work normall on steam?
Do I have to upgrade Ubuntu or wine
Wine1.2.2
Ubuntu 10.04

---

### Post by synaptix on 2012-04-09
> **sonic dude said:**
> After I download do I have to run the game through a special program or will it work normall on steam?

It should work as normal through Steam.

---

### Post by sonic dude on 2012-04-09
Do I have to upgrade Ubuntu or wine?
Wine 1.2.2
Ubuntu 10.04

---

