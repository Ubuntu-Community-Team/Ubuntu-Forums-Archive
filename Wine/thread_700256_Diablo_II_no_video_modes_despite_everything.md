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

I've been trying to get Diablo II(plus LoD expansion) to work under wine 0.9.53 and Ubuntu 7.04 on my Toshiba satellite A10 with Intel Corporation 82852/855GM Integrated Graphics Device. I followed the extremely helpful howto found floating on these forums and have tried several xorg configurations. Suffice to say that it isn't working. The problems I've encountered seem numerous, but also seem to revolve around a central issue. It is that issue I would appreciate help with. I will try to provide as much information as possible.

In simple terms, the diablo video test comes up with no video modes found (exclamation mark) and the game itself comes up with good old error 22: a critical error has occurred with DirectDraw. Here's what it looks like in Terminal:

> 
arthur@hieronymous:~$ wine /home/arthur/.wine/drive_c/Program\ Files/Diablo\ II/Diablo\ II.exe
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
ALSA lib seq_hw.c:457: (snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
arthur@hieronymous:~$ libGL warning: 3D driver claims to not support visual 0x4b
fixme:win:EnumDisplayDevicesW ((null),0,0x34e474,0x00000000), stub!
err: x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x8 @0! (XRandR)


[quick note that two spaces exist up there that aren't there in my terminal -- I just made them to get rid of smiley faces] Okay, so going back a few steps, here's what it looks like when I run the video test:

> 
arthur@hieronymous:~$ wine /home/arthur/.wine/drive_c/Program\ Files/Diablo\ II/D2VidTst.exe
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:win:EnumDisplayDevicesW ((null),0,0x33e11c,0x00000000), stub!


And going back a few more steps to my xorg.conf file, which I have tried several times to reconfigure, both automatically and manually, now looks like this -- well at least the part I think matters:

> 
Section "Device"
Identifier "Intel Corporation 82852/855GM Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82852/855GM Integrated Graphics Device"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection


I would like you to note that I have tried the game and the test with the vesa driver (which xorg reconfigure automatically chooses) and the current i810. Following one howto on the ubuntu wiki pages I tried changing the driver to 'intel' but that destroyed my computer and I had to change it back to one of the two options above.

So basically, to cut a long winded story short, I've been trying to gather as much information as I can to help myself but according to all those tidbits I seem to be doing everything right and it still isn't working. Could anyone out there help? I know you can!

As a further note, the response to glxinfo | grep direct is rendering: Yes.
Oh, and glxgears works fine. Just fine.

Thanks in advance for any and all help!

---

### Post by happyhamster on 2008-02-18
- Just a long shot: try setting the DirectDrawRenderer to gdi in the wine registry (default = opengl). 
A quick way of doing that is pasting the following lines in an empty text file and saving it as diablo2.reg (or any name of your liking).

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="gdi"

- Then import it into the registry using:

wine regedit diablo2.reg

- If you want to change that setting later (to opengl), either make another textfile and proceed as above, or just use the bare command:

wine regedit

- and change the setting manually. Good luck.

---

### Post by lastredoubt on 2008-02-18
Thanks for the suggestion happyhamster!  I gave it a shot.  

Sadly, it adds a startlingly new development to the whole business -- if I leave the winecfg emulated window box checked then it loads up in a really small window, like before -- but if I uncheck that box and try running the game then my screen shifts into 800x600 res, which seems like the beginning of good times, though it ends up 'rebooting' me.  

The reason I put rebooting in quote marks is because I don't actually know the term for what it did to me.  It crashed, to be sure, but instead of restarting my computer, it sent me back to the ubuntu login screen.  Sorry Mario, but your princess is in another castle.

So, I'm going to go ahead and change back the registry and search for more clues as to why my game works fine but only in a little, little, useless box!

Hope you come back with some more suggestions! Thanks again.

---

### Post by harold4 on 2008-02-18
Give [this]("http://www.svenswrapper.de/english/downloads.html")  a try

Also, what's your glxinfo output?

---

### Post by lastredoubt on 2008-02-18
harold4 ! I think I read through somebody-else-with-a-similar-problem's thread and that lead me to the same site -- I haven't documented my try, so i shall try again and let you know how it goes.

As to my glxinfo output .... Badoom!

> arthur@hieronymous:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17


---

### Post by happyhamster on 2008-02-18
It killed your X-server (same thing as pressing ctrl-alt-backspace). Didn't expect that at all. 

Reason I suggested changing to gdi, is because it's the only way I can get the Diablo2 demo to work. (I have an Nvidia card though.)

---

### Post by harold4 on 2008-02-18
Looks like a deeper problem there

EDIT: What is your fps when running glxgears from the terminal?

---

### Post by lastredoubt on 2008-02-18
Okay, firstly: Harold4, the glide3 to opengl wrapper crashed my X server (now that I know what that means -- thanks happyhamster) while just attempting the Diablo video test.  I tried fiddling with the accompanying .init thing and it punched my x server in the face again!

I didn't even approach the game itself after such tomfoolery.  So I've gotten rid of the wrapper.  

Just before I mention my framerate via glxgears I want to mention that the three little colourful wheels are screwed up now! They used to go around smooth as a whistle but now they are clunky and seriously not entertaining to watch!  I don't know what step of my tinkering has caused such awfulness but I would like to get things back in order.  Ah!

Here's the whacky print out:

> 751 frames in 5.9 seconds = 127.411 FPS
794 frames in 5.4 seconds = 145.896 FPS
798 frames in 5.5 seconds = 145.605 FPS
798 frames in 5.4 seconds = 147.034 FPS
798 frames in 5.7 seconds = 139.156 FPS


---

### Post by harold4 on 2008-02-18
The FPS is really low.  My FPS with my NVidia 8600m GT is over 7,000.

Before worrying about the game, I'd shoot for getting 3D acceleration working with your Intel graphics chip.

I'm sure there are howto's all over the forum for that.  Once the 3D accel is working, then that wrapper will come in handy.

---

### Post by lastredoubt on 2008-02-18
Oh harold4 I swears to you it was working smooth and fast earlier! I don't know what's happened.  I've been fiddling with xorg.conf all day and it seems like vesa and i810 are the only drivers that do me any good.  The howto's that say to use the 'intel' driver instead don't work for me at all.  phhhhah and doggerel! I'll keep working on getting it back to normal if you keep working on helping me get that little window into a bigger window, eh? Eh?

But seriously, damn.

---

### Post by lastredoubt on 2008-02-18
Alright, Harold7000, I changed drivers and now under the good old, old, old, good, old i810 driver for my sweet sour Intel stock graphics chip, my framerate is high...er.

> 2479 frames in 5.0 seconds = 495.741 FPS
2309 frames in 5.0 seconds = 461.599 FPS
2433 frames in 5.0 seconds = 486.537 FPS
2473 frames in 5.0 seconds = 494.546 FPS


So there. It, it may not be 7000 fps, but hey, cut my piece a little slack -- those wheels looked good. And besides, I might change my name to harold5 just to show you up.

Back to the fullscreen from little window fiasco that drew you all here!

---

### Post by harold4 on 2008-02-18
See, now your framerate has quadrupled!  I was just stressing the fact that the driver needed fixed first.  I was in no way bashing your hardware.

Post a screenshot of your graphics and desktop integration tab of winecfg

---

### Post by lastredoubt on 2008-02-18
It's okay -- my hardware is more like limpware, and it knows it.  

Here's the screenshots...

...attached....

EDIT:: wow, those pictures are of the highest maximum quality possible on earth. I really wish I knew what the hell I was doing.

---

### Post by harold4 on 2008-02-18
Under the applications tab, make sure the diablo ii.exe is set to run in "windows 2000."

See if you're able to run the game without the -w switch.

---

### Post by lastredoubt on 2008-02-19
Hello my harold4, I've just got back from trying Diablo II with wine as windows 2000 to equivalent success as before -- it works, but not in fullscreen or even a larger window.  I've been playing it, of course, but the smallness of the screen and thus lack of ability to use spell-hotkeys has become annoying. 

Also, something new -- it used to be able to play the cinematics and now it can't.  Furthermore, the title screen used to look snazzy and normal, but now it has glaring color faults, such as greeny pixels all over the place.  Alas, Diablo has decidedly chosen to become the devil. Apt.  But not -get. 

Priority number one is still screen size.

---

### Post by harold4 on 2008-02-19
Take a screenshot of how diablo looks while running.  I haven't had it installed in a long time, but remember the size being too small at one point.

Also, are you using wine from the ubuntu repo, or the winehq repo?

---

### Post by lastredoubt on 2008-02-19
Ah, good question -- I believe wine was from the ubuntu repo until I tried to install Diablo II, and then after it not working, searched the net for howto's, guides, advice, etc., and came across something that told me to update wine via the wine hq repo -- so I believe this is a step that can be attributed to me being awesome and trying to work out the problem myself before asking around on these lovely forums.  So, in short, the wine HQ repo.  Yes!

And here are some more amazing,won't-believe-your-eyes pictures...

....apparently coming at ya in two posts, because of thumbnail file size. Yippee.

---

### Post by lastredoubt on 2008-02-19
That thumbnail totally convinced you that it isn't such a small window, in fact, it made you think, "Hey, this lastredoubt weirdo is totally lame not being able to cope with a window that big."

Well.... Damn, okay, so you know how I said this whole second post was because sh-mum-mm-mah-mumble, well, it's actually because I don't know what I'm doing; but now I do!

---

### Post by harold4 on 2008-02-20
The exception in the first sreenshot occurs in windows as well.  Usually a re-install of D2 will fix that.

After the re-install you should be able to get into D2 without using the -w switch.

---

### Post by lastredoubt on 2008-02-20
Hi harold4, thanks for all your careful attention to my predicament.  I've just down a clean install of Gutsy, which is an upgrade for me, and will reinstall Diablo II and see what happens. 

Thanks again for all the help! Will let you know how it turns out.

---

### Post by harold4 on 2008-02-20
Not a problem.  As much as I used to like D2, I'm always willing to help someone get it running :-P

---

### Post by lastredoubt on 2008-02-21
Okay, harold4, here's the scoop:

Gutsy solved all my problems (no offense).  After a clean install, now with the intel driver rather than i810, Diablo works like some slick poop!

In fullscreen AND in a bigger window.  I found out how to make a bigger window -- it was really easy and silly not to have figured it out long ago -- from within the game itself, in the video options menu, just change the resolution. ARGH! How nimrod-like of me. And you, poor Harold4, with a heart of platinum, there thinking I did all the obvious stuff such as the above.  This is what is to be expected of me, however, so apologies!

Fullscreen is awesome, but the gnome panels are in the way, and all  I can think of to get rid of them is to gnome-session-remove gnome-panel before I start, then gnome-panel & when I'm done : /


Anyway, thanks for all the help! Consider this case cracked.

---

### Post by harold4 on 2008-02-21
Instead of killing the panels, I used to make the virtual desktop the resolution of my screen, that way the panels exist, but are overlapped.  That way you can still see alerts and what not from the system tray.

---

