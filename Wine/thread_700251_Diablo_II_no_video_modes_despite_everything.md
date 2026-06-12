---
title: "Diablo II no video modes despite everything"
date: 2008-02-18
forum: Wine
---

### Post by lastredoubt on 2008-02-18
EDIT:: The below still may be the source of the problem, yet I recently stumbled across a minor success. I can get the game to run but in a really small window.  Is there any way I can increase the window size or play it fullscreen?  I managed to get this far by either running the game via terminal with a '-w' at its end or by clicking the windowed option in winecfg.  The screen is a little too small to play on still, so please help! Not sure if this helps but here is my xrandr output:

> 
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 347mm x 260mm )  *60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none


Well hopefully not everything.  

I've been trying to get Diablo II(plus LoD expansion) to work under wine 0.9.53 and Ubuntu 7.04 on my Toshiba satellite A10 with Intel Corporation 82852/855GM Integrated Graphics Device. I followed the extremely helpful howto found floating on these forums and have tried several xorg configurations.  Suffice to say that it isn't working. The problems I've encountered seem numerous, but also seem to revolve around a central issue. It is that issue I would appreciate help with.  I will try to provide as much information as possible. 

In simple terms, the diablo video test comes up with no video modes found (exclamation mark) and the game itself comes up with good old error 22: a critical error has occurred with DirectDraw.  Here's what it looks like in Terminal:

> arthur@hieronymous:~$ wine /home/arthur/.wine/drive_c/Program\ Files/Diablo\ II/Diablo\ II.exe
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
ALSA lib seq_hw.c:457: (snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
arthur@hieronymous:~$ libGL warning: 3D driver claims to not support visual 0x4b
fixme:win:EnumDisplayDevicesW ((null),0,0x34e474,0x00000000), stub!
err: x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x8 @0! (XRandR)


[quick note that two spaces exist up there that aren't there in my terminal -- I just made them to get rid of smiley faces]  Okay, so going back a few steps, here's what it looks like when I run the video test:

> arthur@hieronymous:~$ wine /home/arthur/.wine/drive_c/Program\ Files/Diablo\ II/D2VidTst.exe
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:win:EnumDisplayDevicesW ((null),0,0x33e11c,0x00000000), stub!

And going back a few more steps to my xorg.conf file, which I have tried several times to reconfigure, both automatically and manually, now looks like this --  well at least the part I think matters:

> Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

I would like you to note that I have tried the game and the test with the vesa driver (which xorg reconfigure automatically chooses) and the current i810.  Following one howto on the ubuntu wiki pages I tried changing the driver to 'intel' but that destroyed my computer and I had to change it back to one of the two options above. 

So basically, to cut a long winded story short, I've been trying to gather as much information as I can to help myself but according to all those tidbits I seem to be doing everything right and it still isn't working.  Could anyone out there help?  I know you can! 

As a further note, the response to  glxinfo | grep direct is rendering: Yes. 
Oh, and glxgears works fine. Just fine.

Thanks in advance for any and all help!

---

### Post by disturbedite on 2008-02-18
d2 is so old that it only runs at 640x480 or 800x600 resolution.  you can't "force" it to run at a different resolution.
also, d2 was 16bit color iirc, so it can't before forced to run at 24/32bit color either.

---

### Post by lastredoubt on 2008-02-18
I hadn't realized -- but, I'm sorry to say, I think that's besides the point.  At the moment Diablo II is working at a decent resolution yet in a very small window.  Unless the reason for my small window of Diablo is because it is somehow compensating for 'being forced' into a higher resolution, then I really don't see how that affects what's going on. And if it is compensating, then please, for the love of Linux, help me out and tell me something practical I can do increase the size of the game window.

---

### Post by disturbedite on 2008-02-19
i already told you, you can't.  its either running in full screen or windowed mode, the resolution isn't different, its simply the difference between full screen & windowed mode.
d2 has a fixed resolution of 640x480 or 800x600.

---

### Post by lastredoubt on 2008-02-19
Two points then:

How do I switch it between 640x480 and 800x600? Is it possible? At the moment I think the window is 640x480 and anything bigger would be great. 

How can I make it work running in fullscreen rather than only working as a small window? I didn't realize fullscreen meant high resolution -- I assumed a game could be played in fullscreen at a lower resolution -- this is what I would like to accomplish.  Is it possible? 

I don't mean to make it sound like I know what I'm doing, because I don't, but shouldn't it be possible to have Diablo work at, say, 800x600 and in fullscreen? Or, alternatively, have it work in a 800x600 window rather than a 640x480 window?

I appreciate your input so far, but clearly I'm still muddled on what you mean.

---

### Post by disturbedite on 2008-02-20
> **lastredoubt said:**
> Two points then:

How do I switch it between 640x480 and 800x600? Is it possible? At the moment I think the window is 640x480 and anything bigger would be great.
from within the game options.

> **lastredoubt said:**
> How can I make it work running in fullscreen rather than only working as a small window? I didn't realize fullscreen meant high resolution -- I assumed a game could be played in fullscreen at a lower resolution -- this is what I would like to accomplish.  Is it possible?
again, from within the game options.  and full screen *doesn't* mean high resolution, i didn't say it did.  you can D2 at 640x480 or 800x600 in full screen OR windowed mode.
i thought you said you wanted to run it at a higher resolution than 640x480?  now i'm confused.

i'll try to clear this up for you.
the fact that D2 can only run at 640x480 or 800x600 resolution (because its so old) is because its hardcoded into the game.  (similar to starcraft).  on windows, its the same, you cannot run in it at any other resolutions than the ones previously mentioned.
wine "respects"/emulates this behavior, wine does not allow you to force the game to run at a different resolution than it natively supports.

---

### Post by lastredoubt on 2008-02-21
I understand now! Thanks for your patience -- I really appreciate it; the confusion has mostly been mine, and I think I'm on the right track now. Brilliant.

Cheers!

---

### Post by disturbedite on 2008-02-21
glad to help.  maybe it will save you some time.  trying to figure out how to do something that isn't possible, i mean.  ;)

---

