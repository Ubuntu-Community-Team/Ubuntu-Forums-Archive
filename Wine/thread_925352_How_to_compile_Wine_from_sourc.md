---
title: "How to compile Wine from sourc????"
date: 2008-09-20
forum: Wine
---

### Post by Codemastadink on 2008-09-20
Hey, im trying to get Crysis working in wine. The HowTo on the aplication databas says to  "Compile Wine 1.1.0 with this patch to get it to do "proper" mouse warping""

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107)

So, how do i compile wine? I've looked everywhere and am just really confused, 

Is there any way to simply do this? If so please help me out guys, i'd really love to get this game going.

---

### Post by Codemastadink on 2008-09-20
Someone please

---

### Post by Codemastadink on 2008-09-21
Bump

---

### Post by angryfirelord on 2008-09-21
You have to find wine's dependencies. Usually you can do that when you compile it and it spews out errors. If there are any README or INSTALL files in the wine tarball, read them and they will tell you how to copile wine.

However, there's no need to compile it when there are .debs made specifically for Ubuntu. Just add the wine repository and you'll always have the latest version of wine:

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

---

### Post by aoanla on 2008-09-21
> **angryfirelord said:**
> You have to find wine's dependencies. Usually you can do that when you compile it and it spews out errors. If there are any README or INSTALL files in the wine tarball, read them and they will tell you how to copile wine.

However, there's no need to compile it when there are .debs made specifically for Ubuntu. Just add the wine repository and you'll always have the latest version of wine:

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

Of course, if you'd read the guy's post, rather than just the title, you'd know that he wants to compile with certain patches. A pre-built deb isn't going to help with that.



As for actually doing it:

First:

sudo apt-get build-dep wine  

(that installs your dependencies for compiling it)

Get the source code from here:

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)

(and unzip it and untar it)

Also get your patch.

Apply the patch:

change directory to the unpacked source directory, and copy the patch over to it.

patch -p1 < patch_name.diff

will then apply the patch to the source.

Compile wine:

[http://www.winehq.org/site/docs/wineusr-guide/installing-wine-source](http://www.winehq.org/site/docs/wineusr-guide/installing-wine-source)


Tell us if anything gives issues at any point.

---

### Post by Codemastadink on 2008-09-21
> **aoanla said:**
> 


Get the source code from here:

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)

(and unzip it and untar it)



Tell us if anything gives issues at any point.

I see a lot of files.. which one do i need to get?

Sorry im new to ubuntu, i know the basics and can do most stuff, just this gives me trouble
[COLOR="Red"]
EDIT: Oh ok so i found the one i need, now what do i do with it? were do i unzip it to?[/COLOR]

---

### Post by Codemastadink on 2008-09-21
.

---

### Post by Codemastadink on 2008-09-21
Someone?

---

### Post by aoanla on 2008-09-22
Anywhere you want - it will all unpack into a directory called wine-1.1.0 
(or whatever release version you chose). This directory contains all the source code for wine - the rest of the steps compile your copy of wine from the source code, and then install it to your system (thus, the location of the source code itself doesn't matter).

---

### Post by Codemastadink on 2008-09-22
> **aoanla said:**
> Anywhere you want - it will all unpack into a directory called wine-1.1.0 
(or whatever release version you chose). This directory contains all the source code for wine - the rest of the steps compile your copy of wine from the source code, and then install it to your system (thus, the location of the source code itself doesn't matter).

Okay just did it into my home folder, thanks a bumch, now how do i apply the patch?

On the site i right clicked on it and saved it, the filename is "attatchment.cgi" so what command would i use?

You said to use 

```
patch -p1 < patch_name.diff
```

but mine isnt even a .diff file its .cgi

Or did i get the patch in the wrong way?

---

### Post by Codemastadink on 2008-09-22
..

---

### Post by aoanla on 2008-09-23
> **Codemastadink said:**
> Okay just did it into my home folder, thanks a bumch, now how do i apply the patch?

On the site i right clicked on it and saved it, the filename is "attatchment.cgi" so what command would i use?

You said to use 

```
patch -p1 < patch_name.diff
```

but mine isnt even a .diff file its .cgi

Or did i get the patch in the wrong way?

You got the patch in the wrong way, probably - the cgi script is the thing that should have redirected your browser to the correct location for it to download the actual patch.

You could always try it, in case the browser just didn't pick up the correct name for it (but did fill it with the right stuff) - patch won't use an invalid patch, nor attempt to apply a patch that it can't match to the existing code, so you're pretty safe there.

---

### Post by Codemastadink on 2008-09-23
> **aoanla said:**
> You got the patch in the wrong way, probably - the cgi script is the thing that should have redirected your browser to the correct location for it to download the actual patch.

You could always try it, in case the browser just didn't pick up the correct name for it (but did fill it with the right stuff) - patch won't use an invalid patch, nor attempt to apply a patch that it can't match to the existing code, so you're pretty safe there.

Hey idk how to get the patch really, it didnt work. Coudld you check and see how 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107)

Its about half way down the page in red.

---

### Post by david_kt on 2008-09-23
I have patched the wine for you, just download from here:

[http://www.mediafire.com/?sharekey=282809a13c089396d2db6fb9a8902bda](http://www.mediafire.com/?sharekey=282809a13c089396d2db6fb9a8902bda)

After you download it, extract it and then compile it (see below how to complie it).

But you must have the necessary program to compile it:

```
sudo apt-get build-dep wine
```

But if you want to patch it yourself, this is the step:

Download the source (may be you already have it):

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449&release_id=609819](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449&release_id=609819)

Extract it, let's assume you extract it on your desktop.

Open terminal, and go to dinput folder:

```
/home/your_user_name/Desktop/wine-1.1.0/dlls/dinput
```

Off course change you_user_name with your actual user name.

Create a new file, using gedit, let's say the name is patch.diff (you could use any name and extention, it does not matter):

```
gedit patch.diff
```

copy and paste the patch below and save it:
```
--- dlls/dinput/mouse.c_old	2008-03-03 11:14:47.000000000 +0100
+++ dlls/dinput/mouse.c	2008-03-10 19:23:21.000000000 +0100
@@ -306,7 +306,7 @@
                 wdata = pt1.y;
             }
 
-            This->need_warp = (pt.x || pt.y) && dwCoop & DISCL_EXCLUSIVE;
+            This->need_warp = (hook->pt.x<2 || hook->pt.y<2 || hook->pt.x>((2 * This->win_centerX)-2) || hook->pt.y>((2 * This->win_centerY)-2) );
             break;
         }
         case WM_MOUSEWHEEL:
```

Close the text editor and in terminal run below command (make sure you still in the dinput directory):

```
patch <patch.diff
```

The last step is to compile wine. Navigate to the extracted directory of wine source, where you could find the readme file:

```
cd /home/your_user_name/Desktop/wine-1.1.0
```

Run the installer from there:

```
./tools/wineinstall
```

It will take sometime to compile.

Hopefully you could run your program. I did not try whether or not this wine is suitable for your program, I just help you to patche and to compile it.

DK

---

### Post by Codemastadink on 2008-09-24
/

---

### Post by david_kt on 2008-09-24
> **Codemastadink said:**
> 
So i downloaded and extracted, and ran the

```
sudo apt-get build-dep wine
```

to compile. 

Very sorry I did not write it clearly. I guess you have run sudo apt-get build-dep wine before, so that you do not need to run it again. What you need to do is:

Make sure you  do not have wine installed:

```
sudo apt-get remove wine
```

Or, if you have installed wine from the source code before, uninstall it using below command:

```
cd /home/your_user_name/Desktop/wine-?.?.? (whatever wine you ever compiled and install before
```
and then 
```
sudo make uninstall
```

After making sure you do not have wine installed, open terminal and navigate to the extracted directory of wine source, where you could find the readme file:


```
cd /home/your_user_name/Desktop/wine-1.1.0
```

That is assuming you extracted the downloaded source on your desktop.

And then run the installer from there:


```
./tools/wineinstall
```

DK

---

### Post by Codemastadink on 2008-09-24
Still getting the same problem :( UGH!!

---

### Post by david_kt on 2008-09-24
> **Codemastadink said:**
> Still getting the same problem :( UGH!!

Problem in compiling wine or problem running your program?
If problem in running the program, make sure you have done below after installing Crysis as mention in the wineappdb:
[LIST=1]
[*]Put d3dx9_36.dll and XINPUT1_3.dll in windows/system32. You can get them from a DLL site like dll-files.com
[*]Set Shaders to High, else you will get graphical problems
[*]If you have problems with insane HDR lighting (believe me, you will), open a console and issue con_restricted 0 and r_glow 0
[/LIST]
DK

---

### Post by Codemastadink on 2008-09-24
> **david_kt said:**
> Problem in compiling wine or problem running your program?

DK

just running wine in general, when i go to aplications its not in there, but the old stuff is, when i used the command to uninstall the older one it said it couldnt be found

---

### Post by david_kt on 2008-09-24
> **Codemastadink said:**
> just running wine in general, when i go to aplications its not in there, but the old stuff is, when i used the command to uninstall the older one it said it couldnt be found

I saw the file size of the demo crysis is 1.7 GB, too much for me to download as I do not play this game.

But if you want to clear the old stuff in the menu that fail to be removed by uninstaller, just open your browser:

Places ==> home folder ==> press <ctrl> and h (to view hidden file) ==> double click on .local directory ==>  applications ==> wine  

and then you could delete whatever stuff you think should not be there anymore.

DK

---

### Post by Codemastadink on 2008-09-24
> **david_kt said:**
> I saw the file size of the demo crysis is 1.7 GB, too much for me to download as I do not play this game.

But if you want to clear the old stuff in the menu that fail to be removed by uninstaller, just open your browser:

Places ==> home folder ==> press <ctrl> and h (to view hidden file) ==> double click on .local directory ==>  applications ==> wine  

and then you could delete whatever stuff you think should not be there anymore.

DK

AWESOME!!! Got rid of all that old crap, but i still cant get the new wine working.

Wine doesnt show up in the Applications menue

---

### Post by david_kt on 2008-09-24
> **Codemastadink said:**
> AWESOME!!! Got rid of all that old crap, but i still cant get the new wine working.

Wine doesnt show up in the Applications menue

Well, if you give me more details of your problem, I might be able to help. what you could do is:

Rune the installer in terminal:

```
wine setup.exe
```

And copy and paste the output of that terminal here to see what is failing. If the setup is ok but it is not show up in the menu, open your browser

Places >> Home >> press <ctrl> <h> >> .wine >> drive_c >> Program Files

And open the folder you suspect is your program you have just install. And after that see is there any program.exe there (for example crysis.exe).

You could try to double click that exe file.

If it is not working open terminal, type cd and drag and drop the folder containing program.exe to your terminal and press enter, it would go to that folder as working directory.

Type wine program/crysis.exe (or whatever exe file you want to execute) and post the out put if the terminal here.

DK

---

### Post by Codemastadink on 2008-09-24
> **david_kt said:**
> Well, if you give me more details of your problem, I might be able to help. what you could do is:

Rune the installer in terminal:

```
wine setup.exe
```

And copy and paste the output of that terminal here to see what is failing. If the setup is ok but it is not show up in the menu, open your browser

Places >> Home >> press <ctrl> <h> >> .wine >> drive_c >> Program Files

And open the folder you suspect is your program you have just install. And after that see is there any program.exe there (for example crysis.exe).

You could try to double click that exe file.

If it is not working open terminal, type cd and drag and drop the folder containing program.exe to your terminal and press enter, it would go to that folder as working directory.

Type wine program/crysis.exe (or whatever exe file you want to execute) and post the out put if the terminal here.

DK

When i type
```
 wine setup.exe
wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found

```

I havent tried to install a game yet because i dont know if it will work, should i try to install the game and see if it does?

---

### Post by david_kt on 2008-09-24
> **Codemastadink said:**
> When i type
```
 wine setup.exe
wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found

```

I havent tried to install a game yet because i dont know if it will work, should i try to install the game and see if it does?

Sure it did not work if you do not have setup.exe in your home folder.
Proceed to install the game and see how it works.

DK

---

### Post by Codemastadink on 2008-09-24
> **david_kt said:**
> Sure it did not work if you do not have setup.exe in your home folder.
Proceed to install the game and see how it works.

DK

So i installed the game, and when i go Applications>Wine>Programs>Electronic Arts>Crysis it says "Play Crysis"

When i click on this the cursor changes to the circle that spins around like its loading, But nothing happens.

If i go into the files where the game is installed and double click on Crysis.exe, again, nothing happens.

If i try to go to the terminal and type
```
 wine crysis.exe
wine: could not load L"C:\\windows\\system32\\crysis.exe": Module not found

```

I tried to change directory to where the .exe file is and then run it, but its inside a "Program files" folder, and when i try to cd to it the terminal can not recognize the space in between. At least i assume so because it cuts off and says 

```
cd /home/cody/.wine/drive_c/Program Files
bash: cd: /home/cody/.wine/drive_c/Program: No such file or directory

```

EDIT: So about 30min after i posted this, i realised my laptop was going slow, i opened up the system monitor and in the processes it said that Crysis.exe was running, and taking about 50% of my cpu power.

So it looks like its running in some way i guess, Idk tho

EDIT#2: So i closed it down in the system monitor and then went to Applications>Wine>Programs>Electronic Arts>Crysis>Play Crysis   and it started back up again in the system monitor, but doesnt display anyhting on screen

---

### Post by david_kt on 2008-09-24
> **Codemastadink said:**
> 

I tried to change directory to where the .exe file is and then run it, but its inside a "Program files" folder, and when i try to cd to it the terminal can not recognize the space in between. At least i assume so because it cuts off and says 

```
cd /home/cody/.wine/drive_c/Program Files
bash: cd: /home/cody/.wine/drive_c/Program: No such file or directory

```

EDIT: So about 30min after i posted this, i realised my laptop was going slow, i opened up the system monitor and in the processes it said that Crysis.exe was running, and taking about 50% of my cpu power.

Here is what you have to do:

1. Restart your computer
2. There are two ways to go to Directory with space in it, open terminal and issue below command:

```
cd /home/cody/.wine/drive_c/Program\ Files
```

(yes, insert foward slash to be able to go to "Program Files" folder), or

```
cd '/home/cody/.wine/drive_c/Program Files'
```
3. After you are in that folder, run wine crysis.exe, and copy and paste the output of that command to see what error it has.

DK

---

### Post by Codemastadink on 2008-09-24
```
cody@cody-laptop:~$ cd /home/cody/.wine/drive_c/program\files/electronic\arts/crytek/crysis/bin32
bash: cd: /home/cody/.wine/drive_c/programfiles/electronicarts/crytek/crysis/bin32: No such file or directory
cody@cody-laptop:~$ cd '/home/cody/.wine/drive_c/program files/electronic arts/crytek/crysis/bin32
> wine crysis.exe
> 


```

Still nothing :/

---

### Post by david_kt on 2008-09-24
> **Codemastadink said:**
> ```
cody@cody-laptop:~$ cd /home/cody/.wine/drive_c/program\files/electronic\arts/crytek/crysis/bin32
bash: cd: /home/cody/.wine/drive_c/programfiles/electronicarts/crytek/crysis/bin32: No such file or directory
cody@cody-laptop:~$ cd '/home/cody/.wine/drive_c/program files/electronic arts/crytek/crysis/bin32
> wine crysis.exe
> 


```

Still nothing :/

DO NOT remove the space, just insert the foward slash:

```
cd /home/cody/.wine/drive_c/program\ files/electronic\ arts/crytek/crysis/bin32
```

Or put '.....', you miss the closing '

```
cd '/home/cody/.wine/drive_c/program files/electronic arts/crytek/crysis/bin32'
```

Please try again.

DK

---

### Post by Codemastadink on 2008-09-24
> **david_kt said:**
> DO NOT remove the space, just insert the foward slash:

```
cd /home/cody/.wine/drive_c/program\ files/electronic\ arts/crytek/crysis/bin32
```

Or put '.....', you miss the closing '

```
cd '/home/cody/.wine/drive_c/program files/electronic arts/crytek/crysis/bin32'
```

Please try again.

DK


Ok, i copied and pasted striaght from here 

```

cody@cody-laptop:~$ cd /home/cody/.wine/drive_c/program\ files/electronic\ arts/crytek/crysis/bin32
bash: cd: /home/cody/.wine/drive_c/program files/electronic arts/crytek/crysis/bin32: No such file or directory
cody@cody-laptop:~$ cd '/home/cody/.wine/drive_c/program files/electronic arts/crytek/crysis/bin32'
bash: cd: /home/cody/.wine/drive_c/program files/electronic arts/crytek/crysis/bin32: No such file or directory


```

Screenshot included of the folder

---

### Post by david_kt on 2008-09-24
> **Codemastadink said:**
> Ok, i copied and pasted striaght from here 

Looks like there is mistyping there. Here is another way to do it to avoid mistyping:

1. Application >> wine >> Browse C:\ Drive
2. Double click Program File etc until you could see the crysis.exe
3. Open terminal and type cd (do not press enter yet)
4. Drag the folder containing crysis.exe (bin32 folder) and drop it to the terminal. On the terminal, you will have cd '/home/........./bin32', and just press enter, you will go to bin32 directory.

5. wine Crysis.exe

DK

---

### Post by david_kt on 2008-09-25
After seeing your screenshoot, here is the correct command:

```
cd /home/cody/.wine/drive_c/Program\ Files/Electronic\ Arts/Crytek/Crysis/Bin32
```

You have to follow the case.

Or:

```
cd '/home/cody/.wine/drive_c/Program Files/Electronic Arts/Crytek/Crysis/Bin32'
```

After that, run wine Crysis.exe (follow the case as well).

DK

---

### Post by Codemastadink on 2008-09-25
```

cody@cody-laptop:~$ cd '/home/cody/.wine/drive_c/Program Files/Electronic Arts/Crytek/Crysis/Bin32' 
cody@cody-laptop:~/.wine/drive_c/Program Files/Electronic Arts/Crytek/Crysis/Bin32$ wine crysis
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x51a520,0x00000004,0x51a51c) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x51940c): Stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x519258,0x00000000), stub!
wine: Unhandled page fault on write access to 0x00932000 at address 0x370b8e46 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00932000 in 32-bit code (0x370b8e46).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:370b8e46 ESP:0051a8e0 EBP:0051a8f0 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:ffffffff ECX:3fff3801 EDX:00000003
 ESI:00900000 EDI:00931ffe
Stack dump:
0x0051a8e0:  0051a924 00000000 00900006 48590000
0x0051a8f0:  0051ad3c 370b344b 00900006 ffffffff
0x0051a900:  376208f0 00000000 0050cfba 378800ec
0x0051a910:  378d6000 00000001 00000000 00032000
0x0051a920:  00000030 5c3f3f5c 756c6f56 307b656d
0x0051a930:  30303030 2d303030 30303030 3030302d
Backtrace:
=>1 0x370b8e46 in crysis (+0xb8e46) (0x0051a8f0)
  2 0x370b344b in crysis (+0xb344b) (0x0051ad3c)
  3 0x371bbf31 in crysis (+0x1bbf31) (0x0052f93c)
  4 0x37059f92 in crysis (+0x59f92) (0x0052fdbc)
  5 0x37626b04 in crysis (+0x626b04) (0x37329ccf)
0x370b8e46: repe stosl	%es:(%edi)
Modules:
Module	Address			Debug info	Name (78 modules)
PE	37000000-3792b000	Export          crysis
PE	78130000-781cb000	Deferred        msvcr80
ELF	7b800000-7b930000	Deferred        kernel32<elf>
  \-PE	7b820000-7b930000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d766000-7e27b000	Deferred        libglcore.so.1
ELF	7e27b000-7e31f000	Deferred        libgl.so.1
ELF	7e330000-7e433000	Deferred        wined3d<elf>
  \-PE	7e340000-7e433000	\               wined3d
ELF	7e433000-7e463000	Deferred        d3d9<elf>
  \-PE	7e440000-7e463000	\               d3d9
ELF	7e487000-7e4e9000	Deferred        rpcrt4<elf>
  \-PE	7e490000-7e4e9000	\               rpcrt4
ELF	7e4e9000-7e58d000	Deferred        ole32<elf>
  \-PE	7e500000-7e58d000	\               ole32
ELF	7e5b5000-7e5e8000	Deferred        uxtheme<elf>
  \-PE	7e5c0000-7e5e8000	\               uxtheme
ELF	7e5e8000-7e5f1000	Deferred        libxcursor.so.1
ELF	7e5f1000-7e5f6000	Deferred        libxfixes.so.3
ELF	7e5f6000-7e5f9000	Deferred        libxcomposite.so.1
ELF	7e5f9000-7e5ff000	Deferred        libxrandr.so.2
ELF	7e5ff000-7e607000	Deferred        libxrender.so.1
ELF	7e607000-7e60a000	Deferred        libxinerama.so.1
ELF	7e60a000-7e62a000	Deferred        imm32<elf>
  \-PE	7e610000-7e62a000	\               imm32
ELF	7e62a000-7e62f000	Deferred        libxdmcp.so.6
ELF	7e62f000-7e647000	Deferred        libxcb.so.1
ELF	7e647000-7e64a000	Deferred        libxau.so.6
ELF	7e64a000-7e731000	Deferred        libx11.so.6
ELF	7e731000-7e73f000	Deferred        libxext.so.6
ELF	7e73f000-7e744000	Deferred        libxxf86vm.so.1
ELF	7e744000-7e75c000	Deferred        libice.so.6
ELF	7e75c000-7e764000	Deferred        libsm.so.6
ELF	7e771000-7e773000	Deferred        libnvidia-tls.so.1
ELF	7e775000-7e80c000	Deferred        winex11<elf>
  \-PE	7e780000-7e80c000	\               winex11
ELF	7e81c000-7e83d000	Deferred        libexpat.so.1
ELF	7e83d000-7e867000	Deferred        libfontconfig.so.1
ELF	7e867000-7e869000	Deferred        libxcb-xlib.so.0
ELF	7e878000-7e88d000	Deferred        libz.so.1
ELF	7e88d000-7e8fa000	Deferred        libfreetype.so.6
ELF	7e8fa000-7e90d000	Deferred        libresolv.so.2
ELF	7e91e000-7e93c000	Deferred        iphlpapi<elf>
  \-PE	7e920000-7e93c000	\               iphlpapi
ELF	7e93c000-7e968000	Deferred        ws2_32<elf>
  \-PE	7e940000-7e968000	\               ws2_32
ELF	7e968000-7e982000	Deferred        wsock32<elf>
  \-PE	7e970000-7e982000	\               wsock32
ELF	7e982000-7e996000	Deferred        lz32<elf>
  \-PE	7e990000-7e996000	\               lz32
ELF	7e996000-7e9af000	Deferred        version<elf>
  \-PE	7e9a0000-7e9af000	\               version
ELF	7e9af000-7ea19000	Deferred        msvcrt<elf>
  \-PE	7e9c0000-7ea19000	\               msvcrt
ELF	7ea19000-7ead8000	Deferred        comctl32<elf>
  \-PE	7ea20000-7ead8000	\               comctl32
ELF	7ead8000-7eb31000	Deferred        shlwapi<elf>
  \-PE	7eaf0000-7eb31000	\               shlwapi
ELF	7eb31000-7ec46000	Deferred        shell32<elf>
  \-PE	7eb40000-7ec46000	\               shell32
ELF	7ec46000-7ec98000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec98000	\               advapi32
ELF	7ec98000-7ed36000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed36000	\               gdi32
ELF	7ed36000-7ee7d000	Deferred        user32<elf>
  \-PE	7ed50000-7ee7d000	\               user32
ELF	7ef9d000-7efa8000	Deferred        libnss_files.so.2
ELF	7efa8000-7efb2000	Deferred        libnss_nis.so.2
ELF	7efb2000-7efca000	Deferred        libnsl.so.1
ELF	7efca000-7efef000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7d16000-b7d1a000	Deferred        libdl.so.2
ELF	b7d1a000-b7e69000	Deferred        libc.so.6
ELF	b7e6a000-b7e82000	Deferred        libpthread.so.0
ELF	b7e93000-b7fc9000	Deferred        libwine.so.1
ELF	b7fcb000-b7fe7000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Electronic Arts\Crytek\Crysis\Bin32\crysis.exe
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000021 
	00000022    0
Backtrace:
=>1 0x370b8e46 in crysis (+0xb8e46) (0x0051a8f0)
  2 0x370b344b in crysis (+0xb344b) (0x0051ad3c)
  3 0x371bbf31 in crysis (+0x1bbf31) (0x0052f93c)
  4 0x37059f92 in crysis (+0x59f92) (0x0052fdbc)
  5 0x37626b04 in crysis (+0x626b04) (0x37329ccf)


```

---

### Post by david_kt on 2008-09-25
Have you put d3dx9_36.dll and XINPUT1_3.dll in windows/system32. You can get them from a DLL site like dll-files.com

If not yet, do it first and run again in terminal.
DK

---

### Post by Codemastadink on 2008-09-25
> **david_kt said:**
> Have you put d3dx9_36.dll and XINPUT1_3.dll in windows/system32. You can get them from a DLL site like dll-files.com

If not yet, do it first and run again in terminal.
DK

Yeah i did already

---

### Post by david_kt on 2008-09-25
> **Codemastadink said:**
> Yeah i did already

That is the end of my wit. You could post the output of the terminal to winedb:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107&iTestingId=19875](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107&iTestingId=19875)

and hope people using this game could help you further.

What I can see the problem that cause wine to abort is :
```
wine: Unhandled page fault on write access to 0x00932000 at address 0x370b8e46 (thread 0009)
```

but I do not know how to solve it at the moment. 

Very sorry.
DK

---

### Post by Codemastadink on 2008-09-25
> **david_kt said:**
> That is the end of my wit. You could post the output of the terminal to winedb:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107&iTestingId=19875](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107&iTestingId=19875)

and hope people using this game could help you further.

What I can see the problem that cause wine to abort is :
```
wine: Unhandled page fault on write access to 0x00932000 at address 0x370b8e46 (thread 0009)
```

but I do not know how to solve it at the moment. 

Very sorry.
DK

Hey thats ok man u totally helped a lot, Tried the best you could :) thats all i can ask :)

Thanks a bunch dude!

---

### Post by Fazer2 on 2008-09-27
Have you enabled external dll files in Winecfg?

---

### Post by Codemastadink on 2008-10-01
> **Fazer2 said:**
> Have you enabled external dll files in Winecfg?

No, how would i do that?

---

### Post by david_kt on 2008-10-01
> **Codemastadink said:**
> No, how would i do that?

First of all rename uppercase dll to lower case(e.g. XINPUT1_3.dll to xinput1_3.dll). After that open terminal and run:

```
wine regsvr32 d3dx9_36
```
```
wine regsvr32 xinput1_3
```

to register your dll.

DK

---

