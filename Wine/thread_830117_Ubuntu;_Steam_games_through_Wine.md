---
title: "Ubuntu; Steam games through Wine"
date: 2008-06-15
forum: Wine
---

### Post by Jaded Misanthrope on 2008-06-15
How would I go about getting Steam games to work through Wine? I found this tutorial, which allows me to open Steam fine (with the exception of Steam friends, which does not work properly, but I gather that this applies to everybody who has managed to get it working) and launch a game to the 'New Game', 'Load Game', et cetera, menu.

However, on some games (most notably Team Fortress 2; I don't seem to remember this happening on any other game) the game window flashes between what it is meant to be showing and either just blackness or the screen shown when the main menu is loading. However, on others the main menu is fine, but when I start a game, I just get a screen that is one solid colour (although said colour varies as time goes on; I assume that it changes depending on what should be shown). Can anybody give me any help on how to get Steam games working properly on Ubuntu?

---

### Post by cogadh on 2008-06-15
It would help to know some information about your PC, such as hardware specs, Ubuntu version and Wine version. Also, the terminal output from Wine may give us an informative error message that could explain exactly what is happening.

---

### Post by Jaded Misanthrope on 2008-06-15
Sure thing; I'll nab those things now.

---

### Post by DDJ on 2008-06-15
I would check out WineHQ.  I use Steam for HL2, HL and CS and it seems to work fine.  With the notable exception of low fps on CS.  That said, WineHQ is a good place to start.  

Hope this helps.  Also check out [http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332) this link tells a lot about how to use WINE, but also shows you to how have WINE properly detect the correct memory on your video card to improve performance.  According to this article, WINE defaults to 64mg on video cards, so you may not be using your card to its fullest potential.

Good Luck. Hope this helps.

---

### Post by YokoZar on 2008-06-16
You might want to try fiddling with the launch options and setting something like -dxlevel 80 to see if that helps

---

### Post by Fred_E _krugar on 2008-06-16
> **YokoZar said:**
> You might want to try fiddling with the launch options and setting something like -dxlevel 80 to see if that helps


I would also like to know how to enable this feature. NM

---

### Post by cogadh on 2008-06-16
Just right-click on the the game in Steam's My Games browser, select Properties, click on the "Set launch options..." button and type "-dxlevel 80" (without the quotes) in the field. Alternatively, you can launch the game directly from the terminal with a command like this:
```
wine steam.exe -applaunch 220 -dxlevel 80
```
That particular command will launch Half-Life 2, but you can change the applaunch number to any Steam game. A full list of applaunch ID numbers for Steam games can be found [here](http://developer.valvesoftware.com/wiki/Steam_Application_IDs). NOTE - The "-dxlevel" launch option only works on Source-based games (Half-Life 2 and episodes, Counter-Strike: Source, Vampire: Bloodlines, etc.).

---

### Post by iaswni on 2008-06-16
it could be compiz behind this and your graphics card.
i got the same problem when launching something with heavy graphics but its not a bug,
 its my ATI card and the proprietary driver.
 maybe if you disable the visual effects and try again it will work fine

---

