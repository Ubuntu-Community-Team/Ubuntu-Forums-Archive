---
title: "Using WINE and runnning games"
date: 2007-12-29
forum: Wine
---

### Post by mongoose_za on 2007-12-29
Hi there,

Just looking for the most basic way to run a game like Quake III and Warcraft 3 using WINE.
I have WINE and the 2games on my machine. (neither were installed but directly copied from my windows machine)
Now what? Must i goto terminal then try wine "quake.exe "? Itried something like that but it wouldn't work anyway.
I'm not to sure on the steps starting off. Just need to see once and i should be ok :)

---

### Post by Crumpets and Jam on 2007-12-29
> **mongoose_za said:**
> Hi there,

Just looking for the most basic way to run a game like Quake III and Warcraft 3 using WINE.
I have WINE and the 2games on my machine. (neither were installed but directly copied from my windows machine)
Now what? Must i goto terminal then try wine "quake.exe "? Itried something like that but it wouldn't work anyway.
I'm not to sure on the steps starting off. Just need to see once and i should be ok :)

I think everything you need to know is listed in the Community Documentation [here]("https://help.ubuntu.com/community/Wine").

---

### Post by mongoose_za on 2007-12-29
thanks man..

---

### Post by b0rka7a on 2007-12-29
There is a Quake III Linux, so you don't need to emulate the Windows version ;).

---

### Post by mongoose_za on 2007-12-30
yeh maybe i should just get the linux Q3 cause i can't get WINE to work these properly. Thought the guide woulda helped but it's just not happening over here. Losing faith here.... maybe making my linux looks nice like yours might help my enthusiasm.

---

### Post by raddellee on 2007-12-30
If you are new at using wine go to winehq or Wine-wiki.org. those web sites helped me. It all about getting files from system 32 (windows partition) and putting them in wine's system 32 

E.g.

Warcraft 3

 to install all you need is msvcrt.dll in 
/home/(user name)/.wine/drive_c/windows/system32

Install game by right clicking install.exe and opening with wine

then install 1.12 patch and crack

then in wine config applications add war3 and make its default version windows NT 4

Then rename the movie files

Then play

I am assuming that you are using wine version 9.50 (not that it should make a difference)

Anyway hope it helps

---

### Post by chessercizes on 2007-12-30
warcraft 3 works really nicely in wine. the only thing is that it doesn't play movies well, so you should probably rename the movies folder to moviez or something.

oh, and you might know this already, but when running warcraft 3, it works waay better in opengl, i.e.

cd to your directory and then
```
wine <warcraft3file> -opengl
```

this has been working for me at least

gl with getting them to work

---

### Post by mongoose_za on 2008-01-02
HEY THERE,

does it have to be patch 1.12 or can i use the latest one?

and when you say "wine <warcraft3file> -opengl" what warcraft3file are you talkign about? the exe? If so will it work with The Frozen Throne too?

---

### Post by mongoose_za on 2008-01-02
ok the install worked and i've patched it to 1.21.
However you told me to cd to the installed dir. That doesn't work. In terminal i type "cd /home/darren/Program Files/Warcraft III" but then it replies "No Such File or Directory" ???Something to do with the spaces? But if i rename the files to have to spaces like ProgramFiles/WarcraftIII won't it mess up my WINE config?

---

### Post by mongoose_za on 2008-01-02
IT STARTED UP!!! WOW IT'S SO COOL THAT IS STARTED!!!

[COLOR="Red"]BUT[/COLOR]

I't slower then a m#$*&^ F@#*&.. i can't even properly click the menu it's so slow.

I cd to my dir then typed wine war3.exe -opengl
 i got this 
  darren@UBUNTU:~/Program_Files/Warcraft_III$ wine war3.exe -opengl
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34f3d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f67c,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x30024, (nil), 16): stub

So it started but it's to slow to run. Must be something not right perhaps with the drivers or opengl... i used ENVY to install my drivers so they should be fine... any ideas?

I just went into my X11 conf to check what Graphics Card is being used my the machine and it gave me this Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"

Probably means that the drivers aren't installed correctly right? Probably why Wc3 is running so slow right?

Well i reinstalled my card and i still have the same problem. So strange when i just don't know. Haven't felt this way since Windows95 :D

---

### Post by raddellee on 2008-01-02
My warcraft 3 installation runs a bit slow as well. Did you make war3.exe default wine engine windows xp. that made mine run a bit faster. also if you install frozen throne it is put in the same directory as warcraft 3 the original mucking up the no cd crack i fixed it buy updating frozen throne to 1.12. 


Also it doesn't have to be updated to 1.12 but if you use a later version you will have to use a suitable crack.

---

### Post by vexorian on 2008-01-03
To me war3 runs faster in WINE than XP (mostly because of -opengl I think)

I think you should double check some things, like for example, do you have a good driver for your graphic card?

---

### Post by mongoose_za on 2008-01-03
for sure it's an opengl problem
it can only run this slow because of something like that..
i'm using the ati-driver-installer-8.443.1-x86.x86_64 drivers.
I'm not sure what else to do really... it's to slow to play. Either a problem configuring the actualy Graphics card or within WINE itself. I did remember seeing people saying that one should change the D3D registery in WINE but when i went there i noticed that my registry doesn't even have that registry key..

---

