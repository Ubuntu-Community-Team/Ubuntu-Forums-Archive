---
title: "World of Warcraft not working effectively for Ubuntu"
date: 2016-04-03
forum: Wine
---

### Post by armon2 on 2016-04-03
Hi, I am trying to play the online MMORPG World of Warcraft on the windows emulator Wine. However, it seems to be really laggy and when I try and open wow.exe it just opens it halfway across the screen really maxmimized with crappy grainy graphics and a bunch of lag. Also, when I try and tab shift out of the screen and re-click back to it. I am left with a half sized screen of WoW frozen and imprinted on my screen until i end up closing the application. What is going on here? ANy suggestions? I am running the latest version of Ubuntu on my envy notebook i 7 processor. 
 
 Also, as a sidenote. I have the naga gaming mouse. And I want to be able to script the two middle buttons on the middle section of the mouse to keybind to mouse button 4 and mouse button 5. However as a default they are set to mouse sensitivity increase/decrease. Is there any script I can use to do that without having razor synapse 2.0. As we know it is not compatible with linux OS... 
 
Thank you guys! Much Appreciated!!

---

### Post by alex_32 on 2016-04-03
Concerning the graphics, you can try and edit the config file so that the game uses OpenGL instead of DirectX. The config file is in your WoW directory in the [B]WTF/Config.wtf
[/B]Find the line **SET gxApi **and change it to [B]SET gxApi "opengl"

[/B]However, even if this works the graphics will not be as good as with DirectX as Blizzard does not support OpenGL as much as DirectX.

---

### Post by armon2 on 2016-04-03
How do I do that? I am new to ubuntu. Really have no clue about this, I have used windows my whole life lol. Also, when I try and run this command it says system cannot find wow.exe or whatever... 
 
__GL_THREADED_OPTIMIZATIONS=1 WINEDEBUG=-all wine wow.exe -opengl

Guessing I have to set it to opengl as u just mentioned...also I cannot find my wow directory anywhere. It is really weird but for some reason there’s virtually nothing in my home directory... 
 
Theres nothing in my .wine files that shows world of warcraft...It is the weirdest thing...

---

