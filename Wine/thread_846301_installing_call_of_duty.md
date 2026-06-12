---
title: "installing call of duty"
date: 2008-07-01
forum: Wine
---

### Post by jwalters on 2008-07-01
I see in a thread that there asre guys actually playing COD.......how in the world do you install and play it?

I can't get the second disk to upload at all........first one seems to install......won't reject, but that's just a small command to make that happen.

Put is disk 2 and the screen asks for disk one all over again........

I've been trying on and off now for about two months..........even with the latest edition of ubuntu it is samo samo.......

---

### Post by brazemcee on 2008-07-03
Type wine /pathtocdrom/setup.exe to install the game.
You need a 'no-cd patch' from Megagames to play the game.
Typewine codsp.exe in the installation directory for singleplayer or wine codmp.exe for multiplayer.

/pathtocdrom/ is your cdrom. You should replace it with your drive location.

Source: Frank's corner

---

### Post by cogadh on 2008-07-03
Actually, that won't work, as the problem is you can't swap the first CD back at the end of the install. In order to get CoD installed properly, you need to use the Loki installer for the game, which can be found here:
[http://mirrors.reallan.net/pub/games/liflg/Call%20of%20Duty/call.of.duty_1.5-english.run](http://mirrors.reallan.net/pub/games/liflg/Call%20of%20Duty/call.of.duty_1.5-english.run). Right-click the link and choose "Save link as..."

EDIT - You may still need to use a cracked .exe to run the game, I can't remember if Wine's copy protection support is sufficient to run CoD.

EDIT2 - I just checked with my copy and I did not need a crack.

---

### Post by jwalters on 2008-07-07
What do you do with the page you directed me to......it seemed like it went on forever. Do you wait till it laods completely and then cut/paste?

Where do you paste all the code?....and what do you do after you do that...?...and what about cod united offensive......thanks....

---

### Post by cogadh on 2008-07-07
Re-read my post, I said right-click the link and choose "Save link as...". Don't just click on the link, it will load a really huge text file that you technically could copy/paste, but why bother when you can just save the text file itself.

After you save the file, it is a simple matter of putting in your CoD install CD, marking the saved file as executable and then running it:
```
chmod +x call.of.duty_1.5-english.run
./call.of.duty_1.5-english.run
```
Once that finishes, the game is installed. The installation will put two launch scripts in your home directory, codsp and codmp, one for single-player games and one for multiplayer games. To run them, just open a terminal and do this:
```
bash codsp
OR
bash codmp
```
You can create a shortcut in the Applications menu that will do the same.

The first time you launch multiplayer, it will take a really long time to load. Once it has loaded, you will need to enter your CD key in order to connect to any multiplayer servers. However, PunkBuster does not work in Wine, so you can only play on servers that are not PunkBuster enabled.

As for UO, since the game is not installed through normal Wine means, none of the registry entries that the UO installer looks for are present, and the install will fail to run, claiming you do not have CoD installed (if you try to install CoD through normal Wine means, the same thing happens anyway). There is supposedly a way to use the CoD install script to install it, but I do not know how to do that. I have also heard that UO can be installed by simply copying the necessary files off of the install CDs into CoD's install directory, but I've never tried it myself.

---

### Post by jwalters on 2008-07-08
thank you very much........I now have cod up and running..........what about cod2?..........same thing?

---

### Post by cogadh on 2008-07-08
There is no installer script for CoD2, but it is not required. You should be able to install it normally by mounting the CD and running "wine /media/cdrom/setup.exe". If it doesn't let you swap CDs (does CoD2 install from a DVD?), then just open another terminal and run "wine eject D:".

---

### Post by Drk Guy on 2008-07-08
There is no need for stupid loki installers, they suck, anyway:

winepath -w /path/to/installer/exe #This will spit out a win-like path for running the exe file
wine 'What winepath spitted out'
#When it asks for 2nd cd, as far as you won't believe it:
wine eject -u #Remember the -u, then umount like a normal cd and mount next cd and continue

Enjoy!

---

### Post by jwalters on 2008-07-10
This is what happened.

 something about the cd key check Windows has for their software.(which I have.) 

I already installed them before, but something went wrong and now it seems to quit before asking. 

I tried deleting the whole cod2 and start over, but it doesn't seem to delete entirely no matter what I do.



jwalters@jwalters-desktop:~$ wine /media/cdrom/setup.exe
fixme:advapi:LookupAccountNameW (null) L"jwalters" (nil) 0x32be7c (nil) 0x32be80 0x32be74 - stub
fixme:advapi:LookupAccountNameW (null) L"jwalters" 0x138d18 0x32be7c 0x13c578 0x32be80 0x32be74 - stub
err:msi:ITERATE_DuplicateFiles Failed to copy file L"C:\\Program Files\\Common Files\\InstallShield\\Driver\\9\\Intel 32\\IDriver.exe" -> L"C:\\Program Files\\Common Files\\InstallShield\\Driver\\9\\Intel 32\\", last error 80
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 2 ignored L"CreateFolder" table values
fixme:advapi:LookupAccountNameW (null) L"jwalters" (nil) 0x33cecc (nil) 0x33ced0 0x33cec4 - stub
fixme:advapi:LookupAccountNameW (null) L"jwalters" 0x16eb58 0x33cecc 0x16db18 0x33ced0 0x33cec4 - stub
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x10040
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x10040
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x10040
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3200-00001e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3200-00001e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3200-00001e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3200-00001e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3200-00001e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3200-00001e000000}

---

