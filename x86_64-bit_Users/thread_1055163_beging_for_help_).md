---
title: "beging for help :)"
date: 2009-01-30
forum: x86 64-bit Users
---

### Post by Bellatox on 2009-01-30
Hi, i am new on linux and so i ain't much of a linux user, therefor i got problems, with lets say drivers :)
since linux drivers are much more complicated then xp ones i'd need help with this :( i tried some guides but no use i'mma lost case :P

 anyhow... i am using toshiba satelite L300-17L with kubuntu 8.10
and i ain't got no sound ...
so sound drivers are main problem , 2nd thing is that i need wireless and that requires drivers too
and 3rd less important is display, don't need this for college things but i need it for relaxation, wow + anime :P

that ofc is 64 bit OS, so i dunno really if it makes thing worser 

so if any1 got sum time to help me out i'd be greatfull for like forever ^_^

---

### Post by cariboo on 2009-01-30
It would help if you told us what sound, wireless and video adapters you have. Drivers are way less complicated then Windows, as most of them are included in the kernel.

Could open a Applications--Accessories--Terminal and type:

```
lspci
```

The above command will give a listing of your hardware. Paste the output in your next post. Please enclose the output in the [noparse]```

```[/noparse] tags. 

To copy and paste from a terminal, simply highlight the text, then to paste if you have a wheel mouse, press the wheel. If you don't have a wheel mouse, press both mouse buttons at once.

Jim

---

### Post by Bellatox on 2009-01-30
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```


```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```


and 

```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

guessing thats what u need :P

EDIT: sorry, forgot code thingys :P

---

### Post by cariboo on 2009-01-30
All your intel devices should run out of the box. Double-click on the speaker icon this should bring up a mixer, make sure that all the controls are turned up. Right-click on the network icon and you should see all available wireless networks.

There is a reolution setting utility in the control center.

Jim

---

### Post by Bellatox on 2009-01-30
yep got sound working, i guess i assumed it doesent, volume was up but it wasnt saying nuthin :P

about wireess i can check Monday, but on ubuntu didnt work 

and i would still like to get better driver for gpu, i got xp on same lap and xp has like 15x better picture then this...
i setupd resolution and stuff

---

### Post by Bellatox on 2009-02-01
ehh i still have crappy image :S there must be a way to improve this ...

---

### Post by Bölvaður on 2009-02-01
What graphic card do you have?

---

### Post by Bellatox on 2009-02-01
> **Bellatox said:**
> ```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```

i tought i said it :P

---

### Post by Uubnewb on 2009-02-01
I don't know if you tried this allready but go to Settings>Administration, here you will find a link (ie nVidia or Radeon etc) to advanged settings for your card.

---

### Post by Bellatox on 2009-02-01
> **Uubnewb said:**
> I don't know if you tried this allready but go to Settings>Administration, here you will find a link (ie nVidia or Radeon etc) to advanged settings for your card.

i aint got administration in settings

---

### Post by cariboo on 2009-02-01
There are no extra settings for Intel cards, the only thing you can set is resolution. I haven't tried it, but I see there is an Intelfb driver in the /lib/modules. 

I've got a 82945G/GZ on my Intel Atom powered media center, running glxgears I get about 300FPS at a resolution of 1360X768 on my 32" HD LCD TV.

Jim

---

