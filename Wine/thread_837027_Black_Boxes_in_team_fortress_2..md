---
title: "Black Boxes in team fortress 2."
date: 2008-06-22
forum: Wine
---

### Post by the_bob on 2008-06-22
I have just killed my windows partition today and I thought what better excuse to leave windows all together. The one reason I use windows is to play my steam games. I tried to install team fortress in wine but I'm getting black boxes any place info should pop up on screen

[IMG]http://img171.imageshack.us/img171/2167/screenshot1ye7.png[/IMG]

Also I can not see the words when I go to find server

[IMG]http://img171.imageshack.us/img171/5194/screenshotteamfortress2te1.png[/IMG]

---

### Post by Trance56k on 2008-06-22
You need the Tahoma Font, you can get it from here [http://www.fontstock.net/11080/Tahoma.html]("http://www.fontstock.net/11080/Tahoma.html")

---

### Post by the_bob on 2008-06-22
I did. Do I need to uninstall steam and reinstall?

---

### Post by Kronie on 2008-06-22
no.. just quit and restart.. 


and i have almost the same problem T_T steam worx fine for me(except friends ofcourse) i go to TF2, and i see the valve logo, then  go to main menu, go on server, and everything is just the way it should be, but in game, i get theese 2 huge black boxes in the right hand corners of the screen! it takes away almost half of the screen, and i cant see whos on the left side of me so i have to constantly turn to check..

PS: am i the only one who cant see other player's achievments through steam community?

PPS: how to run TF2 in windowed mode? 0_o

PPPS: what theme are u using 
and 
PPPPS: am i the only one who gets theese freezez after 20 minutes of playing TF2? the only way to get out of it is restart..

---

### Post by the_bob on 2008-06-22
> **Kronie said:**
> no.. just quit and restart.. 


and i have almost the same problem T_T steam worx fine for me(except friends ofcourse) i go to TF2, and i see the valve logo, then  go to main menu, go on server, and everything is just the way it should be, but in game, i get theese 2 huge black boxes in the right hand corners of the screen! it takes away almost half of the screen, and i cant see whos on the left side of me so i have to constantly turn to check..

PS: am i the only one who cant see other player's achievments through steam community?

PPS: how to run TF2 in windowed mode? 0_o

PPPS: what theme are u using 
and 
PPPPS: am i the only one who gets theese freezez after 20 minutes of playing TF2? the only way to get out of it is restart..

Friends achievements don't work for me either? To run in windowed go into the video settings inside TF2 and there is resolution, aspect ratio, and windowed or fullscreen drop boxes.

I'm using overglossed GTK 2 and emerald theme. you can find them at gnome-look.org. Screenlets program, and my wallpaper is [http://interfacelift.com/wallpaper/details.php?id=1324](http://interfacelift.com/wallpaper/details.php?id=1324) Interface lift is a great website!

Try updating wine to get fix the freezeups. I use 1.0 or try changing the windows version.

Ok back on topic. I downloaded the tahoma.ttf and put it in home/bob/.wine/drive_c/windows/fonts folder and reinstalled steam and TF2 but the boxes are still there? am I doing something wrong?

---

### Post by the_bob on 2008-06-23
Steam uses the font Tahoma which is included in all Windows versions, but is not available on Linux. This will result in invisible text when running Steam without installing Tahoma first. 
    The easiest way to work around this issue is to put a copy of tahoma.ttf from a Windows installation (%WINDIR%\Fonts) to ~/.wine/drive_c/windows/fonts. 
Image:note.png Note: With newer versions of Wine you have to copy tahoma.ttf to ~/.wine/drive_c/windows/fonts/

what does that mean? I found that in a howto.
the end /fonts or /fonts/
How do I add the extra /?

---

### Post by Kronie on 2008-06-23
oh.. i forgot.. tahoma is included in wine 1.0 by default..so..

---

### Post by the_bob on 2008-06-24
I have tried everything. I have now reinstalled ubuntu, used 3 different versions of wine, tried the tahoma fonts from online and from my windows partition, tried putting the bold version from my windows folder. I don't understand what I'm doing wrong. I've looked online for hours and I can't find anyone with my problem. 

Can anyone help me?

---

### Post by the_bob on 2008-06-24
I bought crossover games and it worked right out of the box. I guess you get what you pay for. However after playing for a few mins the characters all loose there color making it very hard to tell teams.

[IMG]http://img361.imageshack.us/img361/9056/screenshotzr4.png[/IMG]
By [bobonthecob](http://profile.imageshack.us/user/bobonthecob) at 2008-06-24

any ideas on this one?

---

### Post by Kronie on 2008-06-24
yea i was getting same lags in windows sometimes.. try messing around with shadows and shaders.. btw how much u bought crossover for?

---

### Post by the_bob on 2008-06-25
> **Kronie said:**
> btw how much u bought crossover for?

39.95 or something like that. Try the 7 day trial before you spend the money.

---

### Post by diaa on 2008-07-08
> **the_bob said:**
> I have just killed my windows partition today and I thought what better excuse to leave windows all together. The one reason I use windows is to play my steam games. I tried to install team fortress in wine but I'm getting black boxes any place info should pop up on screen

[ images snipped ]

Also I can not see the words when I go to find server

[ images snipped ]



I had exactly the same problem, I installed Tahoma and did everything but it didn't go, only one thing solved it, I added -dxlevel 81 to the command-line of the game, you should either run the game as follows:

```
wine <path_to_steam> -applaunch 440 -dxlevel 81
```Or *set launch options* of the game from inside steam(Right-click -> Properties) to

```
-dxlevel 81
```Note: You can also add *-novid* to skip the annoying video intro

Hope this helps.

---

