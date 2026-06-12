---
title: "Warcraft III Frozen Throne 1.21 on lan problem"
date: 2007-11-22
forum: Wine
---

### Post by iskomazaredo on 2007-11-22
hi! i'm just trying to connect my ubuntu pc (Ubuntu 7.04) to my other lan pc (WinXP OS) to play warcraft iii (Dota) so we can play 1 vs. 1 but i'm having hardtime connecting to that pc. even vice versa. i tried to install and configure firestarter in my ubuntu unit and follow the instruction in some post but i can't make it to work up to this moment. could someone here tell me a step by step instruction so we can play it by my friends? i'm really a noob in ubuntu. i can see his network but when i join the game it stuck and nothing happen and vise versa. like when youre having a firewall in windows xp. but xp firewall is off. maybe firewall in my ubuntu is blocking our way. 

in my firestarter i did put 
Allow connections from host : workers <---this is our workgroup

Allow service: Unknown Port: 6112 For: Everyone

i just switched this unit to ubuntu a few days ago. when this is in Winxp we can play. But now not anymore. Please help me guys! thanks in advance.

---

### Post by sauronsmatrix on 2008-01-18
hey, lol i have this exact problem. trying to lan dota with my friends.


it dont work....... i know in 7.04 it worked perfectly fine, but when I upgraded to 7.10, it completely stopped working.

---

### Post by icebuxs on 2008-05-21
me too.. im having a hard time configuring my ubuntu so that it could join lan games in dota. sigh... i tried checking the iptables for blocked port and it turned out that the port we were using for dota was already open. can u guys post solutions and workarounds if theres any development on this.. tnx

---

### Post by shae on 2008-05-22
I believe the problem is caused by an incomplete feature of wine.  You should try the deb of wine patched for warcraft if you are not already using it.  It is avaliable in my PPA at: [https://launchpad.net/~starfall87/+archive](https://launchpad.net/~starfall87/+archive) or instructions on compiling it at [http://ubuntuforums.org/showthread.php?t=795714](http://ubuntuforums.org/showthread.php?t=795714)

---

