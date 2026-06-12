---
title: "Wine stopped working"
date: 2008-07-15
forum: Wine
---

### Post by Markissocoollike on 2008-07-15
I don't know why but I can't seem to configure wine no more or open programs like i used to

---

### Post by Tomatz on 2008-07-15
> **Markissocoollike said:**
> I don't know why but I can't seem to configure wine no more or open programs like i used to

If you dont mind possiably loosing all your wine apps. Try this:

```
sudo apt-get remove --purge wine && sudo apt-get install wine
```

;)

---

### Post by Markissocoollike on 2008-07-15
> **Tomatz said:**
> If you dont mind possiably loosing all your wine apps. Try this:

```
sudo apt-get remove --purge wine && sudo apt-get install wine
```

;)

tried it I still can't configure wine and I still can't run windows applications what the hell? They were running normally before

---

### Post by Markissocoollike on 2008-07-15
I've tried rebooting no luck there either

---

### Post by Tomatz on 2008-07-15
> **Markissocoollike said:**
> tried it I still can't configure wine and I still can't run windows applications what the hell? They were running normally before

Open a terminal (or cd) in one of your windows apps program directory (where the .exe is located). This will be in your **home folder** in the hidden directory **.wine**.

Then run the app in the terminal like this. Obviously changing PROG-NAME for the programs name.

```
wine PROG-NAME.exe 
```

Post the output back on the froums.

---

### Post by Markissocoollike on 2008-07-15
> **Tomatz said:**
> Open a terminal (or cd) in one of your windows apps program directory (where the .exe is located). This will be in your **home folder** in the hidden directory **.wine**.

Then run the app in the terminal like this. Obviously changing PROG-NAME for the programs name.

```
wine PROG-NAME.exe 
```

Post the output back on the froums.

aha here we goes: 

```

err:winedevice:ServiceMain driver L"PenClass" failed to load
wine: could not load L"C:\\windows\\system32\\war3.exe": Module not found

```

---

### Post by Tomatz on 2008-07-15
> **Markissocoollike said:**
> aha here we goes: 

```

err:winedevice:ServiceMain driver L"PenClass" failed to load
wine: could not load L"C:\\windows\\system32\\war3.exe": Module not found

```

WOW right ;)

Try running it from the terminal like this:

```
wine war3.exe -opengl
```

P.s 

Have you changed the graphics drivers lately and or updated the system/kernel?

---

### Post by Markissocoollike on 2008-07-15
> **Tomatz said:**
> WOW right ;)

Try running it from the terminal like this:

```
wine war3.exe -opengl
```

P.s 

Have you changed the graphics drivers lately and or updated the system/kernel?

err:winedevice:ServiceMain driver L"PenClass" failed to load
wine: could not load L"C:\\windows\\system32\\war3.exe": Module not found

I dunno I think I did something to it but I don't know what exactly!

---

### Post by mc4man on 2008-07-15
if your going to run a shortened comm. like that you need your prompt to be in the dir. the exe is in, otherwise wine looks to system32, ex.
> doug@doug-desktop:~/.wine/drive_c/Program Files/ImgBurn$ wine ImgBurn.exe
from your normal prompt use wine <full path>

ex. from normal prompt
doug@doug-desktop:~$ wine '/home/doug/.wine/drive_c/Program Files/ImgBurn/ImgBurn.exe'

---

### Post by Markissocoollike on 2008-07-15
> **mc4man said:**
> if your going to run a shortened comm. like that you need your prompt to be in the dir. the exe is in, otherwise wine looks to system32, ex.

from your normal prompt use wine <full path>

ex. from normal prompt
doug@doug-desktop:~$ wine '/home/doug/.wine/drive_c/Program Files/ImgBurn/ImgBurn.exe'

says theres no such directory strange

---

### Post by Tomatz on 2008-07-15
You could try installing wine 1.0:

[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

---

### Post by Markissocoollike on 2008-07-15
> **Tomatz said:**
> You could try installing wine 1.0:

[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

it doesn't work :(

---

### Post by mc4man on 2008-07-15
@ Markissocoollike
a couple of things, If you run a command that returns an error post the command you used along with the error(s)
What ver. of ubuntu are you using
Just to see browse to places -> home folder -> .wine -> drive_c and see what's there. (enable show hidden files from view tab in home)

note ; the wine site may be down (thread from a few min. ago)

---

### Post by Markissocoollike on 2008-07-15
> **mc4man said:**
> @ Markissocoollike
a couple of things, If you run a command that returns an error post the command you used along with the error(s)
What ver. of ubuntu are you using
Just to see browse to places -> home folder -> .wine -> drive_c and see what's there. (enable show hidden files from view tab in home)

note ; the wine site may be down (thread from a few min. ago)

wheres this enable show hidden files?

---

### Post by Markissocoollike on 2008-07-15
And I'm running the lastest ubuntu

---

### Post by mc4man on 2008-07-15
> wheres this enable show hidden file
when you go places -> home folder look up in the upper task bar and click view. (if anyone tells you to open nautilus that's what they mean - home folder)

---

### Post by Markissocoollike on 2008-07-15
> **mc4man said:**
> when you go places -> home folder look up in the upper task bar and click view. (if anyone tells you to open nautilus that's what they mean - home folder)

It shows me the same directories looks like ill have to reboot the whole system to get this to work, since when has linux gotten so sensitive to what you do with it? I think this might be a bug, I guess so

---

### Post by mc4man on 2008-07-15
I'd install a newer ver. of wine, the hardy repo ver. is flawed (0.9.59)
Either add the hardy repo as instructed here 
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
or if there is some problem with adding the repo atm either wait or go here and take your pick of any of top three
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
just double click on and let GDebi deal with it.
 Uninstall wine first ```
sudo apt-get remove wine
```
probably you should use the 2nd link, and choose ver 1.0 (most stable)

---

### Post by Markissocoollike on 2008-07-15
> **mc4man said:**
> I'd install a newer ver. of wine, the hardy repo ver. is flawed (0.9.59)
Either add the hardy repo as instructed here 
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
or if there is some problem with adding the repo atm either wait or go here and take your pick of any of top three
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
just double click on and let GDebi deal with it.
 Uninstall wine first ```
sudo apt-get remove wine
```
probably you should use the 2nd link, and choose ver 1.0 (most stable)

GREAT! Unfortunatly that didn't work either guess no-one has ever come across this problem before I guess I'll have to reinstall ubuntu again

---

### Post by Tomatz on 2008-07-15
> **Markissocoollike said:**
> GREAT! Unfortunatly that didn't work either guess no-one has ever come across this problem before I guess I'll have to reinstall ubuntu again

Try installing a small windows app in wine, say utorrent. To see if it now works but needs a fresh installation of a windows app.

---

### Post by YokoZar on 2008-07-15
> **Tomatz said:**
> If you dont mind possiably loosing all your wine apps. Try this:

```
sudo apt-get remove --purge wine && sudo apt-get install wine
```

;)
This won't do anything, you need to remove your ~/.wine directory to redo the Wine installation for your home folder.  (eg, with rm -rf ~/.wine)

> **Markissocoollike said:**
> aha here we goes: 

```

err:winedevice:ServiceMain driver L"PenClass" failed to load
wine: could not load L"C:\\windows\\system32\\war3.exe": Module not found

```
That error is because the program "war3.exe" isn't in the directory you tried to run it in.  Wine then looks for it in the system folder, and doesn't find it, hence the error.

Please try again from inside the war3 directory.

---

### Post by YokoZar on 2008-07-15
> **Markissocoollike said:**
> GREAT! Unfortunatly that didn't work either guess no-one has ever come across this problem before I guess I'll have to reinstall ubuntu again
No need for that, ever.  Worst comes to worst you can delete your entire Wine folder (rm -rf ~/.wine)

---

### Post by Markissocoollike on 2008-07-16
> **YokoZar said:**
> No need for that, ever.  Worst comes to worst you can delete your entire Wine folder (rm -rf ~/.wine)

heres the funny thing I did do that and it still doesn't work lol!

---

### Post by Markissocoollike on 2008-07-16
> **YokoZar said:**
> This won't do anything, you need to remove your ~/.wine directory to redo the Wine installation for your home folder.  (eg, with rm -rf ~/.wine)


wheres the wine directory? I can't seem to find the folder for it :( I get winelists but they aint any help!


> 
That error is because the program "war3.exe" isn't in the directory you tried to run it in.  Wine then looks for it in the system folder, and doesn't find it, hence the error.

Please try again from inside the war3 directory.

That doesn't seem to work either

---

### Post by InfSauce on 2008-09-24
I'm experiencing the same problem, tried all of the above, wine wont run at all, no matter what version I install. =(

---

### Post by InfSauce on 2008-09-24
Oh woops, I take that back, 
```
rm -rf ~/.wine
```
seems to have done the trick, wine is now functioning, but it looks like I'm going to have to reinstall everything I was running with it... I'm a noooob linux user but from the looks of it, somehting in the wine directory was somehow jamming it all up.

---

### Post by YokoZar on 2008-09-25
> **Markissocoollike said:**
> wheres the wine directory? I can't seem to find the folder for it :( I get winelists but they aint any help!A folder beginning with a . is hidden by default.  You can either show hidden files in Nautilus or do ls -a in a terminal to see it.

Anyway, if Wine is acting weird and you've successfully run it once before, you most assuredly do have a ~/.wine folder.


> That doesn't seem to work eitherIf you're in the war3 directory then you're in the Wine folder too, as it's most likely installed at ~/.wine/drive_c/Program Files/Warcraft 3.

---

### Post by iluii on 2010-09-24
Alright, I know this thread is old but I need help!!
Im not a total noob to linux since I've been using it for at least 2 years but I havent had the time to really get into it and have been able sort of learn as I go. As for my problem, I was able to get C&C Generals and Zero Hour working with audio on my Xubuntu 10.04 using Wine 1.3, I own the originals but unfortunately they are halfway accross the globe from me right now so I took the install folders directly from my friend's ***doze PC and got it to work fine. Everything was going fine until one morning when the game decided to stop working, I had been fiddling with the registry a bit and had recently done an update so I attributed it to this. I purged wine deleted my .wine, reinstalled and used wincfg to create a new .wine, then I put both generals and zero hour back in into the wine c: drive and tried playing them both. Generals worked (with no audio, I guess ill have to download pulse support or use pasdp Im sure ill figure it out) but zero hour will not start any more no matter what I do, the splash screen comes up the screen goes blank and then it goes back to my desktop. I now its not a no-cd problem because my friend runs it on his ***doze pc no problem and as I mentioned before I was running his folders on my wine until recently. Ill post my terminal ouput to see if anyone can help me out since its chinese to me, please help I was in the middle of a generals challange!! BTW I tried reverting to wine 1.2 stable but didnt help

[email]francisco@francisco-laptop:~/.wine[/email]/drive_c/Program Files/EA Games/Command & Conquer Generals Zero Hour$ wine generals.exe
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1072
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1072
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1072
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1072
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1072
fixme:win:EnumDisplayDevicesW ((null),0,0x338548,0x00000000), stub!
fixme:d3d:swapchain_init The application requested more than one back buffer, this is not properly supported.
Please configure the application to use double buffering (1 back buffer) if possible.
fixme:d3d8:ValidatePixelShader (0x2ed04c8 (nil) 0 (nil)): stub
fixme:imm:ImmReleaseContext (0x10064, 0x137708): stub

---

### Post by iluii on 2010-09-25
BTW

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: IBM Device 0582
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at a0080000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at a0000000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

---

### Post by iluii on 2010-09-25
> **patice said:**
> that's right,you must stopped working after drinking wine


...insightful...

any one out there have anything relevant?

---

