---
title: "Call Of Duty 4 Startup error [wine 0.9.49]"
date: 2007-11-13
forum: Wine
---

### Post by SM0k3 on 2007-11-13
```
err:module:import_dll Library D3DX9_34.DLL (which is needed by L"C:\\Program Files\\Activision\\Call of Duty 4 - Modern Warfare\\iw3sp.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Activision\\Call of Duty 4 - Modern Warfare\\iw3sp.exe" failed, status c0000135

```

I get this when I try to run COD4 anyone know how to fix it? this is also while using a No-CD crack.

---

### Post by cogadh on 2007-11-13
Well, the first part of that error is easy to solve. There are a few native DirectX DLL files that you can add to your Wine directory without hurting Wine's implementation of DirectX:
[LIST]
[*]d3dx9_24.dll through d3dx9_35.dll (12 separate files)
[*]d3dx10_33.dll through d3dx10_35.dll (3 separate files)
[/LIST]
You can copy all of them from an existing Windows installation (all are found in C:\windows\system32), if you have one available to you. Otherwise, try Googling for them, you might be able to download them.

Place them in ~/.wine/drive_c/windows/system32, then run winecfg and add a DLL override in the Libraries tab for each file. They are not part of the drop-down list of available overrides, but you can just manually type the names in. Set each override to native only (there is no built-in equivalent for them, so why leave that option?).

After setting all the overrides, try running the game again. The first error should go away and may allow the game to proceed past the second error as well.

---

### Post by SM0k3 on 2007-11-14
> **cogadh said:**
> Well, the first part of that error is easy to solve. There are a few native DirectX DLL files that you can add to your Wine directory without hurting Wine's implementation of DirectX:
[LIST]
[*]d3dx9_24.dll through d3dx9_35.dll (12 separate files)
[*]d3dx10_33.dll through d3dx10_35.dll (3 separate files)
[/LIST]
You can copy all of them from an existing Windows installation (all are found in C:\windows\system32), if you have one available to you. Otherwise, try Googling for them, you might be able to download them.

Place them in ~/.wine/drive_c/windows/system32, then run winecfg and add a DLL override in the Libraries tab for each file. They are not part of the drop-down list of available overrides, but you can just manually type the names in. Set each override to native only (there is no built-in equivalent for them, so why leave that option?).

After setting all the overrides, try running the game again. The first error should go away and may allow the game to proceed past the second error as well.

Thanks for replying, I found all those DLL's from [this site](http://www.m3fe.com/760/) since I didn't have a windows installation handy, however I did run into another problem which is kind of similar to to the errors I get from COD2.

screenshot attached.

---

### Post by cogadh on 2007-11-14
When you run the game, use the terminal and make sure you change directories to the game's install directory first, then "wine" the executable:
```
cd .wine/drive_c/Program\ Files/<CoD4 directory>
wine <CoD4 executable>.exe
```
That should avoid the whole "run in the correct folder" problem.

---

### Post by SM0k3 on 2007-11-14
This is what I get when I run COD2, I think the errors are similar. Looks like the directories aren't setup correctly but I don't even think I have those folders that it's looking for.

---

### Post by cogadh on 2007-11-14
Same solution:
```
cd .wine/drive_c/Program\ Files/<CoD2 directory>
wine <CoD2 executable>.exe
```

---

### Post by SM0k3 on 2007-11-14
> **cogadh said:**
> Same solution:
```
cd .wine/drive_c/Program\ Files/<CoD2 directory>
wine <CoD2 executable>.exe
```

I got to the splash screen! lol but I got a C++ error......

Edit: COD2 works though using that method. Thanks

---

### Post by cogadh on 2007-11-14
This is a *really* long shot, but you might try installing the MS Visual C++ Runtime package in Wine:
[http://www.microsoft.com/downloads/details.aspx?familyid=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displaylang=en)
I've never tried this myself, but it could work (maybe).

---

### Post by SM0k3 on 2007-11-14
> **cogadh said:**
> This is a *really* long shot, but you might try installing the MS Visual C++ Runtime package in Wine:
[http://www.microsoft.com/downloads/details.aspx?familyid=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displaylang=en)
I've never tried this myself, but it could work (maybe).

Nope, didn't work :(

---

### Post by cogadh on 2007-11-14
Like I said, it was a long shot. 

Just for giggles, I checked the Activision support site to see if there was anything in their answers DB that might apply to that error occurring in Windows. There was nothing that specifically related to CoD4, but apparently C++ runtime errors are quite common in Activision games. I found entries for errors of that type related to over a dozen different games. All of them have the same solution "update your sound and video drivers". Obviously that won't work with Wine, but you could try making adjustments to the sound driver settings in winecfg (try with and without emulation, change the hardware acceleration settings, etc.).

---

### Post by SM0k3 on 2007-11-14
> **cogadh said:**
> Like I said, it was a long shot. 

Just for giggles, I checked the Activision support site to see if there was anything in their answers DB that might apply to that error occurring in Windows. There was nothing that specifically related to CoD4, but apparently C++ runtime errors are quite common in Activision games. I found entries for errors of that type related to over a dozen different games. All of them have the same solution "update your sound and video drivers". Obviously that won't work with Wine, but you could try making adjustments to the sound driver settings in winecfg (try with and without emulation, change the hardware acceleration settings, etc.).


Will do, actually I've already start tweaking around with a few settings if I come up with anything I'll post the solution in this thread. Thanks again for your help at least I'm able to play COD2 now. :lolflag:

---

### Post by gorara on 2007-11-14
> **cogadh said:**
> Well, the first part of that error is easy to solve. There are a few native DirectX DLL files that you can add to your Wine directory without hurting Wine's implementation of DirectX:
[LIST]
[*]d3dx9_24.dll through d3dx9_35.dll (12 separate files)
[*]d3dx10_33.dll through d3dx10_35.dll (3 separate files)
[/LIST]
You can copy all of them from an existing Windows installation (all are found in C:\windows\system32), if you have one available to you. Otherwise, try Googling for them, you might be able to download them.

Place them in ~/.wine/drive_c/windows/system32, then run winecfg and add a DLL override in the Libraries tab for each file. They are not part of the drop-down list of available overrides, but you can just manually type the names in. Set each override to native only (there is no built-in equivalent for them, so why leave that option?).

After setting all the overrides, try running the game again. The first error should go away and may allow the game to proceed past the second error as well.

Hi, I'm having the same problem: 
```
err:module:import_dll Loading library d3dx9_34.dll
```d3dx9_34.dll

I followed your instructions, copying to system32, adding the entries in winecfg, I've even recompiled wine with a patched version (0.9.48)  that said it would get it working. (from here: [http://www.winehq.org/pipermail/wine-devel/2007-October/059790.html](http://www.winehq.org/pipermail/wine-devel/2007-October/059790.html))
Even with the dll's in the wine system32 directory it still gives me the same error.  Is there maybe some extra step I have missed here?

---

### Post by cogadh on 2007-11-14
If you followed all those steps, then it should work, I don't see how it could still say that library is missing. However, I would suggest that you might be better off using the current official release version of Wine, 0.9.49, instead of a self-compiled patched version of 0.9.48.

---

### Post by gorara on 2007-11-14
I compiled the patched version and did a make install, which installed wine to /usr/local/bin/wine.  I also have my original install of wine (via apt-get) installed to /usr/bin/wine.

both versions of wine are present:

```

gorara@xero:~$ /usr/local/bin/wine --version
wine-0.9.48
gorara@xero:~$ /usr/bin/wine --version
wine-0.9.49

```

I've tried running from the command line like this:

```

env WINEPREFIX="/home/gorara/.wine" /usr/local/bin/wine "C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3sp.exe"

```

as well as like this:

```

env WINEPREFIX="/home/gorara/.wine" /usr/bin/wine "C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3sp.exe"

```

but still get the same error.

These are the dx files in my .wine/drive_c/windows/system32 directory:

```

gorara@xero:~$ ls -l /home/gorara/.wine/drive_c/windows/system32 | grep dx
-rwxr-xr-x 1 gorara gorara  443752 2007-03-15 16:57 d3dx10_33.dll
-rw-r--r-- 1 gorara gorara  506728 2007-05-16 17:45 d3dx10_34.dll
-rw-r--r-- 1 gorara gorara  508264 2007-07-19 19:14 d3dx10_35.dll
-rwxr-xr-x 1 gorara gorara  444776 2007-10-02 09:56 d3dx10_36.dll
-rw-r--r-- 1 gorara gorara 3544272 2006-02-09 17:54 d3dx9_24.dll
-rw-r--r-- 1 gorara gorara 3823312 2006-02-09 17:54 d3dx9_25.dll
-rw-r--r-- 1 gorara gorara 3767504 2006-02-09 17:54 d3dx9_26.dll
-rw-r--r-- 1 gorara gorara 3807440 2006-02-09 17:54 d3dx9_27.dll
-rw-r--r-- 1 gorara gorara 3815120 2006-02-09 17:54 d3dx9_28.dll
-rw-r--r-- 1 gorara gorara 3830992 2006-02-09 17:54 d3dx9_29.dll
-rw-r--r-- 1 gorara gorara 2388176 2006-04-07 17:51 d3dx9_30.dll
-rwxr-xr-x 1 gorara gorara 2414360 2006-09-28 15:05 d3dx9_31.dll
-rwxr-xr-x 1 gorara gorara 3426072 2006-11-29 13:06 d3dx9_32.dll
-rwxr-xr-x 1 gorara gorara 3495784 2007-03-12 16:42 d3dx9_33.dll
-rw-r--r-- 1 gorara gorara 4496232 2007-05-16 17:45 d3dx9_34.dll
-rw-r--r-- 1 gorara gorara 5073256 2007-07-19 19:14 d3dx9_35.dll
-rwxr-xr-x 1 gorara gorara 3734536 2007-10-12 15:14 d3dx9_36.dll

```

Any idea whats going on?

---

### Post by SM0k3 on 2007-11-14
> **gorara said:**
> I compiled the patched version and did a make install, which installed wine to /usr/local/bin/wine.  I also have my original install of wine (via apt-get) installed to /usr/bin/wine.

both versions of wine are present:

```

gorara@xero:~$ /usr/local/bin/wine --version
wine-0.9.48
gorara@xero:~$ /usr/bin/wine --version
wine-0.9.49

```

I've tried running from the command line like this:

```

env WINEPREFIX="/home/gorara/.wine" /usr/local/bin/wine "C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3sp.exe"

```

as well as like this:

```

env WINEPREFIX="/home/gorara/.wine" /usr/bin/wine "C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3sp.exe"

```

but still get the same error.

These are the dx files in my .wine/drive_c/windows/system32 directory:

```

gorara@xero:~$ ls -l /home/gorara/.wine/drive_c/windows/system32 | grep dx
-rwxr-xr-x 1 gorara gorara  443752 2007-03-15 16:57 d3dx10_33.dll
-rw-r--r-- 1 gorara gorara  506728 2007-05-16 17:45 d3dx10_34.dll
-rw-r--r-- 1 gorara gorara  508264 2007-07-19 19:14 d3dx10_35.dll
-rwxr-xr-x 1 gorara gorara  444776 2007-10-02 09:56 d3dx10_36.dll
-rw-r--r-- 1 gorara gorara 3544272 2006-02-09 17:54 d3dx9_24.dll
-rw-r--r-- 1 gorara gorara 3823312 2006-02-09 17:54 d3dx9_25.dll
-rw-r--r-- 1 gorara gorara 3767504 2006-02-09 17:54 d3dx9_26.dll
-rw-r--r-- 1 gorara gorara 3807440 2006-02-09 17:54 d3dx9_27.dll
-rw-r--r-- 1 gorara gorara 3815120 2006-02-09 17:54 d3dx9_28.dll
-rw-r--r-- 1 gorara gorara 3830992 2006-02-09 17:54 d3dx9_29.dll
-rw-r--r-- 1 gorara gorara 2388176 2006-04-07 17:51 d3dx9_30.dll
-rwxr-xr-x 1 gorara gorara 2414360 2006-09-28 15:05 d3dx9_31.dll
-rwxr-xr-x 1 gorara gorara 3426072 2006-11-29 13:06 d3dx9_32.dll
-rwxr-xr-x 1 gorara gorara 3495784 2007-03-12 16:42 d3dx9_33.dll
-rw-r--r-- 1 gorara gorara 4496232 2007-05-16 17:45 d3dx9_34.dll
-rw-r--r-- 1 gorara gorara 5073256 2007-07-19 19:14 d3dx9_35.dll
-rwxr-xr-x 1 gorara gorara 3734536 2007-10-12 15:14 d3dx9_36.dll

```

Any idea whats going on?


Try doing like it was suggested to me and go into your ".wine/drive_c/windows/Program Files/Activision/Call Of Duty 4 - Modern Warfare" folder then execute wine from the directory (wine iw3sp.exe).

See if that help.

---

### Post by gorara on 2007-11-14
> **SM0k3 said:**
> Try doing like it was suggested to me and go into your ".wine/drive_c/windows/Program Files/Activision/Call Of Duty 4 - Modern Warfare" folder then execute wine from the directory (wine iw3sp.exe).

See if that help.

Tried running it like that, same error.. This is the error output from the cmd line:

```

gorara@xero:~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare$ wine iw3sp.exe 
Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library d3dx9_34.dll (which is needed by L"C:\\Program Files\\Activision\\Call of Duty 4 - Modern Warfare\\iw3sp.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Activision\\Call of Duty 4 - Modern Warfare\\iw3sp.exe" failed, status c0000135

```

Forgot to mention, I'm running Ubuntu Gutsy 7.10 on an AMD Athlon(tm) 64 X2 Dual Core Processor 3800+

Perhaps this message has something to do with the problem?
```

Trying to load PE image for unsupported architecture (AMD-64)

```

---

### Post by cogadh on 2007-11-14
That is pretty likely. Are you using the 64 bit version of Wine or the 32 bit version with the 32 bit library compatibility package?

---

### Post by aatiis on 2007-11-14
Hi. I am trying tu run VirtualDub with wine and I get the same error message. I use the amd64 version of wine and the amd64 port of vdub (vdub) (vdub64.exe).
I am running compiz-fusion but I hope it has nothing to do with this. Other wine apps work just fine...

---

### Post by cogadh on 2007-11-14
> **aatiis said:**
> Hi. I am trying tu run VirtualDub with wine and I get the same error message. I use the amd64 version of wine and the amd64 port of vdub (vdub) (vdub64.exe).
I am running compiz-fusion but I hope it has nothing to do with this. Other wine apps work just fine...
This thread has nothing to do with VDub. Don't hijack other people's threads with unrelated topics, it's rude. Either post in an existing thread related to VDub or start your own.

---

### Post by gorara on 2007-11-14
> **cogadh said:**
> That is pretty likely. Are you using the 64 bit version of Wine or the 32 bit version with the 32 bit library compatibility package?

I'm not actually sure, I assume both versions I have are 32 bit?  I installed wine initially with apt-get so I think thats probably 32 bit.  The one I compiled from source is mostly likely 32 bit, how would I check to make sure? And if they are, should I give the 64 bit version a try? Can I even run the 64 bit version on 32 bit Gutsy?

---

### Post by cogadh on 2007-11-14
Sorry, I assumed that since you have a 64 bit processor, you were running 64 bit Ubuntu. Honestly, I'm really not sure what would happen if you tried to run the 64 bit Wine or if you even should. I haven't really messed with anything 64 bit in Ubuntu, still in 32 bit land here.

---

### Post by gorara on 2007-11-15
Well, thanks for your help, I'll post an update if I ever get it working :?

---

### Post by save2 on 2007-11-17
hi
I followed the DLL copy instructions from [http://www.m3fe.com/760/](http://www.m3fe.com/760/) and got the splash screen of CoD4 demo, but then it shouted something about glow disabled :
Video card driver does not support separate alpha blend , glow will be disabled.
and then I'm stuck...

fglrxinfo returns:
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GS/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.1 NVIDIA 100.14.19

wine version: 0.9.46

update: upgraded to wine 0.9.47 - same results.
installed and run perfectly well on WinXP.

---

### Post by delusion77 on 2007-11-17
I thought COD4 was open gl... or there was a setting to make it open gl. 

If you can do that. maybe it will solve any problems

---

### Post by cogadh on 2007-11-17
> **save2 said:**
> hi
I followed the DLL copy instructions from [http://www.m3fe.com/760/](http://www.m3fe.com/760/) and got the splash screen of CoD4 demo, but then it shouted something about glow disabled :
Video card driver does not support separate alpha blend , glow will be disabled.
and then I'm stuck...

fglrxinfo returns:
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GS/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.1 NVIDIA 100.14.19

wine version: 0.9.46
Error messages from the game are helpful, but the info that comes from Wine and is output to the terminal would be more helpful. Basically the game is telling you *what* didn't work, but the Wine error messages will tell us *why* it didn't work. "Why" is always more helpful than "what". Run the game from the terminal and post the output here. Make sure you use the forum "code" tabs to make it readable.

---

### Post by Moustacha on 2007-11-17
```
$ wine iw3mp.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x32f91c,0x00000000), stub!

$ wine iw3sp.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x32f91c,0x00000000), stub!
```

That's all I'm getting from the output when i run it. Comes up with the 'glow disabled' then dies.
Using 0.9.49, from the winehq repos.

---

### Post by save2 on 2007-11-18
someone posted a bug already:
[http://bugs.winehq.org/show_bug.cgi?id=10010l](http://bugs.winehq.org/show_bug.cgi?id=10010l)

Yesterday I attached my WinXP drive - booted, installed Demo ... and played it for an hour. It just not ready yet for wine.

---

### Post by cogadh on 2007-11-18
Minor error in that link. Here's one that works:
[http://bugs.winehq.org/show_bug.cgi?id=10010](http://bugs.winehq.org/show_bug.cgi?id=10010)

---

### Post by *daniel on 2007-12-29
> **SM0k3 said:**
> I got to the splash screen! lol but I got a C++ error......

Edit: COD2 works though using that method. Thanks

The floating point error is a result of the No CD crack. There's a new one floating (pardon the pun) around the net that fixes this issue.

You still have to compile Wine with the 3Dmark patch to get CoD4 working, though, and it's pretty slow.

---

### Post by heckens on 2008-02-11
I'm not sure if anyone else is having this problem, but this is what I get when I try to install CoD4 in Wine.

---

### Post by heckens on 2008-02-11
Wow, I solved my problem one minute after posting it...

---

### Post by hyper878 on 2010-01-08
Hello , 
how did u solve ur glow problem?.. I cant load my game.. please help
Thanks! 
[email]hyper878@hotmail.com[/email] reply to this email will be highly appreciated !

---

