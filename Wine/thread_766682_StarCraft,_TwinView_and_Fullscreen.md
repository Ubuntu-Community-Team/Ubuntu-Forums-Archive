---
title: "StarCraft, TwinView and Fullscreen"
date: 2008-04-25
forum: Wine
---

### Post by mriedel on 2008-04-25
I use nvidia-new drivers and two displays at a native resolution of 1680x1050 each, configured through nvidia-settings.

I added an additional metamode for 640x480 in nvidia-settings. It was properly saved and appears in /etc/X11/xorg.conf.

Now when I start StarCraft through wine, it says it couldn't switch video modes. I then switched to 256 colors manually. "Couldn't switch video modes". I also tried switching to 640x480 and 256 colors manually. "Couldn't switch video modes".

My question pretty much comes down to "Why?".

I do NOT want to enable the virtual desktop setting in wine, as StarCraft ends up in a 640x480 window that is too small to play in and furthermore can't keep my mouse from moving out of it (thus making scrolling impossible) although the respective setting (DirectX mouse capture) is enabled.

wine version is 0.9.59. OS is hardy. I let wine emulate Win98. Changing this has no effect.

The wine error message is:
> err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x8 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1680x1050x8 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1680x1050x32 @0! (XRandR)

**Update:**
After checking the ouput of xrandr, I could solve my original problem by turning my second display off in the metamode that sets 640x480 for the primary monitor.

StarCraft now properly starts in fullscreen, but two new problems arise:
A) Even the menus run slow as hell (that wasn't the case when I ran it in windowed / virtual desktop mode)
B) Video mode isn't switched back to 3360x1050 upon exiting StarCraft

**Update2:**

Fixed problem A by doing nothing / doing somethin else. A new problem arose though:

C) Shift-Click and Ctrl-Click (unit grouping and unit type selection) don't work

---

### Post by mriedel on 2008-04-26
**Update3:**

Solved problem C by upgrading to wine-0.9.60. See [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb).

Improved the situation with problem B by **both** (doing only one or the other won't work, at least it didn't for me) upgrading to wine-0.9.60 (see above) and adding another nvidia metamode (first display 1680x1050, second display off). Now when i exit StarCraft, the resolution of my primary screen goes back to 1680x1050. It is still not possible to have it switch directly to 3360x1050. Additionally, when I try to go back to the 3360x1050 metamode by running xrandr --output default --mode 3360x1050, my second display ends up having a black (but corruptedly paintable by application windows) bar at the top which equals my primary display's top gnome panel in size and position.

---

### Post by FrozenFox on 2008-04-26
I'm not sure if it'll help or work (it works for lots of things in wine, but some just dont want to do it, like wc3), but have you tried running sc via xinit /usr/bin/wine pathtostarcraft -- :1     (or perhaps not 1, if its not free. try 2 or something if it wont let you. you can switch back via ctrl+alt+f7 from f8 or f9 as any other x session can)? Note /etc/X11/Xwrapper.config must have allowed_users set to anybody as opposed to console. Or run it as sudo, I think thatll work too, but I donno if it might do something silly with your permissions. This way, your original session will not have its video settings changed at all; you create a new one which starcraft can change.

---

### Post by mriedel on 2008-04-26
Thank you for this idea, didn't think of it. But wouldn't I be unable to hear any sound from applications running on the primary x screen (music player, teamspeak)?

---

### Post by FrozenFox on 2008-04-26
You could try and find out and get back with us. I run all of my games in another x session and talk on ts or listen to music on xmms every day. I only have 1 monitor and a typical setup, however.

---

### Post by mriedel on 2008-04-26
OT: TS works for you on hardy? Check [http://ubuntuforums.org/showthread.php?p=4800767#post4800767](http://ubuntuforums.org/showthread.php?p=4800767#post4800767).

---

### Post by FrozenFox on 2008-04-26
Yes. Ts has worked for me on hardy since the earliest betas. I couldnt say if it works in the final version, since I don't use ubuntu anymore (i use Arch), but I don't imagine it would be any different.

I only had to go into alsamixer, play with the settings in f3 & f4, and enable some seemingly unrelated things (like analog mix or something?) and go to mic boost and press m (enable/mute) and it worked just fine. However, I DO NOT USE GNOME, I've always used KDE, so that may be the thing. Try installing kde, rebooting, then loading ts in kde and see if stuff works. The sound quality seemed to be the same as in windows or any other distro for me (note i use my own server with the highest codec possible. I suppose I could let you in for a bit if you want to test it that way or something). You must also run ts -before- you open any other sound-using apps. Like, right when the desktop loads would work fine. If i load UT2004 for instance, then try to load ts, it wont work and will keep me muted no matter what.

In short: I didn't have to do any special tricks to make TS work just fine, only turn my mic on and up in KDE with hardy as of maybe a month ago.

---

### Post by mriedel on 2008-04-26
Do you start teamspeak regularly or using the padsp wrapper? In case of the former, do you just use oss?

---

### Post by FrozenFox on 2008-04-26
Regularly. I didn't need to do anything but install it and make a shortcut.

Btw: It may just be me configuring it wrong, but I installed pulseaudio on Arch here and ts would not work at all with the wrapper for it. It just joined me muted, just as it did when I try to join ts after i load ut2004 instead of before it.

---

### Post by FrozenFox on 2008-04-26
Actually it seems I did have it set up wrong, and it does work correctly with the padsp. Hrm.

oh, and yes, in either case, I just use oss.

---

### Post by mriedel on 2008-04-27
Does your microphone work using padsp teamspeak?

**Update:** Mine does now, check [http://ubuntuforums.org/showthread.php?t=767515&page=2](http://ubuntuforums.org/showthread.php?t=767515&page=2).

The xinit solution doesn't seem to work for me, at least not as easily. In order for it to not fail, I need to delete my ~/.Xauthority file thus preventing myself from launching any more apps on my primary X. If I don't I just get "client rejected" on the new X.

---

### Post by FrozenFox on 2008-04-27
Odd, I've never had to do that on hardy or any other distro after setting the aforementioned file to "anybody" instead of "console".. though I use a modified xlaunch script from the gentoo forums to automate the stuff. :S Good to hear you got TS working, anyway. I'm out of ideas for the moment, but will post back if I figure out something helpful..

---

