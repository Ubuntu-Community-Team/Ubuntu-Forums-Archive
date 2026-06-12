---
title: "games in fullscreen with wine are not true fullscreen?"
date: 2007-11-14
forum: Wine
---

### Post by ehcualp on 2007-11-14
when ever i play games with wine in fullscreen, my mouse is allowed to leave the "full"screen. I have checked the box labeled "allow directx apps to stop mouse from leaving window", but it still escapes. 
I can tell it escapes, because in the game (in this case, portal, but happens in all of my games) in the menus the mouse is white. my mouse in ubuntu is black, and around the edges of the screen i can see my mouse flicking back and forth between the white mouse and the black mouse. also when i try to turn around in the game(s) via the mouse, it will turn the character, but then leave the screen, stopping me from turning.
and while im posting about wine and this game, when i try to move via w,a,s,d, i can not aim, nor fire my weapon. and then when i release the move keys, my mouse will spring back into action and go to where i moved it while moving my character. its like using  those four keys freezes my mouse. i have rerouter them to the arrow keys but it does the same thing.

Ubuntu Gusty
wine 0.9.49
unrelated?:
i do use compiz, and awn.

---

### Post by Stormspireiv on 2007-11-14
It is most likely compiz screwing with it.  When I try to run a Wine game fullscreen, even with the compiz-fusion fullscreen workaround plugin, it messes with the fullscreen.  For example, whenever my network icons flash for send/recieve, it shows it in the wine app.  Never had a cursor problem though.

Try installing a tray icon to quickly switch between compiz and metacity (or Kwin if you are Kubuntu). Disabling compiz when running games also makes the games run faster.

Edit: I use fusion-icon.  .deb package here: [http://ubuntuforums.org/showpost.php?p=3163821&postcount=8](http://ubuntuforums.org/showpost.php?p=3163821&postcount=8)
After install, set your computer to run fusion-icon at startup.

---

### Post by ehcualp on 2007-11-14
great that worked on the mouse leaving problem, but when i change to metacity awn goes haywire and disappears. when i switch back to compiz, it reappears at the top of the screen instead of the bottom.
and i still have the problem with my keyboard and mouse combonation thing.:(

---

### Post by Stormspireiv on 2007-11-15
Yeah, AWN will go haywire and appear at the top of the screen. It will fix itself once you open a "new" window (as in not one you have set up as a launcher in awn).

I don't know about your keyboard problem though. If they are USB keyboard/mouse, try plugging them in different ports (if they are going through a hub, plug them directly into the computer).

---

### Post by ehcualp on 2007-11-15
my keyboard is ps/2. whats weird about it is if i move forwards or backwards, i can not move my mouse. If i go at an angle using two buttons or more, i can use my mouse. its stupid, it messes up game play in fast moving games.

---

