---
title: "problems to install directx 9 in ubuntu 8.04"
date: 2008-06-16
forum: Wine
---

### Post by leobap on 2008-06-16
Hi,

I'm new here and I have problems to install the directx 9 in Ubuntu 8.04.

The wine were installed correctly and I follow the below link to install the directx:

[http://www.guiaubuntupt.org/wiki/index.php?title=Directx9_no_wine_em_Ubuntu](http://www.guiaubuntupt.org/wiki/index.php?title=Directx9_no_wine_em_Ubuntu)

But in last step, after the command 

#  wine DXSETUP.EXE

The dxdiag.exe is not created!

Can anybody help me to fiz this problem??

---

### Post by cogadh on 2008-06-16
You don't need to install DirectX in Wine, it already has DirectX. At most, you might need to manually copy and override a few DirectX DLL files with a few games, but those are pretty rare.

---

### Post by thisiam on 2008-06-16
I thought the idea of linux was to not use windows only software, openGL i belive is the linux version of DirectX right?
from what i have read other people do is dual boot windows and stick with windows software there. wine is a bitch to install stuff with and there is always a linux alternative.

---

### Post by cogadh on 2008-06-16
That is not the point of Linux, the point of Linux is the ability to choose how you want to use your PC. If you want to choose to use Windows only software, there is nothing wrong with that. 

OpenGL is not the "Linux version" of anything, it is an graphics open standard that will run on Linux, Windows, Mac, PlayStation, Xbox... pretty much anything that can do graphical rendering. 

Many people do dual-boot (I do) but that is not the only option out there, if you want or need to run Windows only software.

Wine is not difficult to use at all, if you take your time with it and don't have unreasonably high expectations of it. 

There is almost never a Linux alternative when it comes to commercial games.

BTW - Why would you post something that seems so "anti-Wine" in the Wine forums?

---

### Post by thisiam on 2008-06-16
I agree that you can use any software that you want and set up your box how you wish but windows games on linux never seem to work as good as they would on windows and i would rather play games natively and enjoy the game rather than have to use emulators that do mess up, and installing games through wine doesn't seem to be a newbie thing to do.

Edit: haha i didn't even realize this was in wine area, i was browsing all new post.

---

### Post by cogadh on 2008-06-16
First off, **W**ine **I**s **N**ot an **E**mulator.

You are right, some Windows games don't work as well in Wine as they would natively, but not all of them. Some games actually work better in Wine than they do in Windows. If you would rather play games natively, that is your choice, but not eveyone is going to make that same choice. 

Installing games through Wine is probably not really a "newbie thing" to do, but how is a newbie ever going to be more than a newbie if they don't try to do some more advanced things? Instead of discouraging the use of more advanced functions in Linux (Wine isn't really all that advanced), we should encourage it by giving new users the necessary instruction to use those functions properly, rather then saying "Oh, that's going to be too hard for you, you shouldn't do that."

---

### Post by stchman on 2008-06-16
> **thisiam said:**
> I thought the idea of linux was to not use windows only software, openGL i belive is the linux version of DirectX right?
from what i have read other people do is dual boot windows and stick with windows software there. wine is a bitch to install stuff with and there is always a linux alternative.

OpenGL is another method of doing 3D acclereation via hardware.  DirecX is Microsoft's proprietary 3D rendering system.

Linux uses a 3D acceleraration called Mesa.  It is pretty close to OpenGL.  If proprietary drivers from Nvidia or ATI use OpenGL over Mesa.

OpenGL came before DirecX.

---

### Post by leobap on 2008-06-16
Thanks for help. I will search for a tutorial about wine and try to configure it. 

Don't know wine has your own directx.

---

### Post by omgirc on 2008-10-26
so am i missing the actual answer?

i followed the directions, copied the dll's recomended and downloaded the exe to install directx went thru all that and ended up with the same problem. dxdiag.exe not found.
Would have been helpful if the web page was in a language i could understand, but hey, gotta try it. Had lots of neat pictures.

Now, can anyone help with dx files? anything would be nice as we have already had the discussion about linux Vs m$.:lolflag:

---

### Post by hikaricore on 2008-10-26
You did indeed miss the answer.

You can't install DirectX under WINE and exprect it to do anything.
WINE already has an implementation of the DX libraries installing DX
in most cases will just make a bigger mess of things.

---

