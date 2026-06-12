---
title: "No fullscreen in skyrim"
date: 2012-06-07
forum: Wine
---

### Post by switch10 on 2012-06-07
I have skyrim installed via play on linux.  Everything seems to be working fine other than I cannot seem to get skyrim to play in fullscreen mode.  I have edited the following entries in skyrimprefs.ini:
```
bFull Screen=1
iSize H=1080
iSize W=1920
``` 

I also changed some settings in wine configuration.  I have wine emulating a virtual desktop size of 1920x1080, the resolution of my screen.  Still no luck.

Any ideas??

Thanks in advance.

---

### Post by Shadowstripe on 2012-06-07
run the game from the launcher hit options and make sure it is also set to full screen there.

disable the virtual desktop I think it makes things go run in a window (but don't quote me on that)

---

### Post by switch10 on 2012-06-08
I get an error when I start the game from the launcher.  I have to go to the game directory and start the game from the "*.exe". the strange thing is that box is never displayed.  It goes right to the game...

---

### Post by Shadowstripe on 2012-06-08
I also had the error from the launcher when trying to run it directly what I had todo was run the launcher from its installed directory.

something like 

cd ~/.wine/drive_c/skyrim/

then

wine skyrimlauncher.exe

or just make a shortcut on your desktop to wine/launcher and specify the starting directory as the location where you installed skyrim (full linux path) the run command you want it to use will be something like wine "c:\skyrim\skyrimlauncher.exe"

bit complicated but it worked for me also I think you have to go through the launcher to make the game detect mods

---

### Post by evil_urna on 2012-08-13
Hate to perform thread necromancy but I am also having this same problem. Game runs like a top in windowed mode but will not even start fullscreen even with the settings changed in SkyrimPrefs.ini

---

### Post by evil_urna on 2012-08-13
I think I may have found something. I checked out the backup I had of my windows install of Skyrim before I slapped Ubuntu back on and there was a file in the same folder as the SkyrimPrefs.ini named "rendererinfo.txt"

It is blank in my ubuntu install but in my windows install it said this:

```

Renderer Device Information:
	NVIDIA GeForce GTS 450   
	nvd3dum.dll
	RenderPath         		: BSSM_SV_3_0
	PSversion          		: 300
	VSversion          		: 300
	VStarget           		: vs_3_0
	PStarget           		: ps_3_0
	PS2xtarget         		: ps_3_0
	maxPS20inst        		: 512
	3.0 Support        		: yes
	3.0 Lighting       		: yes
	Nonpowerof2textures		: yes
	FP16ARGB blending  		: yes
	FP16ARGB filtering 		: no
	Bloom lighting     		: no
	Refraction         		: yes
	2.0 hairw           		: yes
	SLI mode           		: no
	NVapi enabled      		: yes
	Multisample Type   		: 4
	Transparency MS    		: no
	HW Thread Count    		: 4

```

If i try to copy the contents over it just gets re written as blank when I try to launch Skyrim in windowed or fullscreen modes. I tried setting the file as read only and it just farted around and gave me the same crash.

No more ideas here.

EDIT:

```


**err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly (using GL renderer "GeForce GTS 450/PCIe/SSE2", version "2.1.2 NVIDIA 295.40").**
fixme:win:EnumDisplayDevicesW ((null),0,0x32f7bc,0x00000000), stub!
scott@Scott-Desktop:~$ p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:process:GetLogicalProcessorInformation ((nil),0x33ed88): stub
fixme:process:GetLogicalProcessorInformation (0x33edb0,0x33ed88): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x33ed90): stub
fixme:process:GetLogicalProcessorInformation (0x33edb8,0x33ed90): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly (using GL renderer "GeForce GTS 450/PCIe/SSE2", version "2.1.2 NVIDIA 295.40").
fixme:win:EnumDisplayDevicesW ((null),0,0x33f190,0x00000000), stub!
err:mmtime:TIME_MMTimeStop Timer still active?!

```

I think that that bolded part might be something.

---

