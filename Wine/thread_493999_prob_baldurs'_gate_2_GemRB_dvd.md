---
title: "prob: baldurs' gate 2 GemRB dvd"
date: 2007-07-06
forum: Wine
---

### Post by don durito on 2007-07-06
Hi,

I have just bough an dvd version of Balurs Gate 2 and i downloaded and installed Gemrb from [www.liflg.org](www.liflg.org). after this i runned the baldurs's gate 2 installer with sh bal...
Everything worked and the installer nearly finished. but when i reach neraly 100 percent of the installatoin the installer asks me to mount the 2nd cd. 
But i don't have a 2nd cd so i tried to unmount and remount my dvd, but this won't help.

So does anyone have a clue how i can install baldur's gate 2 dvd version using gemrb..

thanks

don

p.s.: i am using xubuntu 7.04 the latest wine version on an thinkpad x31

---

### Post by don durito on 2007-07-06
hey

i know that i am flooding this thread but i just want to tell you what i did in the meanwhile.
first i removed and reinstalled GemRB, then i tried to reinstall Baldur's Gate II via the GemRB installer from loki, but i still get the same error.
after ths i searched various threads through the web and realized the the dvd installer is on the way but not yet realesed. 
so i tried to install Baldur's Gate II via wine, cause some suse and gentoo users gave it gold satues. 
I was able to install it and configured it via winecfg. I can start the game but after it starts the sound failes. And i still had my xorg cursor in the game.(its like one of those cursor widgets where ther cursor is chased by some stars or something, in my case its the knights glove which follows the xorg.cursor)
I was able to create a carrecter and start the first level but when it came to the first dialog. I wasn't able to select one of my answers neiter with the numbers on the keyboard nor with my double cursor. (the dialog is the first time when the game gives the palyer controll so i believe i can't even controll the game). And i wasn't abel to start the menu. the esc key didn't react.
so i had to kill my x window system by pressing strg+alt+backspace. (i know that i could kill the process using strg-alt-f1);

But even worse is that wine made some sort of entry in my Xorg Menu but i can't find the .desktop file in the /usr/share/applications directory; so i can't remove this whole enty (which sucks by the way). And ofcourse i unistalled Baldur's Gate II via wine and removed the baldur.exe from the winecfg.

I am realy frustarted by now cause all i wanted is to play this oldy but goldy on my favorite distro.

So please guys/girls i even don't care anymore about GemRB i just want to play this game and if anyone can send me some sort of how-to how he or she was able to play this game this would be perfectly fine to me. 
(i know that i should start an new thread for some kind of how to) But if we are able to create some sort of solution i will write a how-to.

thanks
and realy pissed don

p.s: a attached picture of my GemRB problem... 
p.p.s: a picture of my xorg menu entry problem (which realy sucks)...

---

### Post by LasTSuRvivoR on 2008-01-20
I compiled & installed gemrb

I have BG2 on my Win partition.

When i try to start gemrb by  typing 

./gemrb

It checks some things and says OK OK OK OK than this error is found.

[KEYImporter]: Opening chitin.key...[ERROR]
[KEYImporter]: Cannot open Chitin.key
[ERROR]
Cannot Load Chitin.key
Termination in Progress...

WTF wit this ??

---

### Post by MaximB on 2008-01-20
Baldur's Gate 2 can work natively on Linux ?

---

### Post by jeffus_il on 2008-01-20
They're using wine and the loki installer, not native Linux software.

---

### Post by MaximB on 2008-01-20
yeah but loki is like natively , I mean it runs games that support Linux like sam and NWN , it's not like wine which is other story.

---

### Post by jeffus_il on 2008-01-20
Loki installs windows executable code, they normally require that you have the original windows disk or a reasonable theft thereof.
Install it and run it, tell me what you have.

---

### Post by fuag155555 on 2008-03-20
I have a linux game dude. They don't use windows binaries, they might get at the information in a way thats not an official installer, of course they ask for the windows cd, they need the game content such as models textures and sounds.

---

### Post by Melcar on 2008-03-20
If you're running BG2 with Wine:

- Game does not work on my 64bit systems (video is corrupted)
- Game suffers from "soft locks" from time to time (usually when you're messing around on the inventory screen); this can be somewhat resolved by using 800x600 resolution
- Sound in game will die out randomly
- 3D acceleration works, but can cause slowdowns with certain effects
- Game does not like ATI cards; this is true even under Windows, but I think in Linux it's more of a Wine vs. ATI thing (it's a know fact that those two don't go well together).

---

