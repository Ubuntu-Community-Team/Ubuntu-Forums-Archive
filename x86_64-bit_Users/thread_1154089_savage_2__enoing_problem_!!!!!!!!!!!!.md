---
title: "savage 2  enoing problem !!!!!!!!!!!!"
date: 2009-05-09
forum: x86 64-bit Users
---

### Post by narrowonflow on 2009-05-09
i installed it whit no problems everything rolled smooth but as soon as i click on the launch icon(on the games drawer) the screen just blinks (black) as if it was going to start but then NOTHING heppends ... wut did i do wrong ?? this is my cup of ubuntu allright ... but i choked on a big seed (4 me @ least) lol ....  plz help
thanx in advance

---

### Post by Triptol on 2009-05-09
You might want to start a terminal and then start the game by entering its name (I guess that would be savage or savage2).

You will probably be presented with the same effect (screen turns black). But, you will probably also have some information on your terminal (gterm, or konsole).

This info might be helpful in finding the problem.

If you have found some more info, your best bet is to post it on the savage forums (if they have them), since you probably have a problem with the game, not with ubuntu.

---

### Post by Lithumian on 2009-05-09
I also have the same problem. It blinks black and quits on its own. Turned off Compiz/desktop effects but doesn't do anything. Playing the editor or model viewer doesn't do anything either.

---

### Post by narrowonflow on 2009-05-10
hav u posted ne threads n where else ??? or hav u ever read about some1 else with the same problem ??

---

### Post by narrowonflow on 2009-05-10
n also i noticed that after i uninstall it it still leavs some files from the savage ... after that i tryd to  force rm but  i still hav some savage files left behind ... do u think that has nething to do whit it no working ??? i would delete th e files manualy but im afraid im gonna delete something inportant... maybe if i could delete everything n install a clean copy it might solve my prob ??

---

### Post by narrowonflow on 2009-05-10
i foud out wut seems to b the problem ... whren i tried to run it from the trminal b4 it wouldnt telme anything bout the prob ... but now after uninstalling n re-intalling a couple hudred times i finaly gave me an error 
```
narrowonflow@narrowonflow:~$ /home/narrowonflow/Savage2/savage2.bin
Savage2 - Fatal Error: OpenGL 2.1 not available.
narrowonflow@narrowonflow:~$ 

```
but u c .... i hav the latest proprietary drivers for my card witch is thwe 180 nvidia ( the card is 9800 gt 1gb oc )

---

### Post by Triptol on 2009-05-11
What is the output of:
```
glxinfo | grep rendering
```
If you don't see the line below:
```
direct rendering: Yes
```
Your opengl is actually not working.

---

### Post by narrowonflow on 2009-05-28
i dont i fixed it :) thanx 4 ur help

---

