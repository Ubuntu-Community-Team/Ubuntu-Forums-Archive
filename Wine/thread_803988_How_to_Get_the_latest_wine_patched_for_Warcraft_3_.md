---
title: "How to: Get the latest wine patched for Warcraft 3 through apt"
date: 2008-05-22
forum: Wine
---

### Post by shae on 2008-05-22
With the interest people seem to have in running Warcraft 3 through wine and the need for patches to get it to run well as seen in this how to post([http://ubuntuforums.org/showthread.php?t=795714](http://ubuntuforums.org/showthread.php?t=795714)) I felt providing a PPA repository for these packages might be appreciated by some people who feel lost when building packages.  Plus by producing packages rather than just compiling from source, it makes it easier to update and remove the packages.

Information about my PPA: [https://launchpad.net/~starfall87/+archive](https://launchpad.net/~starfall87/+archive)
Supported Versions: Gutsy, Hardy

How to enable my PPA:

```
gksu gedit /etc/apt/sources.list
```

Add to that file the following lines:
Note: If you have the repository from WineHQ enabled, you should disable that repository to prevent conflicts.

For Hardy:
```
deb http://ppa.launchpad.net/starfall87/ubuntu hardy main
#deb-src http://ppa.launchpad.net/starfall87/ubuntu hardy main
```

For Gutsy:
```
deb http://ppa.launchpad.net/starfall87/ubuntu gutsy main
#deb-src http://ppa.launchpad.net/starfall87/ubuntu gutsy main
```

Then run the following from terminal to make apt aware of the new repository:
```
sudo apt-get update
```

Then remove your older version of wine and install the one from my repository:
```
sudo apt-get remove wine && sudo apt-get install wine
```

For bugs, please post here.

To remove my version of wine, remove the lines you added to /etc/apt/sources.list and run the following:

```
sudo apt-get purge wine
```

A note on the security of this repository: PPA repositories are not signed repositories.  Usually you should not trust unsigned repositories, but the structure of uploading to PPA makes such repositories more secure.  You are only allowed to upload signed source to the repository and they build it.  Thus the source code on my repository is what those packages are built from thus preventing me from secretly distributing unsafe code.

---

### Post by shae on 2008-05-23
I have updated wine for hardy to rc2 and will hopefully get to gutsy later tonight.

---

### Post by shae on 2008-05-27
I got the gutsy deb for rc2 up now too.  Enjoy.

---

### Post by shae on 2008-05-30
Wine rc3 featuring the official removal of the loss-of-focus bug is now available in my repository.

---

### Post by tatrefthekiller on 2008-05-31
The official rc3 has a bug => lose textures when switching display.
It does not appear in your version, how do you fixed it ?

---

### Post by shae on 2008-05-31
I found that too so I reapplied the loss-of-focus patch and compiled that.

---

### Post by shae on 2008-06-07
Updated for Wine RC4 for Hardy
Gutsy coming soon

---

### Post by nickblame on 2008-06-09
i gave it a shot with gutsy 64 bit for one reason.. playing warcraft 3 on battle.net.

i got wine rc3 and the same bug with battlnet freezing on initialization occured again :(

---

### Post by shae on 2008-06-09
Is that bug isolated to 64-bit because I use the 32-bit package and it works fine?

---

### Post by PandaGoat on 2008-06-18
Wine 1.0 patched for Warcraft III is now in the repository for both Hardy and Gutsy.  

Also in the repository now is a project I have started that is still under heavy development called snoopy.  It is a utility to help host games in Warcraft III (especially DotA).  Though under development it currently has one useful feature: the ability to ping.  Future releases will include the other essentials for hosting such as an autorefresher, location check, ban list, and a more polished interface like outputting to Warcraft III.  To install it, enable the aforementioned repository and install the package snoopy-wc. Here are the instruction to run it:

1. There is a menu entry under Applications->Games.  Open it.  This should open a terminal.
2. Snoopy requires root privileges to sniff a network device, but after it has started it drops the root privileges so there are no security issues. So it is safe to enter your password when prompted.
3. It needs to be running before clients join or it wont catch them, so start it sometime before you start a game.
4. To ping players, minimize to the terminal running snoopy and type ping.  For clarity, snoopy has two methods of pinging: the program ping and using Warcrafts' built in echos.  When you type ping it will use the ping program for a client if there has not been any echos yet, which take 30 seconds or so to start. Why do I use both?  Well, the ping program will timeout on people with improper configurations, but the echos will always work.  So you can type ping anytime, but if you want no time outs, you will have to wait about 30 seconds.
5.  You can also type ip and it will list the players' external ip addresses (if there are lanners, they will have the same ip).
6.  Finally, to exit, simply type exit.

If you want source code or want to help, email me at [email]pandagoat@gmail.com[/email]

---

### Post by Jexel on 2008-06-18
thanks PandaGoat, I will give this a test :)

---

### Post by Lakjin on 2008-07-16
howd it go? is it still under development?

---

### Post by 11Aether11 on 2008-07-16
Has anyone here tried using Warcraft 3 with Garena? I am having some problems (basically I can't host because ppl can't connect to me even though they see my game, and I can't join others' games because I guess a Fatal Error that is memory related) and am wondering whether this patch will help at all.

For those who don't know Garena is a client which allows you to join other ppl's games under Local Area Network in WC3 when you launch it through them. So basically it is like a makeshift Battle.net.

---

### Post by no1wantdthisname on 2008-07-18
Snoopy doesn't seem to work?  It doesn't detect the game creation and player joins.

---

### Post by Jexel on 2008-07-24
any documentation on how to use snoopy-wc?

---

### Post by Lakjin on 2008-07-25
anyone get snoopy to work?

---

### Post by SilverDragon on 2008-07-28
Snoopy didn't do anything when I tried to use it.

---

### Post by shae on 2008-07-28
Are you using wifi or wired internet?

---

### Post by PandaGoat on 2008-07-30
O_O.  I do not know which version you're using, but please answer these questions: 

Did you run it using the shell script snoopy-sh or the binary snoopy-nox?  

Did you enter your password so it could have root privileges to sniff the network device? 

Did you type "ip" or "ping"?

The only problems other people have had that I know of is if they are on 64bit.  To fix this you should just use the 32bit build.

So, do you use x64?

I just released 2.0 which has some fixes and cleanups, and I added autorefresher.  It will be added to starfall87's ppa soon, but you can get a tarball of its source here: [www.snoopy.tuxfamily.org](www.snoopy.tuxfamily.org) 

If you're on 64bit, follow this: [http://www.snoopy.tuxfamily.org/?q=node/8](http://www.snoopy.tuxfamily.org/?q=node/8)

---

### Post by shae on 2008-07-31
I have updated wine and snoopy in my repository.  I am also temporarily removing support for gutsy until I fully figure out the package copy thing.

---

### Post by Rufe0 on 2008-07-31
im having trouble with this, the game starts but the screen goes black(i can still hear the intro playing) it changes screen res probably to 640x480 and if i goto a diferent desktop all the windows are screwed up and i cant realy see the terminal properly to tell u the errors

only way to get out of it is to ctrl+alt+delete and restart

---

### Post by shae on 2008-07-31
It sounds like it cannot find a supported resolution in xorg.conf or there is a problem with xrandr.  What are the modes listed in xorg.conf?

---

### Post by Jexel on 2008-08-01
is it possible to program a delay reducer in snoopy? no host can live without a proper delay reducer.

I also have some other suggestions which you may already be working on.

* Allow the user to specify the refresh rate.

i.e.
refresh start 30

would cause the autorefresher to refresh every 30 seconds. Possibly a min refresh rate of 10 and a max of 60.

* Possibly include a snoopy.rc file so we can set default settings? Like the name of the autorefresher "bot".

* Have the screen dynamically change, rather than piling up on top of each other

* Copy the result of commands such as "ping" and "ip" onto the clipboard, so we can easily paste it into chat

* In game commands like /ping /ping /refresh

For the moment, snoopy is looking great! If a delay reducer is implemented it really will be something for me to use :D


Edit:
I tried creating an account on your site but the captcha seems to be broken, i tried typing in the words but it's always wrong, either that or i'm just stupid

---

### Post by Rufe0 on 2008-08-01
Hmm yeah maybe thats it, got ati card and ive only just got the bloody driver to work

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "glx"
	Load  "dbe"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by shae on 2008-08-01
To Jexel
What is delay reducer?

Specifying refresh rate will likely be implemented.

It is very unlikely that renaming the bot will ever be implemented.

I do not know if he plans on changing the UI to not pile on top of one-another.

Copying to clipboard is unneeded because . . .

The plan is to have it take commands from in-game and output the pings in-game.

The in-game commands will likely be -ping, etc because /command is taken by battle.net.


To Rufe0
```

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
               **Mode      "1280x800" "1024x768" "800x600" "640x480"**
	EndSubSection
EndSection

```

Make 1280x800 your preferred resolution.  On my old machine I had to do this.

Edit: I fixed the problem with reCAPCHA so you should be able to register now.

---

### Post by Jexel on 2008-08-01
> **shae said:**
> To Jexel
What is delay reducer?

Specifying refresh rate will likely be implemented.

It is very unlikely that renaming the bot will ever be implemented.

I do not know if he plans on changing the UI to not pile on top of one-another.

Copying to clipboard is unneeded because . . .

The plan is to have it take commands from in-game and output the pings in-game.

The in-game commands will likely be -ping, etc because /command is taken by battle.net.


Delay Reducer:
[http://veetee.ottechnology.com/index.php?action=tpmod;dl=cat44](http://veetee.ottechnology.com/index.php?action=tpmod;dl=cat44)

Renaming the bot is not necessary, but at least make the bot name shorter.

If you have the in game commands to be -ping or -ip, they will also be sent out to everybody else in the chat, currently the ways it's implemented in apps like WC3Banlist or VisualCustomKick, is that you just type /ping the output gets sent to clipboard and you simply paste the output into chat.

---

### Post by PandaGoat on 2008-08-01
Indeed, being able to change the timeout for the autorefresher will be implemented.  I'm not so sure about the name, but it would be nice if I did.
And there is a problem with autorefresher and having someone who is on your network in the game; snoopy will send the packets to join over a socket, but for some reason cannot close the socket (to leave), but I have no idea what the problem is.  This is not a problem if no one on your network is in your game.

For output and input, as Shae said, I will take input from in game messages--from the host--and output to in game.  I wish I could put stuff in the copy buffer until I add this, but I do not know how, and I don't want to add another dependency on a program that does this.

As for a delay reducer, this is not so easy on Linux.  This requires writing to Warcraft's memory to change the minimum delay.  In lan games the minimum delay is 100ms, and in a battle.net game it is 250ms. But doing this is difficult for one main reason: Warcraft does not actually have its own process. 

I could use a dll injection (shared library in linux's case) and the only method is to set the env variable LD_PRELOAD to the library when running warcraft.  Windows programs can force a process to load a dll while its running, which is probably how dota-client or whatever uses WC's memory.  The problem with this is there actually is no process for Warcraft(as i said above), it is actually wine-preload, so I am not sure how this works. 

Or I could become the process's parent process and read/write to the the child's memory, but once again, Warcraft does not have its own process.

I am hoping Warcraft's memory is in wine-preloads by some offset, but I really have no idea or any practical way of checking.  Hopefully, I will find someone who knows.


[edit] I think /ping and stuff will work

---

### Post by Rufe0 on 2008-08-02
Well my screen is 1680x1050 so I tired that and it's the same except now the screen just goes white, i've tried w/ virtual desktop enabled, no joy

---

### Post by PandaGoat on 2008-08-02
How are you running Warcraft through wine? (what arguments, etc.)  There may be a problem with your video card (or something) and opengl if you use -opengl.  Try running it without -opengl and see what happens.

---

### Post by Rufe0 on 2008-08-02
got a terminal error for u

```
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:win:EnumDisplayDevicesW ((null),0,0x32f1c0,0x00000000), stub!
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  163 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  545
  Current serial number in output stream:  545
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature c63a16cd in module L"war3"
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0x7e4e6767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0x7e4e681e]
#2 /usr/lib32/libX11.so.6 [0x7e52a518]
#3 /usr/lib32/libX11.so.6(XCreateGC+0x26) [0x7e5015b6]
#4 /usr/bin/../lib32/wine/winex11.drv.so(X11DRV_CreateDC+0x134) [0x7e6390e4]
#5 /usr/bin/../lib32/wine/gdi32.dll.so(CreateDCW+0x126) [0x7ecc1e06]
#6 /usr/bin/../lib32/wine/user32.dll.so [0x7edcd469]
#7 /usr/bin/../lib32/wine/user32.dll.so(GetDCEx+0x49b) [0x7edcdc4b]
#8 /usr/bin/../lib32/wine/user32.dll.so(GetDC+0x5c) [0x7edcdefc]
#9 /usr/bin/../lib32/wine/user32.dll.so(GetDialogBaseUnits+0x3d) [0x7ed86e3d]
#10 /usr/bin/../lib32/wine/user32.dll.so [0x7ed8842a]
#11 /usr/bin/../lib32/wine/user32.dll.so(DialogBoxIndirectParamAorW+0x39) [0x7ed8b199]
#12 /usr/bin/../lib32/wine/user32.dll.so(DialogBoxIndirectParamW+0x41) [0x7ed8b201]
#13 /usr/bin/../lib32/wine/user32.dll.so(MessageBoxIndirectW+0x96) [0x7edc8956]
#14 /usr/bin/../lib32/wine/user32.dll.so(MessageBoxIndirectA+0xac) [0x7edc8aec]
#15 /usr/bin/../lib32/wine/user32.dll.so(MessageBoxExA+0x5f) [0x7edc8bef]
#16 /usr/bin/../lib32/wine/user32.dll.so(MessageBoxA+0x3a) [0x7edc8c3a]
#17 [0x1501594d]
#18 [0x150162d2]
#19 /usr/bin/../lib32/wine/kernel32.dll.so(UnhandledExceptionFilter+0x5f) [0x7b844fef]

```

---

### Post by Rufe0 on 2008-08-02
ahh now i've got a visable game but its megga slow gonna do some fidling

terminal...
```
root@adam-desktop:/home/adam# wine "/home/adam/.wine/drive_c/Program Files/Warcraft III/War3.exe"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:win:EnumDisplayDevicesW ((null),0,0x32f1c0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f598,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f1ac,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @75! (desktop)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @70! (desktop)
fixme:quartz:AVISplitter_InitializeStreams stream 1: frames found: 2172570, frames meant to be found: 2173350
fixme:win:EnumDisplayDevicesW ((null),0,0x32e490,0x00000000), stub!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AVISplitter_first_request Created stream 0 thread 0x0000001e
fixme:quartz:AVISplitter_first_request Created stream 1 thread 0x0000001f
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:MediaPosition_get_CurrentPosition (0x156658)->(0x32f908) stub!
fixme:quartz:AVISplitter_thread_reader Receiving error: 80040227
fixme:quartz:AVISplitter_thread_reader Thread 0 terminated with hr 80040227!
err:quartz:ACMWrapper_ProcessSampleData Error sending sample (80040227)
fixme:quartz:AVISplitter_thread_reader Receiving error: 80040227
fixme:quartz:AVISplitter_thread_reader Thread 1 terminated with hr 80040227!
err:quartz:PullPin_Thread_Process Processing error: 8004022e
fixme:quartz:AVISplitter_done_process Waiting for 0 to terminate
fixme:quartz:AVISplitter_done_process Waiting for 1 to terminate
err:quartz:AVISplitter_Flush (0x156f48)->()
dct: 0.000000 ms (0 calls)
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:imm:ImmGetOpenStatus (0x144f08): semi-stub
fixme:imm:ImmReleaseContext (0x60026, 0x144f08): stub
wine: Unhandled page fault on read access to 0x00000200 at address 0xf7fdb09d (thread 0009), starting debugger...
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature c63a16cd in module L"war3"

```

---

### Post by Rufe0 on 2008-08-02
ok seems to work best in win2000 mode and this is my terminal
```
root@adam-desktop:/home/adam# wine "/home/adam/.wine/drive_c/Program Files/Warcraft III/War3.exe"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f784,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f390,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:imm:ImmAssociateContextEx (0x40026, (nil), 16): stub
wine: Unhandled page fault on read access to 0x00000200 at address 0xf7f3409d (thread 0009), starting debugger...

```

the frame rate is so low it is unusable

---

### Post by shae on 2008-08-02
Launch the game with the -opengl flag.

---

### Post by PandaGoat on 2008-08-02
To make things more clear answers these:

When it would not work, were you using -opengl? 
And now when it does work--but with slow framerate--you're not using it?

This indicates a problem with opengl.

---

### Post by Rufe0 on 2008-08-02
Yep that did it, nice one cheers

is there anything i can to make it fullscreen though?

---

### Post by Jexel on 2008-08-05
Going through the latest Wine Issue (350) it seems there might be an acceptex implementation :)

[http://www.winehq.org/?issue=350](http://www.winehq.org/?issue=350)

> As many of WWN's readers will be familiar with there is an open bug concerning acceptex which affects Warcraft 3. In fact, this bug has more than 250 comments and 84 votes, by far the most votes of any bug. Scott Lindeneau sends in a patch to wine-patches recently with a seemingly working implementation of the necessary functions.

Implements locatable async commands that can be notified(Terminated) using a locator (obj_handle_t)
Allows the connect command to be passed two sockets, one for listening and one to accept the connection to(instead of creating a new socket).
sock.c: Implements sock_close_handle to correctly remove any associated/locatable sockets.
fd.c: Implements register_async_l which registers a locatable async request to a file descriptor that can be notified later.
async.c: Implements async_wake_up_l to notify locatable async's and create_async_l which creates locatable async events.

---

### Post by shae on 2008-08-06
I have a testbuild up and building as I type using the AcceptEx patch he made.  If it works, expect it in the repository soon.

---

### Post by shae on 2008-08-06
I finished and tested a build with the new patch.  It works allowing hosting!  But it breaks snoopy.  I will likely wait for the issue to be fixed in snoopy before updating wine.

---

### Post by shae on 2008-08-09
Snoopy and wine should be updated together soon.  It will include the new AcceptEx patch as well as snoopy now includes location with ping as well as copying to the copy buffer.

---

### Post by PandaGoat on 2008-08-09
Also for those interested in snoopy or want to help, go to snoopy's website: [snoopy.tuxfamily.org]("snoopy.tuxfamily.org")

---

### Post by no1wantdthisname on 2008-08-09
I managed to install on 64bit, but it required installing the 32bits libraries as well.


On a side note, have you made any progress on adding delay reduction?

---

### Post by shae on 2008-08-20
A major update to snoopy has now hit the repository.  Furthermore I hope to fix the gutsy issues with wine the next time I update wine.  For information about the new features in snoopy, check out the documentation at: [http://snoopy.tuxfamily.org/sites/doc/doc.html](http://snoopy.tuxfamily.org/sites/doc/doc.html)

---

### Post by k1ngb0b0 on 2008-09-20
> **shae said:**
> A major update to snoopy has now hit the repository.  Furthermore I hope to fix the gutsy issues with wine the next time I update wine.  For information about the new features in snoopy, check out the documentation at: [http://snoopy.tuxfamily.org/sites/doc/doc.html](http://snoopy.tuxfamily.org/sites/doc/doc.html)


I tried all the steps you listed but for some reason I am unable to host still.

Do I need to install snoopy to host?

I'm using 64-bit ubuntu, could that be the problem?

---

### Post by shae on 2008-09-20
I have not personally tested 64bit so that might be a problem, but no you do not need to use snoopy to host.  Have you checked to make sure you have the proper ports forwarded if you are behind a router?  You should make sure to have 6112 open and not firewalled.

---

### Post by k1ngb0b0 on 2008-09-20
> **shae said:**
> I have not personally tested 64bit so that might be a problem, but no you do not need to use snoopy to host.  Have you checked to make sure you have the proper ports forwarded if you are behind a router?  You should make sure to have 6112 open and not firewalled.

I'm using a router but I'm not quite sure how to enable forwarding under linux :-X, can you help me with that?

I'm using a Linksys NR041.  It's just a 4 port cable/DLS router.

I'm terrible with routers and the like, so I'm not sure how to forward the ports here..


Edit: Ok here's what I did, I think the I enabled forwarding.

I went the the advanced router setup after typing my Gateway into firefox.  Then I clicked on port forwarding and view port range forwarding.  Then I put in the range 6112-6119 and checked both protocols.

I did all this and for some reason it still did not work.  Did I forward my ports incorrectly?  Or it might also be 64-bit ubuntu...

---

### Post by shae on 2008-09-20
That is the right idea.  Make sure you forwarded the ports to the ip of your computer and not another one on the network.

---

### Post by k1ngb0b0 on 2008-09-22
> **shae said:**
> That is the right idea.  Make sure you forwarded the ports to the ip of your computer and not another one on the network.

I'm pretty sure I did this right and for some reason I still cannot host games :-/.

Not sure what to try next.

---

### Post by shae on 2008-09-23
You could try Shields Up to see if the port is indeed open.  [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by k1ngb0b0 on 2008-09-29
> **shae said:**
> You could try Shields Up to see if the port is indeed open.  [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)


I just tried this and it said the ports are still closed!

I'm not sure why this is and I don't know how I would go about opening them :-/

Edit: I don't have a static IP set up (and I don't know how to do it) could that be the problem?

---

### Post by shae on 2008-09-29
Perhaps the port is closed by your ISP.  Have you been able to host on a different OS before?  Until shields up reports that port to be open, you will not be able to host.

---

### Post by k1ngb0b0 on 2008-10-01
> **shae said:**
> Perhaps the port is closed by your ISP.  Have you been able to host on a different OS before?  Until shields up reports that port to be open, you will not be able to host.

Yeah I used to be able to host fine on XP.  I'm still searching for a solution...

---

### Post by shae on 2008-10-01
Do you have any firewall active in ubuntu?

---

### Post by k1ngb0b0 on 2008-10-02
> **shae said:**
> Do you have any firewall active in ubuntu?

No I don't.

Edit: I was going to try portforward.com but their instructions are for Windows only so I was kinda stuck.

---

### Post by shae on 2008-10-02
Port forwarding is independent of the operating system.

---

### Post by k1ngb0b0 on 2008-10-03
> **shae said:**
> Port forwarding is independent of the operating system.


I realize that, but the instructions were for XP.  I don't know how to do the linux equivalent actions.

---

### Post by shae on 2008-10-03
Search port forwarding and the version of your router.

---

### Post by Markuz Nightwind on 2008-10-13
Hello shae, could you please build an updated 1.1.6 patched wine? I would like to use the latest fixes with the good patches for warcraft but actually i'm unable to build wine on my amd64 system.

P.S. Thank you very much for this work anyway:)

---

### Post by dsilva on 2008-10-26
k1ngb0b0, wine 0.9.45 is the last version where warcraft3 hosting worked.

See these two threads:

[http://ubuntuforums.org/showthread.php?t=781274](http://ubuntuforums.org/showthread.php?t=781274)
and
[http://ubuntuforums.org/showthread.php?t=795714](http://ubuntuforums.org/showthread.php?t=795714)

follow the bug report and resolution progress at:
[http://bugs.winehq.org/show_bug.cgi?id=13252](http://bugs.winehq.org/show_bug.cgi?id=13252)

---

### Post by shae on 2008-10-26
My version is patched to support hosting.

---

### Post by quank1half on 2008-10-27
Has this version been updated for the recent 1.0.1 release?  Also, is there a version for Intrepid?

---

### Post by shae on 2008-10-27
The current version is 1.1.4 in my repository.  I should be able to update them all after II comes out. (I was trying a different distro out, but will be installing II this weekend.)

---

### Post by Aspras on 2008-11-03
Could you also summarize how can we install the new version on 8.10?

---

### Post by shae on 2008-11-03
I have not updated my repo for intrepid because I just managed to install it yesterday.  Look for a update after the elections.

---

### Post by Aspras on 2008-11-04
So i guess you will let us know about the update through this thread right?

---

### Post by shae on 2008-11-05
Absolutely

---

### Post by Aspras on 2008-11-05
Great, one more question. I hope I will be able to host games and play in games cause even though the right ports of my router were correctly forwarded people couldnt join my games and I couldnt get in-game after the 5 seconds countdown.

---

### Post by PandaGoat on 2008-11-15
Shae just recently updated snoopy to the latest version, 2.9.98, which is significantly better than the previous one.  If you play Warcraft III check out my signature and Shae's repository.

Moreover, I have heard mixed attitudes towards newer versions of wine.  Is the latest one alright now?  What exactly is the most recent decent version?  I have been using 1.1.5 and have stopped updating since I started hearing about problems with wine.  Shae needs to know since he is going to update his repository soon.

---

### Post by Konj on 2008-11-16
Cheers PandaGoat and Shae.

EDIT: I get this message when starting up 2.9.98

> I could not find tcpkill on $PATH.  To see what $PATH is do `echo $PATH`.  Make sure, if you know you have the package dsniff, that tcpkill is in in $PATH; otherwise, install dsniff.
I could not find a suitable program on $PATH to access the clipboard. To see what $PATH is do `echo $PATH`.  You should install the package xclip if you are on linux or pbcopy if you use mac.I could not find wget on your $PATH.  If you're on linux, you probably messed up something.  If you're on mac, you need to install it.


$PATH doesn't even exist.

EDIT2: Regarding Wine, 1.1.8 for me has audio issues. The sound skips, and is very choppy.

---

### Post by PandaGoat on 2008-11-16
Oh crap, I did not realize that the way I checked for those would mess up in this case.  Anyway, it's because the computer that launchpad built it on did not have those installed at the time.  

I fixed it so it will check when being ran instead of checking at compilation.  Shae may update it tonight or tomorrow. Sorry about that.

---

### Post by Konj on 2008-11-20
I don't mean to be naggy or anything, but do you have an ETA on when the repository will be updated?

I downgraded from Wine 1.1.8 to 1.0.1 and the sound works perfectly now.

---

### Post by shae on 2008-11-20
When I have a rough idea which version I should package.  After that it is a matter of a few minutes.

---

### Post by poisonkiller on 2008-11-25
> **shae said:**
> When I have a rough idea which version I should package.  After that it is a matter of a few minutes.
Well, I hope you package Wine 1.1.8 or 1.1.9, since Garena doesn't want to work with older versions (including 1.1.0 and 1.1.4). I tried patching Wine on my own, but I think I messed something up, so I'd really appreciate it, if you upgraded your pre-patched version.

PS: The fix for choppy sound is easy - just kill pulseaudio.

---

### Post by Konj on 2008-11-26
Wouldn't that kill my Amarok sound output?

---

### Post by shae on 2008-11-30
Tomorrow I will hopefully upload 1.1.9 to Intrepid.  If it works, I will backport it to the older versions of Ubuntu.

---

### Post by shae on 2008-12-01
1.1.9 is build and ready to go!  Let me know if you have problems.

---

### Post by jake_swe on 2008-12-02
The 1.1.9 build works however my sound is choppy. And navigating the wc3 maps by draging the mouse to the sides of the screen dose not work properly.

---

### Post by PandaGoat on 2008-12-02
If you have compiz running, the game is not actually running in the full screen that you're thinking of.  Moving the mouse to the edge of the screen actually puts it outside of the game window.

---

### Post by jake_swe on 2008-12-02
Well compiz was actually running. Disabling it worked for the mouse problem. Isnt there an other solution, i kinda like compiz :)

The sound works if i kill pulseaudio but that is nothing i want to do bacause then i can't talk in skype while i'm playing wc3.

---

### Post by PandaGoat on 2008-12-02
Try running warcraft with padsp: "padsp `WINEDEBUG=-all wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -opengl`"

Do "man padsp" if you want to know what it does.

---

### Post by poisonkiller on 2008-12-03
> **shae said:**
> 1.1.9 is build and ready to go!  Let me know if you have problems.
First of all, thank you.
Second, I still can't see any games through Garena. :(

---

### Post by jake_swe on 2008-12-03
I'm afraid padsp did not help me. Sound is still terrible.
This is just one of my many fails in linux. It seams like everything that you can do in windows is kind of possible in linux. (But alot harder.)

---

### Post by shae on 2008-12-03
In System>Preferences>Sound, try selecting alsa for all the options there.

Second, with compiz on, try turning off redirect all windows or something like that.

---

### Post by EvilTchnlgy on 2008-12-04
I know it may be helpful for those who don't know how but it is a bit obnoxious that it breaks properly denoted paths: when I specify Program\ Files it changes it to Program\\ Files...
```
Downloading version 6.57b . . . cd: 1: can't cd to /home/brendan/.cedega/TEST/c_drive/Program\ Files/Warcraft\ III/Maps/Download
[OK]
chown: cannot access `/home/brendan/.cedega/TEST/c_drive/Program\\ Files/Warcraft\\ III/Maps/Download/DotA Allstars v6.57b.w3x': No such file or directory
chmod: cannot access `/home/brendan/.cedega/TEST/c_drive/Program\\ Files/Warcraft\\ III/Maps/Download/DotA Allstars v6.57b.w3x': No such file or directory
Version: 2.9.98

``` 
It's further confusing in that I read > can't cd to /home/brendan/.cedega/TEST/c_drive/Program\ Files/Warcraft\ III/Maps/Download when it isn't actually trying to access that directory

The obvious fix for me was to just change my path to just blanks,just thought I should point it out...

The second thing is that if I stop the autorefresher and then restart it without setting a timeout argument the refresher goes crazy.. although it doesnt instantly tell me I'm disconnected from battle.net, I immediately cannot use the chat box even for snoopy commands. I end up getting an error along the lines of "you are not connected to the chat". Upon leaving the room bnet instantly notifies me of my loss of connection.
Although my understanding was that snoopy connects directly to the socket locally I presume something must be sending too many commands to bnet too quickly as it will not let me reconnect to whichever realm i disconnect from for 5 minutes or so. The connection isn't refused but rather it says I can't connect so I assume it's a security feature of bnet.. I verified that I can connect to other realms during the period of inaccessibility.
Seeing as how I stipulated a timeout default it would be rather helpful if it not only used this at start but int he case that the autorefresher is started without an one defined.

Don't mean to sound too critical, Keep up the great work!

---

### Post by PandaGoat on 2008-12-04
I made it so you do not have to add anything like \ for spaces by adding quotation marks around the path when I use it.

So you do "/refresh start" with no timeout?  I'm not even sure what that would do, but it apparently spams join requests.  It probably reads the timeout as NULL, and in the thread that sends the requests it will sleep for NULL seconds between each refresh which will cause it not to sleep at all since NULL is just 0.  This is not the only thing involved: you as a host try sending packets back accepting the request and packets are sent to battle.net.  Like spamming a channel, it will disconnect you.  

You should always specify a timeout anyway; I didn't implement it working without it specified.

---

### Post by Jexel on 2008-12-08
i had a sound issue too with this release. But I just changed the sound driver to use OSS and then it was working fine.

---

### Post by EvilTchnlgy on 2008-12-08
PandaGoat, I appreciate your technical explanation. I have been using snoopy since I last posted and I must say, I am thoroughly impressed.

---

### Post by Konj on 2008-12-10
So has anyone found a fix for the choppy sound without killing my Amarok sound output? Thanks in advance.

---

### Post by shae on 2008-12-11
Have you tried setting your computer and wine to use alsa?

---

### Post by Konj on 2008-12-11
Yes, sound preferences, Wine preferences and Amarok engine are all set to ALSA. The sound is still choppy.

---

### Post by PandaGoat on 2008-12-12
I just updated to 1.1.10 and experienced the same sound problems.  After messing with it a bit, I found a fix.  Run winecfg, choose Alsa in the Audio tab, and check Driver Emulation in the DirectSound group box in the Audio tab.

*EDIT* Crap, disregard this.  It does not cause other applications to crash but it still has the problem of not letting them use sound.

---

### Post by Ng Oon-Ee on 2008-12-12
> **PandaGoat said:**
> I just updated to 1.1.10 and experienced the same sound problems.  After messing with it a bit, I found a fix.  Run winecfg, choose Alsa in the Audio tab, and check Driver Emulation in the DirectSound group box in the Audio tab.

*EDIT* Crap, disregard this.  It does not cause other applications to crash but it still has the problem of not letting them use sound.
Use the fix I just posted up [here]("http://ubuntuforums.org/showthread.php?t=1009629").

---

### Post by Rufe0 on 2008-12-13
Upgraded to Intrepid

Now when I connect to battle.net nothing happens, I cannot get out of it or press cancel because of complete system crash. I'm not sure if I'm actually getting your package properly. It definitely says PPA when I'm getting it, however the package I get just seems to be a normal version of wine with no mods. Any ideas?

Thanks Rufe0

---

### Post by shae on 2008-12-14
If the package version has PPA in it, it is the right one.  I am wondering what the output from terminal is when you experience that crash.  Do you think there is some way you can get that?

---

### Post by Jexel on 2009-01-12
is it possible for you to update wine with the latest acceptx patch?

[http://bugs.winehq.org/attachment.cgi?id=18638&action=edit](http://bugs.winehq.org/attachment.cgi?id=18638&action=edit)

---

### Post by shaolinmilk on 2009-01-16
How do I get the latest version? I installed the hardy version(don't know the difference) and everything is running fine. I wanna download the newest version, but it keeps on showing dependency issues. I'm new to Ubuntu so I'm not too sure.

And I don't think I can host. I've forwarded my ports and everything and still can't host.

---

### Post by pxc on 2009-01-25
Since Shae hasn't updated his PPA for a while (which I myself was using), I created my own with the latest version (1.1.13) of Wine (along with the war3 patches, of course).

[https://launchpad.net/~pxc/+archive](https://launchpad.net/~pxc/+archive)

Note that the i386 package is not yet done building. Users of regular 32-bit Ubuntu will probably have to wait a little over an hour to be able to download the deb. The amd64 version, however, is finished, and works great on my machine. :-)

---

### Post by shae on 2009-01-25
Sorry for going mia on ya like that.  All of the new versions cause audio issues (at least they did for me).

---

### Post by pxc on 2009-01-26
Hmm... I don't have that problem, but I'm on Kubuntu, which AFAIK doesn't use Pulseaudio. Perhaps the stuttering is related to pulse?

Or maybe it's just been fixed recently..? Can we get a few other Ubuntu War3 players to try the new packages to confirm/figure this out?

---

### Post by ugkbunb on 2009-01-30
> **pxc said:**
> Hmm... I don't have that problem, but I'm on Kubuntu, which AFAIK doesn't use Pulseaudio. Perhaps the stuttering is related to pulse?

Or maybe it's just been fixed recently..? Can we get a few other Ubuntu War3 players to try the new packages to confirm/figure this out?

Ill test it out... thanks for the repo... ill post up tomorrow my results when i get war3 re-installed. just reinstalled 8.10 xubuntu and am using pulseaudio.

---

### Post by pxc on 2009-01-31
I'm currently uploading a new package for Wine 1.1.14, which has not yet made its way into the official Wine Ubuntu repositories either. I also tried with this version a new patch for the OpenGL texture loss bug, which appears to do a more thorough job of preventing its occurrence (I've not yet been able to reproduce it since applying this new patch).

Let me know if it works the same way for you all.

---

### Post by sniperbob on 2009-02-07
(edit)

Nevermind.. I D ten T error. How do I delete posts? :redface:

---

### Post by shaolinmilk on 2009-02-18
> **pxc said:**
> I'm currently uploading a new package for Wine 1.1.14, which has not yet made its way into the official Wine Ubuntu repositories either. I also tried with this version a new patch for the OpenGL texture loss bug, which appears to do a more thorough job of preventing its occurrence (I've not yet been able to reproduce it since applying this new patch).

Let me know if it works the same way for you all.
I downloaded your latest version of wine and it has done wonders! I no longer have ugly/glitchy scrolling!!! Do you have any idea what fixed this?

---

### Post by AnonymousFan9 on 2009-03-03
Thanks so much, this works perfectly!

---

### Post by Markuz Nightwind on 2009-03-20
Hello pxc, could you please add save patch to your wine? Yesterday evening i played war3 a bunch of hours in skirmish mode and when i decided to save it crashed the game without actually saving (using latest wine 1.1.17, while it was working pretty fine with the latest shae version).

Bugzilla link is:
[http://bugs.winehq.org/show_bug.cgi?id=11188](http://bugs.winehq.org/show_bug.cgi?id=11188)

Thanks for the work anyway :)

---

### Post by ostaja on 2009-05-09
Newest WINE is not always best for WC3. I have tested several WINE versions with patches, but 1.1.3 for best with those patches. Example newer WINE versions crash warcraft 3 sometimes when swapping desktops, but with 1.1.3 it wont. Also WINE version 1.0 works, but it does not have that wonderful tray support.

Patches which i have used are: desktop_switching.patch, freetype.patch and updated hosting.patch.

BTW, does anyone know why Warcraft 3 lose textures (white screen, only example buttons and few other textures are visible etc..) when open another wine application. This happens only when run warcraft 3 on opengl mode. Thats why i have used Directx mode on warcraft, but that have own darksides too.

Thx.

---

### Post by shae on 2009-05-09
If you are using jaunty, you might give my latest attempt a try.  It is 0.9.45 which is suppose to work well for warcraft and not suffer from the problems the latest versions have from the warcraft patch 1.23.

(1.0.1-1-isreally-0.9.45-0ubuntu1~ppa6)

(If anyone could, would someone help me figure out the problem with it and lpia?)

---

### Post by misse- on 2009-05-20
Hi, I tried installing your jaunty build via Gdebi. Just got segmentation fault when trying to run warcraft III.

---

### Post by shae on 2009-05-20
Hmm, I am not shocked it was somewhat hacky.  I will upload a newer patched up version soon then.

---

### Post by killabee44 on 2009-05-25
Guys,

My 14 year old nephew has a laptop that he runs his favorite online game, Warcraft3,  on. 

After a string of really bad windows viruses, I installed Jaunty on a separate partition. 

I would like to get Warcraft3 going on Jaunty, but can the PPA repositories be used on Jaunty? Would it be ok? Which is the most stable version of the patched Wine versions right now? 

I see the post by Shae on version 0.9.45, and also see the post by ostaja about versino 1.1.3..

Also, if I end up having to run warcraft in opengl mode (-opengl), is there a way to automate that for my nephew? 

Thanks.

Killabee44

---

### Post by ipx on 2009-05-25
> **killabee44 said:**
> Guys,

My 14 year old nephew has a laptop that he runs his favorite online game, Warcraft3,  on. 

After a string of really bad windows viruses, I installed Jaunty on a separate partition. 

I would like to get Warcraft3 going on Jaunty, but can the PPA repositories be used on Jaunty? Would it be ok? Which is the most stable version of the patched Wine versions right now? 

I see the post by Shae on version 0.9.45, and also see the post by ostaja about versino 1.1.3..

Also, if I end up having to run warcraft in opengl mode (-opengl), is there a way to automate that for my nephew? 

Thanks.

Killabee44

Hello!

Yes, the PPA-repository should work just fine. There is even a wine 1.1.21 with the patches compiled for jaunty. I suggest getting that one, I am using it to play DotA daily.

You can force wc3 to launch in opengl-mode automatically, and I highly recommend it since it gives the game better performance with no downsides.

You should read about it on winehq's appdb, they give you a guide for all you need.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126")

---

### Post by misse- on 2009-05-25
Hi guys,

I reverted back to Intrepid and installed 1.1.9~winehq0~ubuntu~8.10-0ubuntu1~ppa1 and YAY, I can host AND go to my other desktops / alt tab.

Just one minor glitch: the sound got all choppy. I tried using padsp on my Frozen Throne Startup command, but no difference. 

On my other intrepid machine I've got your 1.1.4 version for hardy installed and that one has no such errors.

Ipx mentions a fully (?) functional version for jaunty available in some ppa.. is he referring to Shae's?

Anyway, thanks a beep'n lot for your patches and work. I'm using Ubuntu as my only operating system, and along with mumble I have a solid base to convince my fellow Dota players to go Open Source. It just sucks that wine breaks it sometimes, especially since it has been knowned to work properly before.

Now I understand that Wine has a bigger goal, and can't focus on WC3 working flawlessly through all releases. That's why I'm so glad that there are people like you Shae. :)

---

### Post by shae on 2009-05-26
Yes my ppa has a jaunty build available which should work fine, but suffers from the alt+tab problem with lost textures.  I hope to sort that out with the build of 1.1.22.

I have a updated guide here for Jaunty: [HOWTO Get Wine Patched for Warcraft 3 in Ubuntu 9.04](http://distrohop.com/thread-howto-get-wine-patched-for-warcraft-3-in-ubuntu-9-04)

---

### Post by ipx on 2009-05-26
Hello!

I forgot to mention something;
I am using a script to be able to simply alt+tab out of the game. For this I start wine in a separate, fullscreen window.

Here's the code I use:
```
#!/bin/sh
xgamma -gamma 1.6
env WINEDEBUG=-all wine explorer /desktop=0,1680x1050 "C:\Program Files\Warcraft III\Frozen Throne.exe" 
```

Change the resolution to the one you are using on your desktop, your path to wc3 and optionally remove the gamma-option.
You could just create a shell-script and execute it every time you launch wc3.

Hope this helps you guys out, it sure did to me!

---

### Post by shae on 2009-05-31
That is an excellent idea!

I am sorry, but the current version in the repository is experimenting with using wine hacks as the base for the patched version of wine.  Thus, I need to wait for them to update to the next version of wine for me to get the next version out.  Sorry for the delay.

---

### Post by truthseer0 on 2009-12-15
running 9.10 karmic koala. i'd love to get snoopy, but i need ld.so.preload-manager and no idea if i can fake it somehow.
here's what apt-get it throwing at me:
The following packages have unmet dependencies:
  snoopy: Depends: ld.so.preload-manager (>= 0.1) but it is not installable
E: Broken packages

---

### Post by misse- on 2009-12-27
Hello again :)

The ppa doesn't seem to contain packages for karmic, is there a patched version on its way? I'm running the 64bit version on an Asrock Nettop and am really looking forward to test it with Wc3 :)

Thanks for your great work!

---

