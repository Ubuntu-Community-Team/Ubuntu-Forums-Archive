---
title: "Wine 0.9.39 breaks Eve Online"
date: 2007-06-23
forum: Wine
---

### Post by Afoot on 2007-06-23
Hi,
I'd just like to point out that the aforementioned version of Wine breaks support for Eve Online. It can work with 0.9.39 if you recompile it with a patch found somewhere on winehq (don't know where exactly, maybe you do?). This leaves you with two options:
[LIST]
[*] Get 0.9.36 or any other version you know it works with 
[*] Recompile 0.9.39 with a patch
[/LIST]
If someone decides to recompile it, would you be so kind and upload the deb file (or whatever you managed to get).

---

### Post by Caseyjp on 2007-07-03
.9.40 has resolved those issues, and EVE will install and work with no additional patching.

---

### Post by Sammi on 2007-07-03
@Afoot
I spent a few hours learning how to compile Wine with a patch, in order to make 0.9.39 work. I'm sorry I didn't see this post sooner, or I would have uploaded the deb I created for you. But now we've got 0.9.40, so everybody's happy.
:KS

---

### Post by ipreferpi on 2007-07-27
I have wine 9.41, and when I try to run eve, the splash screen appears then goes away. Nothing else happens. The exefile.exe lingers in the list of processes for a while. I've tried changing the voice option to 0 in preferences and running the d3d exe, but nothing happens. Any ideas?

---

### Post by cogadh on 2007-07-27
Have you done this stuff as listed on Wine's AppDB:
> If it doesn't work you might want to start with a new ~/.wine directory.

- run "wine winecfg" to setup/configure your wine install (mainly sound driver)
- you can copy the Eve folder into ~/.wine/drive_c/ or install from scratch. (try without the cache folder first)
- copy arial.ttf to ~/.wine/drive_c/windows/fonts/ (install ms corefonts package and then search for arial.ttf on your disk)
- install the d3d9x_30.dll by running the RedistD3DXOnly.exe in the bin dir

If Eve crashes/hangs after the character selection you need to add "voiceenabled=0" to ~/.wine/drive_c/windows/profiles/username/Local Settings/Application Data/CCP/EVE/settings/prefs.ini. This is needed if you have a voice enabled account or try to test on Singularity when voice is enabled there.

optional you might want to set VideoMemorySize to the amount of video ram for your gfx card and OffscreenRenderingMode to pbuffer for improved icon rendering. check the wiki then use "wine regedit" to edit the values/create the keys. Don't forget to remove the old icons by deleting the cache/Pictures folder or they won't be rebuild. 
[http://appdb.winehq.org/appview.php?iVersionId=8660](http://appdb.winehq.org/appview.php?iVersionId=8660)

---

### Post by ipreferpi on 2007-07-27
"install the d3d9x_30.dll by running the RedistD3DXOnly.exe in the bin dir" That is the step I'm having trouble with. The .exe doesn't seem to do anything.

edit: some guys on the eve forum are having similar trouble 
[http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=30457&page=46](http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=30457&page=46)

---

### Post by cogadh on 2007-07-27
Are you running it from the terminal like this:
```
wine /media/cdrom0/bin/RedistD3DXOnly.exe
```
and if so, what messages are produced in the terminal?

---

### Post by snoopeh on 2007-08-19
Im having the same trouble with splash screen coming up, then disappearing but lingering in process. The  ' RedistD3DXOnly.exe '
is also causing problems
[B][U]
First I do[/U][/B]

stephen@stephen-desktop:~$ **cd "/media/disk/EVE"**
stephen@stephen-desktop:/media/disk/EVE$ **wine eve.exe**
fixme:process:IsWow64Process (0xffffffff 0x33fc34) stub!
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x347b2c

**_Then I do_**

stephen@stephen-desktop:/media/disk/EVE$** cd "/media/disk/EVE/bin"**
stephen@stephen-desktop:/media/disk/EVE/bin$ **wine RedistD3DXOnly.exe**
fixme:mscoree:GetCORVersion (0x33f730, 600, 0x33f71c): semi-stub!
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33f628
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ee44
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ee44
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ee44
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ee44
[B]err:setupapi:do_file_copyW Unsupported style(s) 0x144
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "c:\\windows\\system32\\DirectX\\DX49d5.tmp\\Apr2006_d3dx9_30_x86.cab"
err:cabinet:FDICopy FDIIsCabinet failed.[/B]

Im new to linux, been using windows for about 10-15 years. Made the swap 3 weeks ago, so far got "World of Warcraft" & "Counterstrike" working. Only other game I would like to get working is EVE Online for the moment.

I've heard that EVE Online is working with transgaming, so Cedega runs fine with EVE. But I've also heard of people getting EVE Online working on Wine. To be honest, I don't know why CCP is working with Transgaming and not the Wine Developers, but **** happens i guess.

Im Running Ubuntu Fiesty Fawn 7.04. If any more information is required, then I will gladly post it, aslong as It helps to fix EVE :)

---

### Post by Perfect Storm on 2007-08-19
[http://ubuntuforums.org/showthread.php?t=522354](http://ubuntuforums.org/showthread.php?t=522354)

---

### Post by snoopeh on 2007-08-19
Ok so after reading [http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=30457&page=47](http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=30457&page=47)

I hear that EVE Online works on wine-0.9.41 , but the problem is I upgraded from wine-0.9.33 to wine-0.9.43 . So there is no option to force to 41, only 33 and 43.

41 is at [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) but, do i need to remove wine, then install 41 before i can put 41 on my machine or what?

---

### Post by Sammi on 2007-08-19
> **snoopeh said:**
> Ok so after reading [http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=30457&page=47](http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=30457&page=47)

I hear that EVE Online works on wine-0.9.41 , but the problem is I upgraded from wine-0.9.33 to wine-0.9.43 . So there is no option to force to 41, only 33 and 43.

41 is at [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) but, do i need to remove wine, then install 41 before i can put 41 on my machine or what?
I think you should be able to just install Wine 0.9.41. After that you should use Synaptic to lock the version, so the system doesn't try to update it to 0.9.43 again. To do this you need to find and select Wine in Synaptic, then you go to the"package" menu and choose "lock version".

---

### Post by snoopeh on 2007-08-19
I open the .deb with "GDebi Package Installer" , but it just says "Error  : A later version is already installed " and won't let me install. Whats the command line to install deb files? I think i've used it before just can't remember it.

---

### Post by Sammi on 2007-08-20
> **snoopeh said:**
> I open the .deb with "GDebi Package Installer" , but it just says "Error  : A later version is already installed " and won't let me install. Whats the command line to install deb files? I think i've used it before just can't remember it.Then you should uninstall 0.9.43 first. You can do that in Synaptic.

Anyway the terminal command for using the package manager to install is: sudo apt-get install *package-name* 

And remove is: sudo apt-get remove *package-name*

---

### Post by snoopeh on 2007-08-20
Ahh, I thought it would be different for .deb files such as wine_0.9.41~winehq0~ubuntu~7.04-1_i386.deb

Guess not, thanks for the help :)

---

### Post by Sammi on 2007-08-20
np :D

---

### Post by koer on 2007-08-26
hello, i have been trying to run eve online for some time now , finally i did it , i had that splash screen going away problem , but this is how i fixed it : installing wine 9.44 then eve online (latest version 3.22 ) 
first copy    arial.ttf     to home/(user name)/.wine/drive_c/windows/fonts/ ( arial.ttf can be found by searching your windows hard drive ) with places>search for files
note: you wont find the /.wine file unless you type it in the file browser
then go to   home/(user name)/.wine/drive_c/windows/profiles/(username)/Local Settings/Application Data/CCP/EVE/settings/prefs.ini 
 and type :     audio=0   save it and close it (type it above "buffersize"
you should be able to start eve online, but without sound

if the upper and lower ubuntu bars cause you to be unable to undock or close things , press esc and set window mode and press esc again, the press esc again and quit the game and start it again , it showld appear as a window and it wont change your desktop configuration

hope this is of help 
i got my info from : [http://appdb.winehq.org/appview.php?iVersionId=9022](http://appdb.winehq.org/appview.php?iVersionId=9022)

---

### Post by Altar on 2007-09-05
I'm trying to get EVE installed but every time I try to install it comes back with an NSIS Error saying the full eve client iv'e downloaded is corrupt.  As a relatively new ubuntu user I could use some help.

Thanks

---

### Post by Sammi on 2007-09-07
> **Altar said:**
> ...the full eve client iv'e downloaded is corrupt...First thing to do is to download it again. Seems like the first download had errors in it.

---

