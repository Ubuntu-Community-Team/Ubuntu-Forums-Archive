---
title: "Dwarf fortress help"
date: 2008-10-14
forum: Wine
---

### Post by tsktac on 2008-10-14
Hi everyone I'm a bit of a newb with Ubuntu and I have a problem with dwarf fortress.  I have played the game on this computer using windows and it worked perfectly.  After I installed Ubuntu I installed wine because the dwarf fortress wiki said it would work with using that program.  I don't know if I installed wine right or if I missed some special Ubuntu installation step with the game but it's not working.
  It reacts normally when I click it by asking if I want to use full screen or not, but it only displays a blank screen and a slow startup song.  The rest of the music is in good tempo but I can't see the blocky graphics that usually greets me to every game.  Please help, this month are the longest I've ever gone without this game, and I need to be able to play before the next big update.

P.s. This is my first post.

---

### Post by david_kt on 2008-10-15
> **tsktac said:**
> Hi everyone I'm a bit of a newb with Ubuntu and I have a problem with dwarf fortress.  
P.s. This is my first post.

See last post of below thread:

[http://ubuntuforums.org/showthread.php?t=533013](http://ubuntuforums.org/showthread.php?t=533013)


DK

---

### Post by tsktac on 2008-10-15
I searched through the forums first and found that thread but it didn't help.  The game starts just fine but I can't see the screen, I can only hear the music.
  Would this have to do with video drivers?  I have Nvidia and I haven't upgraded the drivers since I switched to Ubuntu.

---

### Post by david_kt on 2008-10-15
> **tsktac said:**
> Would this have to do with video drivers?  I have Nvidia and I haven't upgraded the drivers since I switched to Ubuntu.

Most likely yes. Try:

System > Administration > Hardware Drivers

DK

---

### Post by tsktac on 2008-10-15
I have tried enabling the driver but the weird thing was... it was already enabled.  To make sure I turned the desktop graphics on high and it worked fine.,
  I don't know what to do from here, should I just stick to playing games and windows applications on a different computer?  Or do you think it is a fixable problem?
P.s. Sorry if this post dosn't give much info I'm in the middle of a pretty bad fever.

---

### Post by david_kt on 2008-10-15
> **tsktac said:**
> I have tried enabling the driver but the weird thing was... it was already enabled.  To make sure I turned the desktop graphics on high and it worked fine.,
  I don't know what to do from here, should I just stick to playing games and windows applications on a different computer?  Or do you think it is a fixable problem?
P.s. Sorry if this post dosn't give much info I'm in the middle of a pretty bad fever.

Please write again when you get well, I subscribe to this thread so that as and when you reply I will receive a notification in my email.

For Nvidia driver it should work. What you could do is try:

```
glxinfo | grep render
```

and paste the output here.

Get well soon.
DK

---

### Post by tsktac on 2008-10-17
Thanks, I ran the command in terminal and I got this output.
-----direct rendering: Yes
-----OpenGL renderer string: GeForce4 MX Integrated GPU/AGP/SSE/3DNOW!
  Earlier today I found another game by Bay 12(The people who made dwarf fort.)and on it's wiki it says to use wineconsole and back end curses.  It gave a link to [http://winehq.org/site/docs/wineusr-guide/cui-programs]("http://winehq.org/site/docs/wineusr-guide/cui-programs"), and from this it said you have to execute a special command for console user interfaces.  I think this might work, but I don't know how to add a curses backend.
  Do you think this would work?

---

### Post by david_kt on 2008-10-18
> **tsktac said:**
> Thanks, I ran the command in terminal and I got this output.
-----direct rendering: Yes
-----OpenGL renderer string: GeForce4 MX Integrated GPU/AGP/SSE/3DNOW!

Are able to enable compiz? If yes, then your card driver is ok. Then try disabling compiz, and try again to launch your game.

> **tsktac said:**
> 
  Earlier today I found another game by Bay 12(The people who made dwarf fort.)and on it's wiki it says to use wineconsole and back end curses.  It gave a link to [http://winehq.org/site/docs/wineusr-guide/cui-programs]("http://winehq.org/site/docs/wineusr-guide/cui-programs"), and from this it said you have to execute a special command for console user interfaces.  I think this might work, but I don't know how to add a curses backend.
  Do you think this would work?

It might work, not sure though. What you could do is:

1. Open terminal and go to the games directory:
```
cd ~/dwarfort

```

To run normal wine, just run wine dwarfort.exe. But according to the link you give, instead of wine dwarfort.exe, you should run:


```
wineconsole dwarfort.exe
```

or```


wineconsole --backend=curses dwarfort.exe
```

or 

```

wineconsole --backend=user dwarfort.exe
```

You might need to replace user with actual user (I am not sure, just give it a try).

DK

---

### Post by tsktac on 2008-10-18
*Warning long post*
I tried tried the backend commands and all I got was a whole bunch of errors and fixmes.  Some of these have to do with an external hard drive I'm  using, but is not plugged in. This is the output from curses...(longest)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MFC80U.DLL (which is needed by L"C:\\Program Files\\Maxtor\\Sync\\DRVIFNT.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Maxtor\\Sync\\DRVIFNT.dll") not found
err:module:import_dll Library DRVIFNT.dll (which is needed by L"C:\\Program Files\\Maxtor\\Sync\\SyncServices.exe") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"C:\\Program Files\\Maxtor\\Sync\\SyncServices.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Maxtor\\Sync\\SyncServices.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Maxtor\\Sync\\SyncServices.exe" failed, status c0000135
And the game started as usual with no graphics.
This is the output from user (the word user not the actual user)
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1340c8,0x134768): stub
It started a window called Df then opened another window of the visual deficient game.
When I tried to use the actual user name it said command not known, so I'm guessing your supposed to use the word user.
*I hope this helps*
Why are there smilies?

---

### Post by david_kt on 2008-10-18
> **tsktac said:**
> 
*I hope this helps*
Why are there smilies?

The smileys are semi colon and ) put together. Enclose your output with [ CODE ][ /CODE ]to avoid smileys and make it easier to read. Just click on the # before you paste the output.

Looks like the wineconsole is not the way to go, but to examine your card driver. You should check whether or not you could enable compiz. If it could not enable, you have to troubleshoot it first. This is the only way I know to make sure the card driver is ready for wine.

May be try below:
```
sudo apt-get install nvidia-glx-legacy
sudo apt-get install nvidia-settings
gksudo nvidia-settings
```

After you could enable compiz, disable it before you launch you program.

If you could not enable compiz, you might need to buy supported video card. Intel chipset is a safe bet.

DK

---

### Post by Tulth on 2008-10-27
I run dorf fortress under wine, and every time I have had a problem with the tiles not drawing at all, it has turned out the game has been unable to access/find my tilesets.  Most typically this happens to me when I'm trying to upgrade to the newest DF version.

If I were you, I would make sure that the game is referencing the correct tilesets in your config files, that the tileset files exist, and that they are readable by the DF executable.  You might also try starting DF from the command line in the DF folder to make sure that DF is starting in the correct working directory.

---

