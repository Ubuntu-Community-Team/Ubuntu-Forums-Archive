---
title: "Two quickies ..."
date: 2006-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by wannabelinuxconvert on 2006-01-22
Hi,

I have two quick questions I'm hoping you can answer ...

1/ I ran the command glxgears as this is supposed to be a good test to see if your graphics card is running right. I got this from the lastest issue of 'Linux Formt' and it quotes that it should print a FPS rate to the terminal every five seconds so you can check it against the benchmarks for your system. Except mine doesn't do this, it's displays the gears, but that's all. Is this normal on PPC architecture !? Is there any other way to check if the cards working right !? The reason I ask this is sometimes my screen gets a bit slugish and you can see where you've dragged windows from etc while there being redrawn ... and also when I boot up, there are three errors just before the login screen appears, and one of them mentions the word 'radeon' and mine is the in-built readeon of the mac-mini.

2/ I have successfully configured my USB wireless card throught the networking app from the SYSTEM -> ADMINISTRATION menu but sometimes when I boot up it's working, and other times I have to go into the Network settings and activate the thing. Is there anyway I can get the card to start everytime I boot as this can be quite tedious !? Maybe some file I can edit manually ?!

Cheers

Mic

(Oh and keep an eye out for a how-to I'm putting together on getting Apache2, MySQL, Java1.5, Tomcat5, PHP5 and RubyOnRails all working seemlessy on the same machine using Apache's virtual hosts and proxy-redirection :D )

---

### Post by codejunkie on 2006-01-28
[QUOTE=wannabelinuxconvert]Hi,

I have two quick questions I'm hoping you can answer ...

1/ I ran the command glxgears as this is supposed to be a good test to see if your graphics card is running right. I got this from the lastest issue of 'Linux Formt' and it quotes that it should print a FPS rate to the terminal every five seconds so you can check it against the benchmarks for your system. Except mine doesn't do this, it's displays the gears, but that's all. Is this normal on PPC architecture !? Is there any other way to check if the cards working right !? The reason I ask this is sometimes my screen gets a bit slugish and you can see where you've dragged windows from etc while there being redrawn ... and also when I boot up, there are three errors just before the login screen appears, and one of them mentions the word 'radeon' and mine is the in-built readeon of the mac-mini.

2/ I have successfully configured my USB wireless card throught the networking app from the SYSTEM -> ADMINISTRATION menu but sometimes when I boot up it's working, and other times I have to go into the Network settings and activate the thing. Is there anyway I can get the card to start everytime I boot as this can be quite tedious !? Maybe some file I can edit manually ?!

Cheers

Mic

(Oh and keep an eye out for a how-to I'm putting together on getting Apache2, MySQL, Java1.5, Tomcat5, PHP5 and RubyOnRails all working seemlessy on the same machine using Apache's virtual hosts and proxy-redirection :D )[/QUOTE]
dont know about the wireless issue but to fix the glx gears problem run 
```
sudo gedit /etc/bash.bashrc
```
and add 
```
alias glxgears='glxgears -printfps'
```
to the bottom of the file, save and exit and close all open terminals then fire up a terminal and try it again it should output the frames per second.

---

