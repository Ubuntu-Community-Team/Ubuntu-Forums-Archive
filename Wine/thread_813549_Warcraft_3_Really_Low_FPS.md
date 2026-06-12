---
title: "Warcraft 3 Really Low FPS"
date: 2008-05-30
forum: Wine
---

### Post by Absurdiverse on 2008-05-30
Alright, two questions. First: I'm a complete Linux noob so be detailed and coherent please. I just installed Warcraft 3 using Wine. I'm using Wine version 1.0-rc3 and Ubuntu 8.04. I have an ATI x1650 Graphics Card. When I run Warcraft 3 it is extremely slow. My FPS has to be around 2 or 3. I'm not sure why this is. I checked WineDB and it said, in so many words, it should 'just work.'

Second: Is it true I have to turn off my Visual Effects every time I want to play a game in Wine? This is a hassle. Is there a way around it? I notice that when it is one Warcraft 3 just flashes wildly.

Thanks.

---

### Post by shae on 2008-05-31
For best fps, launch Warcraft 3 with the -opengl launch option like this:
```
WINEDEBUG=-all wine /path/to/warcraft/warcraft_exe_name.exe -opengl
```

Yes if you are experiencing FPS problems you should turn off compiz for gaming.  You should look into using fusion-icon or compiz-switch to switch easily between the two for gaming sessions.  Also check out my PPA which has wine build with a patch to allow hosting and loss-of-focus at
[https://launchpad.net/~starfall87/+archive](https://launchpad.net/~starfall87/+archive)

---

### Post by domagoj91 on 2009-12-06
> **shae said:**
> For best fps, launch Warcraft 3 with the -opengl launch option like this:
```
WINEDEBUG=-all wine /path/to/warcraft/warcraft_exe_name.exe -opengl
```

Yes if you are experiencing FPS problems you should turn off compiz for gaming.  You should look into using fusion-icon or compiz-switch to switch easily between the two for gaming sessions.  Also check out my PPA which has wine build with a patch to allow hosting and loss-of-focus at
[https://launchpad.net/~starfall87/+archive](https://launchpad.net/~starfall87/+archive)

I've got the same problem but there is no change when i start it whit this code.

---

### Post by beastrace91 on 2009-12-06
Have you tried upgrading your Wine version? Alot of time this gives performance increases.

Regards,
~Jeff

---

### Post by leveliv on 2009-12-07
I get pretty normal FPS on my box. I close things like Docky and stuff but other than that they are okay. What card are you using? 

and make sure it uses opengl like someone said. come to think of it, I should actually start using opengl ...Also curious, Do you play online?

---

