---
title: "Counter Strike/Wine resolution?"
date: 2006-06-16
forum: Wine
---

### Post by chrism66 on 2006-06-16
Ok here is my dilemma. I run my desktop at a resolution of 1280x1024. I want to play CS, DOD, etc..... at 1024x768. I have tried the launch options of -height -width, and full screen and it still comes up not a full screen, and when I close the game my desktop stays at 1024x768. Right now I need to change my desktop resolution to 1024x768 to get a full screen. Any help would be greatly appreciated.

Chris

---

### Post by eqisow on 2006-06-17
The only thing I can think of would be if you had "Virtual Desktop" Enabled in Wine. Run winecfg in a terminal window, go to the graphics tab, and make sure 'Emulate a Virtual Desktop' is unchecked.

---

### Post by Oblong_Cheese on 2006-10-14
I have the same problem, and also my main menubar at the top of the screen is visible when playing CS:S.

Hrm!

---

### Post by macabro22 on 2008-03-05
bump

---

### Post by frodon on 2008-03-05
Which version of wine are you using ? i'm using 0.9.50 with same desktop resolution and same game resolution than you and i don't have this problem.

---

### Post by Hobbez on 2008-07-18
I had a problem with the window size... It was actually a pretty easy fix so I am trying to make it more available than it was for me. 

This was a helpful solution for me. When the window is small as it is for me running compviz and dual monitors. The problem I had was cs was opening in a 800 x 600 window, and there was no option to change it in steam.

The solution is to go to wine and let it manage it’s self… I also messed with the default wine window size so it would take up the whole screen (one face of my right cube.

"
Default Re: Missing option from merge? Wine fullscreen woes :(
Quote:
Originally Posted by chuckyp
I’m assuming the plugin will hit git stream soon?
In the meantime, (in Cedega) you can untick the “Managed” option, and with most games this will work and fix this problem.
"

In wine, find where you can switch the window management style and choose for wine to manage it..

HTH
-r

Here is the forum url where I found my answer.

[http://forum.compiz-fusion.org/showthread.php?t=2507](http://forum.compiz-fusion.org/showthread.php?t=2507)

The wget for the SteamInstall.exe on
[http://thepemberton.com/posts/archives/13#comment-4635](http://thepemberton.com/posts/archives/13#comment-4635)
didn’t work for me. I searched “SteamInstall.exe” in google and found a different copy. This is the one I used, and for sheer convince I have linked it here.

SteamInstall.exe is here.
[http://www.ausgamers.com/files/details/html/10694](http://www.ausgamers.com/files/details/html/10694)

---

