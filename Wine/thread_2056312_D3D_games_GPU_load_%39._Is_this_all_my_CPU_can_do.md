---
title: "D3D games GPU load %39. Is this all my CPU can do?"
date: 2012-09-11
forum: Wine
---

### Post by nsfnd on 2012-09-11
Hello everyone.

I have a Lenovo Y560 notebook.
It has i7-740qm cpu @ 1.73Ghz (2.93Ghz with Turbo Boost but can not achieve this on linux; thx to threads jumping between cores)
And an Ati HD5730 graphics card with 1GB dedicated memory.
Also 8GB ram and a 60gb ssd.
I have Ubuntu 12.04 installed with KDE. 3.2.0-30-generic kernel.

So when i try to run a D3D game, fps is around 30. All with low settings.
I tried **Orcs Must Die, Skyrim, Dota 2, CSS, TF2.** 
(Except for League of Legends, i get 100fps on empty areas and 60fps on combat for some reason)
(All fine on Windows)
On the screen shot you can see that i set Cpu Core 2 and 3 to Steam and Dota2.(If i force only 1 core, Cpu is 2.7Ghz but all i get is 15fps)
In this case cpu frenquencies are about 2.2Ghz.
And from the **watch aticonfig --odgc** command you can see that **only %39 of GPU is used**.

So what i understand is my CPU is bottlenecking. 
My question is, do i unterstand this right? If so is there anything i can do? Is it possible to make more use of GPU?
Thx for reading and sorry for my English :)
[IMG]http://dl.dropbox.com/u/37807725/dota2-edit.jpg[/IMG]

---

### Post by amikot on 2012-09-12
I had similar problem with WOW on my desktop.
With my graphics card on windows i get more than 60FPS, on wine i have 30FPS with CPU usage around 50-70%.
Im not sure, but i think that cold be memory bandwidth problem. Maybe wine is moving or coping twice ?  Or maybe wine cant use more then one core in CPU ? using 100% of one core will be shown as 50% of a 2cores CPU  or 25%  of 4cores CPU.

PS. With latest Nvidia drivers i have really good FPS on wine, similar to result on Windows. It could be, that is not problem related to wine itself, it cold be problem with graphics drivers.

---

### Post by nsfnd on 2012-09-12
But my cpu usage is around %80 as you can see on top left corner on htop.
I have the latest fglrx ( 12.8 ) but you might be right.

---

### Post by amikot on 2012-09-13
You have 80% CPU usage but only on 2 of 4 cores.
Calculating usage on all 4 cores you have 40% CPU usage.

---

