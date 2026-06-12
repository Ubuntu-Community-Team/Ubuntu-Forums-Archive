---
title: "HOWTO Dual-Boot WoW with one install"
date: 2012-06-06
forum: Wine
---

### Post by cwwilson721 on 2012-06-06
If you're like me, you play WoW in both Linux/wine and in Windows. Why? Because, like it or not, Windows does a better job of updating, and various addon managers just plain work in Windows, and not in Linux. Also, my son plays WoW in Linux. For those keeping track, in a 'normal' setup, that is 3 WoW installs of over 18GB each. While you can 'consolidate' a 'universal' WoW install in Linux to just one for everybody, that would leave at least a total of 2 installs, one in Linux, one in Windows. Since most Windows installs use the NTFS Filesystem, 'linking' your WoW/wine install to that leads to errors and VERY slow gameplay. What to do?

***[SIZE="3"]SETUP[/SIZE]***

[SIZE="3"]**_Partitions:_**[/SIZE] 
Have an 'extra' FAT32 Partition that both Windows and Linux can see and use. In my case, I just added a 100GB one in an extended partition. In Windows, that would be the end of it. But in Linux, you must have the correct options in /etc/fstab for the partition to be writable by all users.

My example fstab entry for my fat32 partition is like this:
```
UUID=971F-167F  /Data32         vfat   [COLOR="RoyalBlue"]user,rw,umask=111,dmask=000[/COLOR] 0       0
```
Note the part in blue. That is the options that allow all users to read/write to the partition for Fat32. It mounts my partition to /Data32.

[SIZE="3"]**_Wine:_**[/SIZE] 
Install the latest wine by typing (in a terminal)
```
sudo apt-get install wine1.4
```
After install, type (in terminal)
```
winecfg
```
Wincfg sets up your 'basic' wine install, with the 'generic' dlls, registry, etc. At this time, you should set your default install as 'Windows XP' (that helps as far as sound in WoW goes), and then go to your 'Drives' tab.

In the Drives section, you have a bunch of drives in there. Personally, I do NOT want Windows programs (and possibly virus's) to have access to ANY part of my Linux install, so I delete all but the 'C:\' drive. After that, I create a "D:\" drive that points to my Fat32 partition. That comes in handy later.

[SIZE="3"]**_Video:_**[/SIZE] 
If you have a Intel Chipset/Graphics, good luck. Search this forum on how to get those working. For ATi/AMD and Nvidia, make sure your "Additional Drivers" are installed for your graphics. 

**_[SIZE="3"]Windows/WoW:[/SIZE]_**
Install WoW as you normally would in Windows, except have it install to your Fat32 Partition (in my case, drive 'D:').
After it finishes in Windows, try it out, make sure it works.

That's it for initial setup.

Next part: Linking Linux/WoW/wine to your Windows WoW install

---

### Post by cwwilson721 on 2012-06-06
***[SIZE="4"]Setting up wien/Linux to use the Windows WoW install[/SIZE]***

Now that you have the basic setup done, it's time to get wine/Linux to 'play nice' with Windows.

Generally, I recommend to use opengl with WoW/wine, but for the purposes of this HOWTO, I'll let it run Wine's version of D3D.

Remember: [COLOR="Red"]**Wine and Windows registries should NEVER NEVER NEVER MIX!**[/COLOR]
I cannot stress this enough. Doing so will cause your expensive Windows install to fail, dogs will lie with cats, kids will listen to old people, and general chaos will result.

Enough warning. Don't do it!

For safety sake, I rename my .wine folder to '.wine-wow', so if I need any other programs to run in wine, it won't mess with my WoW install. After that, it's all done in the command in your launcher for WoW.

Now, here's the embarrassing part: I don't remember how to make a launcher. I just edited the one I already had from my previous installs. Figure it out, and just make a launcher, with the correct icon for WoW. However you do this, it will work.

**_[SIZE="3"]Editing the Launcher Command[/SIZE]_**
In my case, my WoW/wine folder is ".wine-wow", and my Fat32 Partition is mounted at /Data32, with it being the "D:" drive in wine. Change the following for your particular setup as needed, including your username.

Right click the Launcher, and choose "Properties". Click inside the "Command" box, and type:
```
env WINEPREFIX="/home/[COLOR="Red"]<USERNAME>[/COLOR]/.wine-wow" padsp wine "D:\World of Warcraft\Launcher.exe"
```

What does all this do?
"env WINEPREFIX="/home/[COLOR="Red"]<USERNAME>[/COLOR]/.wine-wow" tells wine to use the ".wine-wow" folder, with the registries in it, as your "Windows" environment.

"padsp" tells wine use Pulse Audio for the following commands. This part is optional. Up to you. I use it so I can use my Vent client (Mangler) at the same time. 

wine "D:\World of Warcraft\Launcher.exe" tells wine to run the WoW Launcher.exe in your fat32 partition. (NOTE: Sometimes a WoW update/patch will mess this up. In that case, substitute "Wow.exe" for "Launcher.exe")

Try the "new" launcher out, and it should work fine. If not, you may need to run WoW/wine in opengl mode, which I'll cover in the next post.

---

### Post by cwwilson721 on 2012-06-06
And one more, just to make sure. It can get lengthly.

---

