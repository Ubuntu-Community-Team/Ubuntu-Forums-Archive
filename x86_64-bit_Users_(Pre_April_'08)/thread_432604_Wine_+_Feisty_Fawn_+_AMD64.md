---
title: "Wine + Feisty Fawn + AMD64"
date: 2007-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by fatbuttlarry on 2007-05-04
[img]http://img337.imageshack.us/img337/1242/wineubuntuuu4.gif[/img]

Not sure why, but Wiggens McPeck and I both found the following steps to help us with our wine segmentation faults:
(We both run the same type of processors, video cards, same exact versions of wine and ubuntu). This assumes you have wine installed [ [installing wine #1](https://help.ubuntu.com/community/WineForAMD64)] [[installing wine #2](http://wiki.winehq.org/UbuntuAMD64)]
```

sudo apt-get remove wine
sudo apt-get install wine
sudo apt-get install kde-guidance
wineprefixcreate
winecfg (then close)
wineconfig (then close)
mkdir ~/.wine/drive_c/windows/profiles
mkdir ~/.wine/drive_c/windows/profiles/$USER

```

Then reinstall your NVIDIA driver.
Not sure why, but this seems to fix it.

**Note:**  For LCD displays on nVidia 420/440/460 click [[here](http://kmandla.wordpress.com/2007/05/12/howto-troubleshoot-nvidia-drivers-with-the-ubuntu-704-desktop-cd/)]

-Tres




------------------------------------------------------------------------------------

Hey!

Been smashing my head getting wine to load on AMD64 (Kubuntu 7.04).

A year ago I tried this, and there weren't enough people running native 64 with wine.  Now, it seems there are, and even WineHQ has excellent support for it!

[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

Unfortunately, no matter what I do, whether its downloading w/ apt-get, grabbing a pre-compiled binary, or compile myself (0.9.36), I get Segmentation Fault.

I tried a couple old versions, although only 0.9.35 and 0.9.36 are officially offered for Feisty Fawn, but still no luck.

I saw a few of the WoW guys having similar problems with older versions, and needing to compile with > export CFLAGS="-fno-stack-protector" but the docs say the newest versions don't need this anymore.

I did try compiling with the -fno-stack-protector flag with no luck.

For reference:
```
lite@bjorn:~$ uname -r
2.6.20-15-generic
```

```
lite@bjorn:~$ wine notepad
Segmentation fault (core dumped)
lite@bjorn:~$ 
```

```
lite@bjorn:~/wine-0.9.36$ wineconfig
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)
Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 3547, in <module>
    wineconfigapp = WineConfigApp()
  File "/usr/bin/wineconfig", line 118, in __init__
    self.CreateWindowsInstall()
  File "/usr/bin/wineconfig", line 318, in CreateWindowsInstall
    winewrite.SetDriveMappings(drives)
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 60, in SetDriveMappings
    SetShellLinks(drives[26:])
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 63, in SetShellLinks
    existingshelllinks = os.listdir(wineread.winepath + "/dosdevices/c:/windows/profiles/" + os.environ['USER'])
OSError: [Errno 2] No such file or directory: '/home/lite/.wine/dosdevices/c:/windows/profiles/lite'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 3547, in <module>
    wineconfigapp = WineConfigApp()
  File "/usr/bin/wineconfig", line 118, in __init__
    self.CreateWindowsInstall()
  File "/usr/bin/wineconfig", line 318, in CreateWindowsInstall
    winewrite.SetDriveMappings(drives)
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 60, in SetDriveMappings
    SetShellLinks(drives[26:])
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 63, in SetShellLinks
    existingshelllinks = os.listdir(wineread.winepath + "/dosdevices/c:/windows/profiles/" + os.environ['USER'])
OSError: [Errno 2] No such file or directory: '/home/lite/.wine/dosdevices/c:/windows/profiles/lite'
```

The station is a dual core x64 4800 on an ASUS nForce w/ onboard video.

Any help would be great! Thanks guys!

-Tres

---

### Post by Kilz on 2007-05-04
You dont need to compile it.

Look in my signature, click on wine link, get script, run it, wine works, problem solved :D .

---

### Post by fatbuttlarry on 2007-05-04
Alright.  I think the culprit of this was something video related.

Although I was running X, rebooting crashed X.

I reinstalled the nVidia driver and launched X and wine worked perfectly fine.

The version I ended up using was the precompiled version ```
sudo apt-get install wine
```

So if someone else gets this kernel panic, reboot and make sure your video is working.

I suspect the kernel panic was due to some shared object files not being in the correct location.  Even the "-fno-stack-protector" workaround is built into the lastest version, which is why I got the same results after a successful build.

I also installed all of the wine dev dependencies, for reference, incase one of them by chance helped.

-Tres

---

### Post by NullHead on 2007-05-05
Feisty now has 64bit debs in the wine Repository. 
To be able to use the repository do this.
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

```
```
sudo apt-get update
```
```
sudo apt-get install wine
```
this worked for me.

---

### Post by Kilz on 2007-05-05
> **NullHead said:**
> Feisty now has 64bit debs in the wine Repository. 
To be able to use the repository do this.
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

```
```
sudo apt-get update
```
```
sudo apt-get install wine
```
this worked for me.

That is most excellent news that the wine repo has a 64bit deb file.  :D

---

### Post by fatbuttlarry on 2007-05-05
Yes, those were my first and last steps.

I'd also like to add, this error:

> [Errno 2] No such file or directory: '/home/lite/.wine/dosdevices/c:/windows/profiles/lite'

Although very obvious was fixed by creating the folder "lite" in "profiles".  I wouldn't have thought wineconfig could crash on an error that basic, but it did.

Also, the new steam installs gave a bunch of file permission errors, so I used an old backed up install that was still laying around. :beer:

-Tres

---

### Post by NullHead on 2007-05-05
> **Kilz said:**
> That is most excellent news that the wine repo has a 64bit deb file.  :D

I'm not shure they are  64bit because when I'm doing various things some of those say when they crash in the dump that there was an error in the 32bit code. I don't understand debs very well but I don't think wine is 64bit yet.

---

### Post by Kilz on 2007-05-05
> **NullHead said:**
> I'm not shure they are  64bit because when I'm doing various things some of those say when they crash in the dump that there was an error in the 32bit code. I don't understand debs very well but I don't think wine is 64bit yet.

No wine isnt 64bit yet, wine is a 32bit application layer. Someone will probably tell you that Wine stands for Wine is not an emulator , but most people think of it as one. It lets you run 32bit windows exe's. But it isnt perfect. It cant run everything, yet.
What is in the repos is a 32bit wine, as opposed to a 64bit wine. 64bit wine would run 64bit windows applications. 64bit wine is in its early stages from what I have read. What is in the repos is important. Because its a 64bit package for installing 32bit wine. For the most part all most users want is to run 32bit windows code. 
Im not surprised that the deb still has some bugs because its the first one. But I am happy to see it. As I can soon start to work on other projects that have been in my head and stop supporting the howto I have for wine in the near future.

---

### Post by fatbuttlarry on 2007-05-05
Yeah.  Although it's a 64bit repo package, its really 32 bit code. Cheers.

---

### Post by GoalieCa on 2007-05-05
I haven't figured out how to get opengl working. I have installed the nvidia-32 bit compat libs.

edit: fixed. had to install the libsdl 32-bit libs. 
Weird though is vsync is 1 fps off.. so it tears a little. but it runs ultra smooth!!!!

---

### Post by fatbuttlarry on 2007-05-06
Great!

I'm having a problem getting half-life/counterstrike to launch in 1024x768 without "Desktop Emulation" checked in wineconfig/winecfg.

Resolutions list with desktop emulation checked, but defaults to 640x480 otherwise. :\

-Tres

---

### Post by Enverex on 2007-05-06
What is the output of "xrandr"? (run it in a terminal).

---

### Post by fatbuttlarry on 2007-05-06
I'm not home to check, but when I ran it, it listed just about every resolution under the sun, including 1280x1024, 1152x864, 1024x768, 800x600, 640x480, etc.  I can't remember the refresh rates off-hand, but I explicitly remember only one refresh rate listed for each resolution, which may or may not be normal.

I remember an old XFree86.config workaround for opengl with refresh rates or something, but that was more of an opengl not initializing error.

Do you think this is the same issue, and perhaps wine + xorg are working around it and pushing 640x480 instead?


-FBL

---

### Post by Enverex on 2007-05-06
Does the game let you changed the res itself? I would have thought that would be the obvious choice.

---

### Post by fatbuttlarry on 2007-05-06
> **Enverex said:**
> Does the game let you changed the res itself? I would have thought that would be the obvious choice.

There are two methods for changing resolution:
[list=1]
[*]**Steam** » **Right Click Game** » **Properties** » **Set Launch Options**
```

-width 1024 -height 768

```

[*]Physically opening up the game and going to **Options** » **Video** » **Game Resolution**

[/list]

The first option does nothing, and the game loads in 640x480.

The second options lists no selectable resolutions.  When I get home I can give the exact error, but you can see wine rejecting the resolution change.

I think the error said something about X11/dx not finding a compatible resolution (which can be temporarily fixed by emulating a wine desktop)

-Tres

---

### Post by robbie carrobie on 2007-05-06
dudes please forgive me, i dont like wasting peoples time, however, i followed the instructions on how to download and install this application, which has been done successfully, but i cant see it anywhere, where should it be, i have even reinstalled it from  add and remove programs, am i such a slaphead - please help before insanity sets in - kind regards robert.

---

### Post by fatbuttlarry on 2007-05-07
**robbie;**Are you talking about wine or steam?

If wine, go to winehq.com and follow the install instructions for ubuntu.  They're very straight forward.

If half-life + wine, get an older version of steam or copy the install from a windows box.  Please be as specific as possible.

**enverex:** Here's the wine debug, sorry I didn't get it earlier.

(resolution message)
```
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
```

(entire thing)
```
fixme:shdocvw:ViewObject_SetAdvise (0xfdef668)->(1 00000002 0x1363650)
fixme:shdocvw:PersistStreamInit_InitNew (0xfdef668)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xfdef668)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xfdef668)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xfdef668)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xfdef668)
fixme:shdocvw:OleObject_Close (0xfdef668)->(1)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x188a50) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x187a88)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x187a88)->((nil),00000013)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x187a88)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.

```


Thanks!!!


-FBL

---

### Post by fatbuttlarry on 2007-05-07
Got it!  Half-Life will launch full screen if you set the color depth to the same as the desktop.  Lol ,thats an old bug too, but it fixed it!

-FBL

---

### Post by billstei on 2007-05-07
Kilz,

I've used the instructions and Sidenet script that you provided, and I appreciate it and have had no problems with it, but if I switch to this new repository do you have any warnings or recommendations as to how to uninstall (and/or avoid conflicts with) the Sidenet setup?

Thanks,
Bill

---

### Post by Kilz on 2007-05-07
> **billstei said:**
> Kilz,

I've used the instructions and Sidenet script that you provided, and I appreciate it and have had no problems with it, but if I switch to this new repository do you have any warnings or recommendations as to how to uninstall (and/or avoid conflicts with) the Sidenet setup?

Thanks,
Bill

Sidenet only sets up wine. You can simply delete the .wine and c folders from your home directory. But ask yourself a few questions before removing an already working install of wine. Is it broke? Should I fix it if it isnt broke? Because what you will be doing is installing wine with no configuration, the exact same 32bit wine you already have. You will have to then do all the config manually.

---

### Post by NullHead on 2007-05-07
> **GoalieCa said:**
> I haven't figured out how to get opengl working. I have installed the nvidia-32 bit compat libs.

edit: fixed. had to install the libsdl 32-bit libs. 
Weird though is vsync is 1 fps off.. so it tears a little. but it runs ultra smooth!!!!


opengl just works for me i didn't have to do anything to it.

---

### Post by fatbuttlarry on 2007-05-07
> **NullHead said:**
> opengl just works for me i didn't have to do anything to it.

Me too, minus the resolution problem, that I apparently caused. :)

I think linux nvidia defaults to vsync off, whereas windows nvidia defaults to vsync on.  Not sure if or how to change it, but that could be whats causing the tearing.  Your game has a locked rate, and your card has an unlocked rate. Cheers.

-Tres

---

### Post by penvzila on 2007-07-01
I have used the install scripts, compiled from source, and used the latest 64bit debs, and I still always get "Segmentation fault (core dumped)" when I use wine at all, including notepad and winecfg.

---

### Post by Enverex on 2007-07-01
Something is very, very wrong with your toolchain then, possibly your LibC6. Erm, you could try deleting your ~/.wine* folders first though.

---

### Post by fatbuttlarry on 2007-07-02
I had that issue too... I think its due to a missing file or folder.  I remember creating it.

My Error:

```
OSError: [Errno 2] No such file or directory: '/home/tres/.wine/dosdevices/c:/windows/profiles/tres'
```

My work around:

```
mkdir ~/.wine/dosdevices/c:/windows/profiles/$USER
```

or look in **.wine** and make sure the necessary folders are there.

I remember launching wineconfig and working from it's error messages.  Funny how it screws up like that... 
-Tres

---

### Post by scriminaci on 2007-07-06
I have the same problem... i installed 64 bit version of wine 0.9.40 from the wine repo...
When i run wineprefixcreate or winecfg
mario@mario-laptop:~$ wineprefixcreate 
Segmentation fault
mario@mario-laptop:~$ winecfg
Segmentation fault

I tried to erase the ~/.wine folder and reinstall the package but it did not work... I tried also the 0.9.40 32 bit version and the 0.9.39 64 bit version but the error is the same... 

Someone can help me?

---

### Post by Enverex on 2007-07-07
What version of Ubuntu are you using?

---

### Post by scriminaci on 2007-07-07
the problem is that I had install wine not long time ago and it worked; I have a turion 64 bit and ubuntu feisty 64 bit but then there was not a 64 bit version of wine so I used instruction in this page
[http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64)
and it worked fine.
But I had to reinstall ubuntu and I tried to install the 64 bit version with apt. But it does work, so I tried with the previous install method (forcing the installation of a 32 bit version and removing wine with apt-get --purge remove) but it also does work.

thanks for support
mario

---

### Post by fatbuttlarry on 2007-07-08
Again, I'm pretty sure it's a missing folder or symbolic link.  That was our issue, identical description (worked, then didn't).

Another thing you can try is WineTools.  It might help create those folders too.  I'm not sure how I got the missing folder/link from the error message... I probably should have documented it, since it was the reason I created this thread... :beer:

-Tres

---

### Post by Skrypt on 2007-07-09
> **NullHead said:**
> Feisty now has 64bit debs in the wine Repository. 
To be able to use the repository do this.
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

```
```
sudo apt-get update
```
```
sudo apt-get install wine
```
this worked for me.
I ran these commands but none of the directories seem to have created. There's no ./wine directory. When I run winecfg I receive this: 
> 
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/shelby', starting in the Windows directory.
Segmentation fault (core dumped)
I ran: 
```
mkdir ~/.wine/dosdevices/c:/windows/profiles/$USER
```
and couldn't create the directory either. 

What do I do now? =S

---

### Post by fatbuttlarry on 2007-07-09
dosdevices/c: has to be a symbolic link to drive_c in ~/.wine

Make sure to create all of the folders it says its missing.  There is some creation problem.  If it still won't let you create them, use sudo, then sudo chown to force ownership to yourself.

-Tres

---

### Post by Skrypt on 2007-07-10
> Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/skrypt', starting in the Windows directory.
wine: cannot find '/home/skrypt/Desktop/AIM/aim.exe'
Where am I supposed to create those? /home/skrypt? It looks like it's trying to reference .dll files. Do I need to download some or are they provided with wine?

---

### Post by fatbuttlarry on 2007-07-10
/home/skrypt is probably the directory you are trying to execute your command from, and the dos devices need to have symbolic links out of the wine directory too.

You should first make sure that the folder **dosdevices** and **drive_c** exist in **.wine**.

```

cd ~/.wine
mkdir drive_c
mkdir dosdevices

```

Then make a symbolic link to **drive_c** called **c**
```

ln -s ~/.wine/dosdevices c

```

Inside **.wine**, you should see three registry files.  Create them if they don't exist
```

touch system.reg
touch userdef.reg
touch user.reg

```

Now the dosdevices are all symbolic links too, so that you can access the places by drive letter.
```

cd dosdevices
ls -al

```

You should see something similar:
```

c: -> ../drive_c
d: -> /
e: -> /media/cdrom0
h: -> ~

```

You you should at least create c, d, and h if they don't exist, by using the same **ln -s** method above.

Note also, AIM 4.8 is the only version I could get working with wine.

-Tres

---

### Post by waddletron on 2007-07-10
Kilz, i don't see anything about it in your signature and the only wine packages in the repo for FF x86_64 are dummy packages. Yes I have all the repos enabled.

---

### Post by Enverex on 2007-07-10
You shouldn't do any of this, if it didn't happen automatically then something is broken.

Do "sudo rm -rf ~/.wine*" then run winecfg again.

---

### Post by fatbuttlarry on 2007-07-10
> **Enverex said:**
> You shouldn't do any of this, if it didn't happen automatically then something is broken.

Do "sudo rm -rf ~/.wine*" then run winecfg again.


He shouldn't **have** to do any of this.  But I deff got segfaults w/ a vanilla setup, and had to create some dirs.

-Tres

---

### Post by Skrypt on 2007-07-11
I don't know what to say other than to list this evenings failures.

> 
skrypt@Eos:~$ cd ~/.wine
[email]skrypt@Eos:~/.wine[/email]$ mkdir drive_c
[email]skrypt@Eos:~/.wine[/email]$ mkdir dosdevices
[email]skrypt@Eos:~/.wine[/email]$ ln -s ~/.wine/dosdevices c
[email]skrypt@Eos:~/.wine[/email]$ ls
c  dosdevices  drive_c
[email]skrypt@Eos:~/.wine[/email]$ touch system.reg
[email]skrypt@Eos:~/.wine[/email]$ touch userdef.reg
[email]skrypt@Eos:~/.wine[/email]$ touch user.reg
[email]skrypt@Eos:~/.wine[/email]$ cd dosdevices
[email]skrypt@Eos:~/.wine[/email]/dosdevices$ ls -al
total 8
drwxr-xr-x 2 skrypt skrypt 4096 2007-07-11 03:03 .
drwxr-xr-x 4 skrypt skrypt 4096 2007-07-11 03:04 ..
[email]skrypt@Eos:~/.wine[/email]/dosdevices$ ln -s ~/.wine/dosdevices d
[email]skrypt@Eos:~/.wine[/email]/dosdevices$ ln -s ~/.wine/dosdevices h
[email]skrypt@Eos:~/.wine[/email]/dosdevices$ ls -al
total 8
drwxr-xr-x 2 skrypt skrypt 4096 2007-07-11 03:07 .
drwxr-xr-x 4 skrypt skrypt 4096 2007-07-11 03:04 ..
lrwxrwxrwx 1 skrypt skrypt   29 2007-07-11 03:06 d -> /home/skrypt/.wine/dosdevices
lrwxrwxrwx 1 skrypt skrypt   29 2007-07-11 03:07 h -> /home/skrypt/.wine/dosdevices
[email]skrypt@Eos:~/.wine[/email]/dosdevices$ ln -s ~/.wine/dosdevices c
[email]skrypt@Eos:~/.wine[/email]/dosdevices$ cd ..
[email]skrypt@Eos:~/.wine[/email]$ ls -al
total 16
drwxr-xr-x  4 skrypt skrypt 4096 2007-07-11 03:04 .
drwxr-xr-x 32 skrypt skrypt 4096 2007-07-10 18:33 ..
lrwxrwxrwx  1 skrypt skrypt   29 2007-07-11 03:03 c -> /home/skrypt/.wine/dosdevices
drwxr-xr-x  2 skrypt skrypt 4096 2007-07-11 03:07 dosdevices
drwxr-xr-x  2 skrypt skrypt 4096 2007-07-11 03:03 drive_c
-rw-r--r--  1 skrypt skrypt    0 2007-07-11 03:04 system.reg
-rw-r--r--  1 skrypt skrypt    0 2007-07-11 03:04 userdef.reg
-rw-r--r--  1 skrypt skrypt    0 2007-07-11 03:04 user.reg
[email]skrypt@Eos:~/.wine[/email]$ winecfg
/home/skrypt/.wine/system.reg is not a valid registry file
/home/skrypt/.wine/userdef.reg is not a valid registry file
/home/skrypt/.wine/user.reg is not a valid registry file
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/skrypt/.wine', starting in the Windows directory.
Segmentation fault (core dumped)
[email]skrypt@Eos:~/.wine[/email]$ sudo rm -rf ~/.wine*
Password:
[email]skrypt@Eos:~/.wine[/email]$ winecfg
wine: creating configuration directory '/home/skrypt/.wine'...
Warning: could not find DOS drive for current working directory '', starting in the Windows directory.
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/skrypt/.wine'.
[email]skrypt@Eos:~/.wine[/email]$ wineserver: could not save registry branch to /home/skrypt/.wine-Q1YQSh/system.reg : No such file or directory
wineserver: could not save registry branch to /home/skrypt/.wine-Q1YQSh/user.reg : No such file or directory
[email]skrypt@Eos:~/.wine[/email]$ 


---

### Post by fatbuttlarry on 2007-07-11
I got some of those symbolic links wrong... sorry...

```

cd ~/.wine
ln -sf ~/.wine/drive_c c

```

Hopefully by now you understand the symbolic links...

Make sure these are accurate in dosdevices:

```

c: -> ../drive_c
d: -> /
e: -> /media/cdrom0
h: -> ~
```

Those colons in the names are needed.

Sorry for the confusion.

Also, this looks bazaar:

```
could not save registry branch to /home/skrypt/.wine-Q1YQSh/system.reg : No such file or directory
```

Not sure what **.wine-Q1YQSh** is.

Infact, we should probably start from scratch like **Enverest** said by removing and starting over.  That way we can build only the folders that are missing, and perhaps submit this as a bug in the 7.04 x86-64 release.

If you have SSH open on that box, I wouldn't mind working with you on this. 

-Tres

---

### Post by Skrypt on 2007-07-11
I'd greatly appreciate the help via SSH. (Though, to be honest, I'm a newb there, too!)

I used the remove command given but I'm inclined to believe wine is installed elsewhere and was before I started trying to ever install it. In the Add/Remove Pannel it's still showing.

---

### Post by fatbuttlarry on 2007-07-11
Thats good.  Wine is a unique program because it builds a windows drive and stuff.  Removing the folder in your directory just removes your personal files that wine uses.

You can completely remove wine with:

```

sudo apt-get remove wine

```

Then install it again with:

```

sudo apt-get install wine

```

The catch is, removing it an reinstalling it does no good if you're .wine folder is messed up, hence why he asked you to remove that.

Although you are a "noob", we all are in different ways.  The more ppl trying ubuntu the better!!!

-Tres

---

### Post by Skrypt on 2007-07-11
Hm... I've removed it all and reinstalled and followed the steps here to the T. How do we go about settings up the SSH now? =P

---

### Post by fatbuttlarry on 2007-07-12
> **Skrypt said:**
> Hm... I've removed it all and reinstalled and followed the steps here to the T. How do we go about settings up the SSH now? =P

```
sudo apt-get install ssh
```

or 

```
sudo apt-get install ssh-server
```

Something like that...

Once that's installed.

```
sudo adduser tfino
```

Email the password to fatbuttlarry at gmail.

If you have a router, make sure to forward port 22 to your computer's ip address. Cheers.

-Tres

---

### Post by givupnliv on 2007-07-14
I'm not sure if this qualifies as a new thread. I tried to install WINE on Feisty AMD64, it apparently didn't take. I am getting the following error msg when I run update manager:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

Any advice would be appreciated.  It is my understanding that if I can get wine running properly, i will be able to run cd-rom games on Feisty Fawn 64bit even though the cd's came only with windows drivers.. Is this correct?

---

### Post by NullHead on 2007-07-14
> **givupnliv said:**
> I'm not sure if this qualifies as a new thread. I tried to install WINE on Feisty AMD64, it apparently didn't take. I am getting the following error msg when I run update manager:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

Any advice would be appreciated.  It is my understanding that if I can get wine running properly, i will be able to run cd-rom games on Feisty Fawn 64bit even though the cd's came only with windows drivers.. Is this correct?

It looks like you didn't add repository's key to your system. so what you need to do is put this bit of code into your terminal. ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by fatbuttlarry on 2007-07-14
> **NullHead said:**
> It looks like you didn't add repository's key to your system. so what you need to do is put this bit of code into your terminal. ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

^-- He's right.

Yes, generally, your games will run from cdrom, depending on the game.  Wine just tricks the cd rom device drive to read from your actual linux cdrom drive.

What game it is?

-Tres

---

### Post by givupnliv on 2007-07-14
Thanx Nullhead, it looks like that may have done it.

My kids have several PC games.Now, i'm trying to install Diablo  II and I don't follow exactly what the instructions are telling me to do. Here is the instructs from the Ubuntu guide:

 How to run programs in Wine

    * Read #How to Install Wine 

Once Wine is installed, you can run programs in Wine by using the terminal (Applications > Accessories > Terminal). Then if you want to try to install/run a program under Wine do this:

1. Download an EXE file.

2. Navigate to the directory of the EXE file using the cd command in the terminal.

3. Type in "wine EXENAME.exe" and it will then run the install.

4. Hope the install works.

5. Hope the program works. 

I don't understand how to download the cd-rom, and how do I "navigate" to  the EXE file?
I understand how to put commands into the terminal as long as I know what the command is, but it's almost like I need a guide on how to understand the instructions.

I put the cd in the drive, i did number 3 above, but it stated that it could not find the file. Also, this particular game is an expansion set(Battle Chest), so there are several discs that need to be run. Is there a Ubuntu(FeistyFawn AMD64) guide available that is oriented more for the Linux illiterate. I am having trouble with the general terminology. Thanx in advance for any tips or advice.

---

### Post by givupnliv on 2007-07-14
> **fatbuttlarry said:**
> ^-- He's right.

Yes, generally, your games will run from cdrom, depending on the game.  Wine just tricks the cd rom device drive to read from your actual linux cdrom drive.

What game it is?

-Tres

DiabloII It's my sons' game.

---

### Post by NullHead on 2007-07-14
> **givupnliv said:**
> Thanx Nullhead, it looks like that may have done it.

My kids have several PC games.Now, i'm trying to install Diablo  II and I don't follow exactly what the instructions are telling me to do. Here is the instructs from the Ubuntu guide:

 How to run programs in Wine

    * Read #How to Install Wine 

Once Wine is installed, you can run programs in Wine by using the terminal (Applications > Accessories > Terminal). Then if you want to try to install/run a program under Wine do this:

1. Download an EXE file.

2. Navigate to the directory of the EXE file using the cd command in the terminal.

3. Type in "wine EXENAME.exe" and it will then run the install.

4. Hope the install works.

5. Hope the program works. 

I don't understand how to download the cd-rom, and how do I "navigate" to  the EXE file?
I understand how to put commands into the terminal as long as I know what the command is, but it's almost like I need a guide on how to understand the instructions.

I put the cd in the drive, i did number 3 above, but it stated that it could not find the file. Also, this particular game is an expansion set(Battle Chest), so there are several discs that need to be run. Is there a Ubuntu(FeistyFawn AMD64) guide available that is oriented more for the Linux illiterate. I am having trouble with the general terminology. Thanx in advance for any tips or advice.

well you need to understand some things first. Step three wants you to run the installer ... the ".EXE" so you need to know where that file is located. well you know it's on the cd-rom so look at the cdrom from the terminal by typing ```
cd /media/cdrom/
``` now what you just did is change directories to look at the cdrom ... now what you don't see any of the files on the cd. To look at them type```
ls
``` then do step 3

---

### Post by givupnliv on 2007-07-14
It just keeps saying "module not found" no matter how I type the file name as instructed in step 3. I'm not doing something right.

---

### Post by fatbuttlarry on 2007-07-15
Well, the howto almost looks like its written from some downloaded EXE.

I'm sure you know what an exe is, and i'm sure you can figure out how to 'cd' to it.

Since I've never tried DiabloII + wine, you may want to see if you can find any success stories.

Generally, wine will automatically map your cdrom drive (usually D: or E:) to /media/cdrom or whatever.

So, essentially, if it was D:\Setup.exe in windows, you could ```
wine d:\\setup.exe
```

Of course, that assumes a lot, but you shoudl be able to see what the exe is called by popping the cdrom in and clicking the icon that would normally appear on your ubuntu/kubuntu desktop. :popcorn:

-FBL

---

### Post by penvzila on 2007-07-19
> **Enverex said:**
> Something is very, very wrong with your toolchain then, possibly your LibC6. Erm, you could try deleting your ~/.wine* folders first though.

Whatever it was... the amd64 packages from the wine repository worked when I reinstalled feisty on the same laptop.

---

### Post by fatbuttlarry on 2007-07-19
> **penvzila said:**
> Whatever it was... the amd64 packages from the wine repository worked when I reinstalled feisty on the same laptop.thanks for the update! :popcorn::popcorn:

---

### Post by fatbuttlarry on 2007-07-22
Very bazaar.  It's trying to use a folder called ".wine-DLtbAz"

Upon running it a second time, I get a new folder: ".wine-Pwqn6t"
> wine: creating configuration directory '/home/tres/.wine'...
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/tres/.wine'.
tres@sysadmin-desktop:~$ wineserver: could not save registry branch to /home/tres/.wine-DLtbAz/system.reg : No such file or directory
wineserver: could not save registry branch to /home/tres/.wine-DLtbAz/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/tres/.wine-DLtbAz/user.reg : No such file or directory

---

### Post by WIGGMPk on 2007-07-22
Running wineconfig

> sysadmin@sysadmin-desktop:~$ wineconfig
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)
Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 3547, in <module>
    wineconfigapp = WineConfigApp()
  File "/usr/bin/wineconfig", line 118, in __init__
    self.CreateWindowsInstall()
  File "/usr/bin/wineconfig", line 318, in CreateWindowsInstall
    winewrite.SetDriveMappings(drives)
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 60, in SetDriveMappings
    SetShellLinks(drives[26:])
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 63, in SetShellLinks
    existingshelllinks = os.listdir(wineread.winepath + "/dosdevices/c:/windows/profiles/" + os.environ['USER'])
OSError: [Errno 2] No such file or directory: '/home/sysadmin/.wine/dosdevices/c:/windows/profiles/sysadmin'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 3547, in <module>
    wineconfigapp = WineConfigApp()
  File "/usr/bin/wineconfig", line 118, in __init__
    self.CreateWindowsInstall()
  File "/usr/bin/wineconfig", line 318, in CreateWindowsInstall
    winewrite.SetDriveMappings(drives)
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 60, in SetDriveMappings
    SetShellLinks(drives[26:])
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 63, in SetShellLinks
    existingshelllinks = os.listdir(wineread.winepath + "/dosdevices/c:/windows/profiles/" + os.environ['USER'])
OSError: [Errno 2] No such file or directory: '/home/sysadmin/.wine/dosdevices/c:/windows/profiles/sysadmin'
sysadmin@sysadmin-desktop:~$ ICE default IO error handler doing an exit(), pid = 31295, errno = 0



---

### Post by fatbuttlarry on 2007-07-22
Ok, I have your x-server exported to my XP-64 box:

[[img]http://img509.imageshack.us/img509/2039/untitledlc3.th.png[/img]](http://img509.imageshack.us/img509/2039/untitledlc3.png)

Now i'm going to try getting notepad loaded! :)

-Tres

---

### Post by fatbuttlarry on 2007-07-22
```
tres@sysadmin-desktop:~$ wineconfig
kbuildsycoca running...
DCOP Cleaning up dead connections.
Segmentation fault (core dumped)
Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 3547, in <module>
    wineconfigapp = WineConfigApp()
  File "/usr/bin/wineconfig", line 118, in __init__
    self.CreateWindowsInstall()
  File "/usr/bin/wineconfig", line 318, in CreateWindowsInstall
    winewrite.SetDriveMappings(drives)
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 60, in SetDriveMappings
    SetShellLinks(drives[26:])
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 63, in SetShellLinks
    existingshelllinks = os.listdir(wineread.winepath + "/dosdevices/c:/windows/profiles/" + os.environ['USER'])
OSError: [Errno 2] No such file or directory: '/home/tres/.wine/dosdevices/c:/windows/profiles/tres'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 3547, in <module>
    wineconfigapp = WineConfigApp()
  File "/usr/bin/wineconfig", line 118, in __init__
    self.CreateWindowsInstall()
  File "/usr/bin/wineconfig", line 318, in CreateWindowsInstall
    winewrite.SetDriveMappings(drives)
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 60, in SetDriveMappings
    SetShellLinks(drives[26:])
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 63, in SetShellLinks
    existingshelllinks = os.listdir(wineread.winepath + "/dosdevices/c:/windows/profiles/" + os.environ['USER'])
OSError: [Errno 2] No such file or directory: '/home/tres/.wine/dosdevices/c:/windows/profiles/tres'
ICE default IO error handler doing an exit(), pid = 31898, errno = 0

```

---

### Post by WIGGMPk on 2007-07-22
> /home/sysadmin/.wine/userdef.reg is not a valid registry file
/home/sysadmin/.wine/user.reg is not a valid registry file


Get this error when running winecfg any thoughts?

Also, wine.conf was not created on installation. wineconfig screams with reg edit cannot export error's.

Is there a tool to create a wine.conf ?? shooting the dark here lol


Thanks in advance

---

### Post by givupnliv on 2007-07-22
i've followed every bit of advice i've been given. wine is installed, it has a directory on the applications drop down menu that shows the pc game i downloaded, but it will not play it. i have removed and reinstalled wine at least 3 times and i've tried various games. i can not get it to play a game at all. does anyone have a surefire way of playing Windows based pc games on ubuntu feisty fawn adm64 without all this drama?

---

### Post by fatbuttlarry on 2007-07-22
Well, yes.  There's this non-free application called Cadega.  It works great and plays games out of the box, and they support 64-bit.  I think it's between 20-30 bucks a year.  It has a free 30 day demo that would be worth trying.

Cadega has contributed a huge amount of open source code to the Wine repository over the years, so essentially giving them money will benefit us all. :)

I'm still working with a guy through ssh/putty to get documented once and for all the cause of this problem.

We are both running multi-core 64 bit AMD with Nvidia graphics cards.  

-Tres

---

### Post by fatbuttlarry on 2007-07-23
Updated.  Please see first post.

-Tres

---

### Post by Myzrael on 2007-07-23
WINE installed fine and runs fine. Just one problem (big one for me). When I run a game fullscreen my keyboard inputs don't get focus on the game program. This is a showstopper because this means that fullscreen I have no keyboard input which makes it impossible to game ofcourse.
Anyone who can help me with this? Sure it's a simple solution but I can't seem to find it.

---

### Post by fatbuttlarry on 2007-07-23
what type of keyboard?  Standard 101/US?  generally, i'd say click on the game, but i'm sure you've tried that.  What game is it?

---

### Post by Myzrael on 2007-07-23
Standard keyboard. Problem is that the game doesn't get focus while it should in fullscreen.....It's an old bug, documented and still not fixed. Only happens in true full screen mode. Happen on Counter Strike/ Counter Strike Source and other games. I bypassed the problem now by launching the game without a windows manager in a separate X session, and once the game is launched, hiding the windows behind it so that Wine won't make any focus errors.

---

### Post by WIGGMPk on 2007-07-24
> **fatbuttlarry said:**
> Updated.  Please see first post.

-Tres

Also, before running:

winecfg
wineconfgi

Make sure you run:

wineprefixcreate

Or else it will be upset about missing files:

userdef.reg


At least for me

---

### Post by fatbuttlarry on 2007-07-24
Weird.  We play Half-Life and CS 1.6 with out any issues like this.  Is it an ATI or NVIDIA specific problem?

We've fixed some resolution problems by making sure to run the game in the same color depth as the desktop.

-Tres

---

### Post by fatbuttlarry on 2007-07-24
> **WGGMk said:**
> Also, before running:

winecfg
wineconfgi

Make sure you run:

wineprefixcreate

Or else it will be upset about missing files:

userdef.reg


At least for me
+added :)

---

### Post by Myzrael on 2007-07-28
Any tips why Counter Strike source runs like a snail here? Using a Nvidia card with a fast computer, no problems in XP normally, and the latest version of Wine and Ubuntu Feisty 64bit. Counter strike 1.6 runs just fine and normal speed but Source doesn't. It looks like source is being rendered in software completly because there are absolutly no fancy graphics anywhere. How to fix this?
I think the problem is DirectX because Counter Strike 1.6 only runs in -gl mode as well.

---

### Post by fatbuttlarry on 2007-07-29
There's a few threads/pages with a tutorial on getting the source engine to run with wine... have you gone through any?

Here's a small howto: (scroll down)
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

-Tres

---

### Post by Myzrael on 2007-07-29
I've tried every manual I could find with google so yep......................I sadly have.

---

### Post by givupnliv on 2007-07-29
I've been all over the internet(google, winehq, ubuntu guide, others) and I've spent a ridiculous amount of time on these forums. As I sit here with at least 9 different cd-rom games, and I've tried every bit of advice I could find, I have not been able to play even one single game, not even a trivia game where there is no graphics. The last advice I was given was to throw money at it and buy cedega. If you must pay, you may as well stick with Windows. By now, Ubuntu should have a program built in to automatically load anything made for windows or even mac. I have built more than 15 gaming pc's and loaded Vista on 4 of them in the time I spent trying to figure out how to play a video game on ubuntu. Thus , it is NOT ready for the desktop, It should be doing this out of the box or at least with a simple download. It is safe to say that at this point in the evolution of the home computer world, there are minimum expectations the MAJORITY of computer users have and ubuntu does not live up to them by any stretch of the imagination. You should absolutely not have to spend hours each day for several days to attempt to figure out how to perform simple tasks that XP and yes, even Vista can do without even having an internet connection. It makes no difference what os the cd's or drivers were created for, any and all systems should by now have a very simple program to convert them to the proper language. I read all these posts about how Vista is such a mess. I've loaded 4 and you can play any cd-rom game on anyone of those systems. wine only seems to work for those that have no life outside of their pc. Poor me, I have a life.

---

### Post by Myzrael on 2007-07-29
uh givupnliv.
The fact that wine doesn't work for you has nothing to do with Ubuntu.....

That said. I'm struggling with WINE myself but I think using ENVY to install my Nvidia drivers had a lot to do with my problems. I run GLXgears roughly 6 times faster (I know it's a bad benchmark) now that I installed the Nvidia drivers from the Nvidia website itself and just let Nvidia handle my Xorg files etc. Everything works great now and is much faster! 
So maybe CCS will work now ;) Time to see tomorrow because the wine reinstall is finished but Steam needs to download CCS.

---

### Post by PresidentJFJ on 2007-07-29
Well I've read through this whole thread and not one thing has made wine work, even winecfg. I have no idea why. Every single time I try to use wine i get "segmentation fault(core dumped)". I managed to open wineconfig by creating the folder /profiles/jack in the dosdevices directory, but that's it! Nothing else even does anything. i get these errors that say
HKEY_CURRENT_USER\Software\Wine\about 8 of these errors.
Is there a way to install wine on 64 bit that isn't from the repos so I won't have all these problems. This is driving me nuts.

---

### Post by fatbuttlarry on 2007-07-29
> **givupnliv said:**
> I've been all over the internet(google, winehq, ubuntu guide, others) and I've spent a ridiculous amount of time on these forums. As I sit here with at least 9 different cd-rom games, and I've tried every bit of advice I could find, I have not been able to play even one single game, not even a trivia game where there is no graphics. The last advice I was given was to throw money at it and buy cedega. If you must pay, you may as well stick with Windows. By now, Ubuntu should have a program built in to automatically load anything made for windows or even mac. I have built more than 15 gaming pc's and loaded Vista on 4 of them in the time I spent trying to figure out how to play a video game on ubuntu. Thus , it is NOT ready for the desktop, It should be doing this out of the box or at least with a simple download. It is safe to say that at this point in the evolution of the home computer world, there are minimum expectations the MAJORITY of computer users have and ubuntu does not live up to them by any stretch of the imagination. You should absolutely not have to spend hours each day for several days to attempt to figure out how to perform simple tasks that XP and yes, even Vista can do without even having an internet connection. It makes no difference what os the cd's or drivers were created for, any and all systems should by now have a very simple program to convert them to the proper language. I read all these posts about how Vista is such a mess. I've loaded 4 and you can play any cd-rom game on anyone of those systems. wine only seems to work for those that have no life outside of their pc. Poor me, I have a life.

I'm sure 50% of the worlds population can feel your pain.

I don't disagree that there should be some form of binary standard (which Java pretty much is right now), but the gaming companies don't create versions for Linux because they think there isn't a demand for it.

The windows executable is a very complicated and closed-source standard, usually created with some proprietary (and usually Microsoft) product.  The gaming companies are scared to release their source code due to intellectual rights, and Microsoft won't help matters because they don't want people to move away from purchasing their product.

If someone told you that Ubuntu was a direct replacement for windows, then yes, you were lied to.

But if someone told you that there was a free alternative to using your desktop computer that had all of the capabilities of windows, then that person told the truth.

Linux is built from the same type of people that get frustrated with **** that doesn't work.  Ubuntu is helping change the stereotype of "linux is only for guru's", but it won't happen over night.

If you want to do something and feel good about it, stick with the free world and contribute what you know and what you've tried, because despite first glance, almost everyone that uses Linux now needs help getting something working properly.

If you want games to run out-of-the box with linux, yes, you have to pay some money still.  If you'd rather pay $200+ for closed-source software like Vista, then keep paying more money.  At least the CrossOver Office and Cedega crew contribute code back.  Buying vista is like paying 20x the amount to get your car fixed, when you could probably do it yourself, but the mechanic never told you what went wrong or what got fixed.

Ubuntu works great and it's completely free, it just needs more community help.  And by free, you must understand that it's more than just free to obtain.  It's also free to modify and distribute and even free to sell (yes, you can sell it).

The wine project (what you're having the most difficulties with) is amazing for what it does.  I play Half-Life and counterstrike 1.6 pretty well now, and hopefully soon, I can get rid of Windows all together.

As for the guy trying HL2/CS Source, I know there's a lot of success stories.  Please post up some steps you've tried and some errors you're recieving so you can get the community feedback thats keeping ubuntu alive.

I've seen some tweaks that say it runs better with DX7 or DX8, etc, but you haven't elaborated on exactly what you've tried and what you haven't.

-Tres

---

### Post by WIGGMPk on 2007-08-01
> **PresidentJFJ said:**
> Well I've read through this whole thread and not one thing has made wine work, even winecfg. I have no idea why. Every single time I try to use wine i get "segmentation fault(core dumped)". I managed to open wineconfig by creating the folder /profiles/jack in the dosdevices directory, but that's it! Nothing else even does anything. i get these errors that say
HKEY_CURRENT_USER\Software\Wine\about 8 of these errors.
Is there a way to install wine on 64 bit that isn't from the repos so I won't have all these problems. This is driving me nuts.

The walk through that fatbuttlarry described on the first page should be sufficient enough to install and run on amd64. Provided that your segmentation faults are similar to the one's we were having.


Pay close attention to the commands you enter in sequence.

And dont forget to reinstall your graphics drivers. May not work for none nVidia cards.

Please post your results.

---

### Post by PresidentJFJ on 2007-08-01
I hate to say it, but I can't figure out how to use Linux at all anymore. I tried all the stuff on the earlier pages, and none of it helped. I tried to go back to 32 bit Ubuntu but now my nVidia drivers won't install properly. I did it the same way every time and it has just stopped working. Every time I install them now, it screws up my xconfig file and I can't boot up Ubuntu without reverting back to my old xconfig file then reinstalling the drivers. The drivers work for the rest of the session then I can't reboot. If anyone can tell me how to fix that problem that would be great. It's funny, Linux worked perfectly until I tried to use windows programs on it, and I had to fix my boot record when I uninstalled Linux. No wonder there are so many OS flame wars.

---

### Post by fatbuttlarry on 2007-08-01
> **PresidentJFJ said:**
> I hate to say it, but I can't figure out how to use Linux at all anymore. I tried all the stuff on the earlier pages, and none of it helped. I tried to go back to 32 bit Ubuntu but now my nVidia drivers won't install properly. I did it the same way every time and it has just stopped working. Every time I install them now, it screws up my xconfig file and I can't boot up Ubuntu without reverting back to my old xconfig file then reinstalling the drivers. The drivers work for the rest of the session then I can't reboot. If anyone can tell me how to fix that problem that would be great. It's funny, Linux worked perfectly until I tried to use windows programs on it, and I had to fix my boot record when I uninstalled Linux. No wonder there are so many OS flame wars.Great you asked.... This is a similar issue... it should be placed in the instructions.  There's a line in a second config file that needs to be commented out or else the nvidia card wont work after a reboot... let me try to find it!!!

-Tres

---

### Post by fatbuttlarry on 2007-08-01
Crap... couldn't find it...

I did find this however: (appended link to first post too)

> Now let’s make sure that nvidia module isn’t inserted into the kernel.

lsmod | grep nvidia

Ideally, the results should be nothing. If you get anything that even remotely resembles this …

nvidia 4713780 22
i2c_core 22784 2 i2c_ec,nvidia
agpgart 35400 2 nvidia,intel_agp

then pull it out with this.

sudo rmmod nvidia

If for some reason Ubuntu says that module is in use, X is probably still running. Go back and kill GDM again, and make sure it’s gone.

When that’s settled, install the packages you need to patch and build the driver.

-Tres

---

### Post by PresidentJFJ on 2007-08-01
Thanks for the help, but im going away tomorrow for 2 weeks so I won;thave time to get Linux back up and running. I will definately try that when I get back though. Thanks a lot!

---

### Post by fatbuttlarry on 2007-08-02
:twisted:

---

### Post by michaelfitzi on 2007-08-02
Hello, 
All that is keeping me tied to Windows is to play WoW. I have been trying to install and get Wine working, but keep failing.  There isn't a an apt-get somewhere that I can do that would get it set up for WoW?!?!? 
The post above is saying to mess around with my nvidia drivers, that scares me, cause it took me a couple of days to get them set up and to get Beryl set up.  

All I need is a magic "self" install for WoW.

I know, I am "whining" sorry... I will keep trying, tho. As I am very happy with Ubuntu!
Thanks!

---

### Post by fatbuttlarry on 2007-08-02
> **michaelfitzi said:**
> Hello, 
All that is keeping me tied to Windows is to play WoW. I have been trying to install and get Wine working, but keep failing.  There isn't a an apt-get somewhere that I can do that would get it set up for WoW?!?!? 
The post above is saying to mess around with my nvidia drivers, that scares me, cause it took me a couple of days to get them set up and to get Beryl set up.  

All I need is a magic "self" install for WoW.

I know, I am "whining" sorry... I will keep trying, tho. As I am very happy with Ubuntu!
Thanks!
What steps have you tried?

Latest WoW with wine tricks:

[http://appdb.winehq.org/appview.php?iVersionId=8136](http://appdb.winehq.org/appview.php?iVersionId=8136)

Any steps you don't understand just ask!!!

Scroll down to where it says **New Users**

-Tres

---

### Post by ves on 2007-08-10
I had the same problem as first poster, namely a segmentation fault whenever I tried to run winecfg or wine notepad. After reading this thread it looked like my graphics drives could be the problem.

The drivers I use are from the NVIDIA site, since I have a 8600GT and they're not supported by the restricted drivers manager yet. I installed them by following [this guide]("http://www.robdian.co.uk/content/view/56/"). My problem was most probably that at some point I updated to the latest kernel by running the update manager.

After reading this thread I tried to install the video drivers again by running "sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run" and lo and behold, wine is working perfectly now. It could be that I answered some question in the installer differently this time, but since it says it needs to compile headers for my kernel I'm guessing my updated kernel caused the problems.

---

### Post by fatbuttlarry on 2007-08-10
> **ves said:**
> I had the same problem as first poster, namely a segmentation fault whenever I tried to run winecfg or wine notepad. After reading this thread it looked like my graphics drives could be the problem.

The drivers I use are from the NVIDIA site, since I have a 8600GT and they're not supported by the restricted drivers manager yet. I installed them by following [this guide]("http://www.robdian.co.uk/content/view/56/"). My problem was most probably that at some point I updated to the latest kernel by running the update manager.

After reading this thread I tried to install the video drivers again by running "sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run" and lo and behold, wine is working perfectly now. It could be that I answered some question in the installer differently this time, but since it says it needs to compile headers for my kernel I'm guessing my updated kernel caused the problems.Another one bites the dust! Thanks for the update!  Make sure it works after a reboot!

-Tres

---

### Post by revenant138 on 2007-08-20
I used the above fix and it worked great. After many, many hours of frustration it was easy-peasy.

---

### Post by fatbuttlarry on 2007-08-20
> **revenant138 said:**
> I used the above fix and it worked great. After many, many hours of frustration it was easy-peasy.

Yes!  Long live ubuntu! :)

---

### Post by oscarsfriend on 2007-08-26
From way back in post one...

> **fatbuttlarry said:**
> 
Then reinstall your NVIDIA driver.
Not sure why, but this seems to fix it.


I think I know why (not sure if anyone has already mentioned this).  I had the same problem, and I also had problems with google earth segfaulting.  When I reinstalled my nvidia driver (had to do this as the first step), it asked me if I wanted to install 32bit compatibility libraries (or something like that).  Now, I am pretty sure I wasn't asked that when I installed the first time around -- most likely because I didn't install the 32bit compatibility stuff 'til long after I installed the nvidia drivers.  After this I just copied my ~/.wine across from my old machine, and everything worked fine.  Google earth also works fine, with no fudges, as well.

---

### Post by fatbuttlarry on 2007-08-27
> **oscarsfriend said:**
> From way back in post one...



I think I know why (not sure if anyone has already mentioned this).  I had the same problem, and I also had problems with google earth segfaulting.  When I reinstalled my nvidia driver (had to do this as the first step), it asked me if I wanted to install 32bit compatibility libraries (or something like that).  Now, I am pretty sure I wasn't asked that when I installed the first time around -- most likely because I didn't install the 32bit compatibility stuff 'til long after I installed the nvidia drivers.  After this I just copied my ~/.wine across from my old machine, and everything worked fine.  Google earth also works fine, with no fudges, as well.

:guitar:  Sounds plausible.  Cheers.

---

### Post by cogitordi on 2007-08-27
I followed the simple instructions in this document and I have Wine running in Ubuntu Feisty/AMD64 for the first time ever:
[https://help.ubuntu.com/community/WineForAMD64](https://help.ubuntu.com/community/WineForAMD64)

There are a few old M-Windows applications that I like to use and I am also running 32-bit Firefox for Windows under Wine so I can see some Flash-based content (Apple Movie Trailers, Youtube). 

I've donated to the Wine project and you should too!

---

### Post by oscarsfriend on 2007-08-27
In the interest of not diverting the thread, I'll keep this brief...

> **cogitordi said:**
>  I am also running 32-bit Firefox for Windows under Wine so I can see some Flash-based content (Apple Movie Trailers, Youtube). 

I have 64bit firefox on Ubuntu Feisty working with Flash, and Apple movie trailers, Youtube, etc. No need for wine here.  Followed this guide to get flash working: [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727) .  Installed firefox mplayer plugin, and codecs from medibuntu repository to get video working: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) .

---

### Post by Kilz on 2007-08-27
> **oscarsfriend said:**
> In the interest of not diverting the thread, I'll keep this brief...



I have 64bit firefox on Ubuntu Feisty working with Flash, and Apple movie trailers, Youtube, etc. No need for wine here.  Followed this guide to get flash working: [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727) .  Installed firefox mplayer plugin, and codecs from medibuntu repository to get video working: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) .

If you want flash running, [I have a better link,]("http://ubuntuforums.org/showthread.php?t=476924") it will take all of 10 seconds.

---

### Post by fatbuttlarry on 2007-08-27
Good links!  Keep them coming.  Off-topic is ok when its to help others!

-Tres

---

### Post by creatorlarry on 2007-12-20
Though it seemed bizarre to me, but it really worked. Thank you very much.
While reinstalling, the driver installer did say some of my previous installed file was changed. I am just so interested which part of wine would have something to do with the nvidia driver. (I'm using beta driver from the nvidia)

---

### Post by fatbuttlarry on 2007-12-20
Great!  Thanks for posting!

I upgraded to Gutsy (7.10), and I'm using the pre-packaged drivers with success.  I'll explore the ones from nVidia if I read some performance gains (I can't imagine how lol).

Cheers.

-Tres

---

### Post by Artemis3 on 2008-01-14
Weird but true. Just reinstalling the same Nvidia drivers, and choosing the same options (don't download kernel, don't reconfig xorg, the rest default) cured wine segfaults.

I'm using Gutsy x64 with an 8800gt; wine 0.9.53 from [budgetdedicated.com repositories](http://www.winehq.org/site/download-deb).

---

### Post by fatbuttlarry on 2008-01-14
Cheers.

-FBL

---

