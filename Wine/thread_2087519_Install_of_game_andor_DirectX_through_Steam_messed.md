---
title: "Install of game and/or DirectX through Steam messed up resoluton"
date: 2012-11-23
forum: Wine
---

### Post by Zeriercahl on 2012-11-23
I'm a bit long-winded so see bottom for quick version and specs.

**Friendly Hello:**
Hello all at the Ubuntu forums, I just recently built my own computer and decided to switch to Ubuntu for the extra coolness. I've been learning a lot through all this, and mostly been trying to figure out issues on my own (read: Google searches). However, I couldn't seem to find others with this problem so I've come here for help.

**Detailed Recount:**
So I just used WINE and WINETRICKS to install Steam. All went well and it worked. Then I went to trying a game out. I remembered that Orcs Must Die! worked from [http://www.steamgamesonlinux.com/](http://www.steamgamesonlinux.com/) so I tried that out. **After selecting to download it,** that's when the problem occurred.** The screen suddenly zoomed in!!! **I think it's the resolution right? Half the screen is cut off and I can't see parts of the right side of windows. My theory is that this is due to Direct X being installed through Steam, as Steam automatically installed it as I chose to download the game. It didn't even ask me to install Direct X or not ): It all happened so fast. This all being said, the game works fine! It looks a little strange, as if the resolution was off, but it played just fine.
[B]
What I did so far:[/B]
Restarted my computer. Didn't work -_- Researched Steam installing DirectX on Ubuntu then messing up resolution and couldn't really find anything. Researched uninstalling DirectX from Ubuntu but only found uninstalling DirectX after having been installed with Wine, not through Steam. Got mad and ate my feelings.

**Quick Version:**
Steam installed with Wine and Winetricks. Steam downloaded and installed game + DirectX. Resolution messed up now (I think; pretty sure), can't fix it, very annoying, halp!

**Specs:**
Ubuntu Version 12.04
Wine Version 1.4.1
Have not changed any settings in Wine
Using Winetricks
Graphics Card: [http://www.gigabyte.com/products/product-page.aspx?pid=4361#sp](http://www.gigabyte.com/products/product-page.aspx?pid=4361#sp)
Drivers: Proprietary (Installing those were a LOT of fun)
If any more information is needed I am ready to report.
[B]
Thank You:[/B]
Thanks a lot for your help and all the work you do to support noob ubuntuers like me (:

---

### Post by Zeriercahl on 2012-11-24
Did some more searching and found a command called xrandr
Tried "xrandr -s 0" but it didn't do anything.
Ran xrandr alone and terminal showed this:

> 
Screen 0: minimum 8 x 8, current 640 x 480, maximum 16384 x 16384
DVI-I-0 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480        59.9*+
   320x240       120.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)

Let it be known that I have a DVI to VGA cord running from my Graphics card to my monitor.

I've read elsewhere on this forum that to uninstall DirectX I should delete the .wine folder? I hope it doesn’t come to that but if it does, do I have to uninstall it as well?
Hopefully someone can point me in the right direction here ):

---

### Post by Zeriercahl on 2012-11-24
Looking into this xrandr command, I found this and tried to run it:
xrandr --output DVI-I-0 --mode 1024x768

But I was met with this message:
xrandr: cannot find mode 1024x768

I get the same messages for 800x600, 1400x1050, and seemingly any other combination of numbers.

Going into System Settings then Displays, my Resolution is set to 640x480 and there are no other options for me to choose from. Rotation has Normal, Clockwise, Counter Clockwise, and 180 Degrees. It's set to Normal and I haven't messed with that. Launcher Placement has Unknown and All Displays as its two options. It's set to Unknown, but moving it to All Displays doesn't seem to do anything. Finally, when I click Detect Displays, nothing seems to happen.

So once again, to reiterate, I need to fix my resolution here, and this problem seemed to be caused by Steam being run under Wine installing DirectX.

---

### Post by Artemis3 on 2012-11-27
This happens to me in a game, and doing alt enter twice (to switch windowed / full screen modes) cures it.

If the resolution remains changed after quiting the game, you have to set it up again (eg. in nvidia-settings). In some apps its unavoidable, but try using the same desktop resolution.

And yes, try renaming .wine or use another wineprefix to start from scratch.

BTW you should use steam for linux, some games download and don't run, but the binaries are there and can be run with wine... A few others have linux binaries and work out of the box (World of Goo, Team Fortress 2, etc...).

---

### Post by Zeriercahl on 2012-11-27
Thanks for replying but you're a little too late. In another thread talking about how to get rid of directx, it was recommended to get rid of wine, so that's what I did.
Shortly after that, the computer crashed and now Ubuntu won't launch soooo I've got bigger problems. If I can restore my desktop without a complete hard drive wipe then I'll come back to this.
Here's the thread for my new problem:
[http://ubuntuforums.org/showthread.php?p=12376062#post12376062](http://ubuntuforums.org/showthread.php?p=12376062#post12376062)
Edit: Ok scratch that. I think I made a type and apt-get purge wint\* instead of wine, which removed my desktop apparently. I reinstalled the desktop, but now I'm back where I started! Wine seems to be gone but the resolution is still messed up.
I also just want to make sure this is in actuality "resolution" that's my problem. The screen is appears all zoomed in and windows don't fit the screen. I have to Ctrl + Alt + arrow key to wove to other work spaces just to see entire windows, as they are stretching beyond the size of the screen and going into those work spaces. There was even a full screen program I couldn't close as I could only see the top left of it and could not see or reach the X at the top right. Is resolution really my problem?

I could really use some help here. This is really frustrating. I don't even care about steam anymore I have various work to do on my computer and it's been like this for days.
[]("http://ubuntuforums.org/showthread.php?p=12376062#post12376062")

---

### Post by Zeriercahl on 2012-11-27
@[Artemis3]("http://ubuntuforums.org/member.php?u=37597") Ok I'm in nvidia-settings but I don't know what to fix?

---

### Post by howefield on 2012-11-27
You could try deactivating the nVidia proprietary driver, and rebooting using the Nouveau driver. Easy enough to activate later.

---

### Post by Zeriercahl on 2012-11-27
I believe during my installing of the nVidia proprietary drivers adventure, I completely deleted the Nourveau driver.
That being said, there was a time, in between installing nVidia drivers and downloading Orcs Must Die! on steam, that nVidia drivers were working with my graphics card and everything looked great!
Is my goal just to deactivate and reactivate the nVidia drivers? Might that fix the problem?

More than anything I wish I knew WHAT my problem WAS. Other problems I've had so far have had clear errors either in terminal or an error window. This problem just messed up my display without telling me anything' so I'm just flailing around in the dark it feels.

---

### Post by TheSeventhChaos on 2012-12-08
I'm in the Steam for Linux beta and after trying out a few games, I do sometimes get a problem that sounds similar to yours. If the resolution in-game was set to 800x600 for example, that's what my screen resolution would be set to outside of the game as well.

So far I've found 2 ways to fix this:

1) You can go to your System Settings > Display, then change your screen resolution manually from there back to its default.

2) Or, you can just simply log out of your session and then log back in. Although, this means all of the applications you have running will close.

I'm running Linux Mint 14, so I apologize if these don't work for you on Ubuntu, although I don't see why they wouldn't since Mint is based off of Ubuntu.

Hope this helps.

---

### Post by Zeriercahl on 2012-12-08
Thanks for the response Mr. Chaos. However both of those solutions were tried and did not work. For some reason, in System Settings > Display, there was no other listed resolution. A restart similarly had no effect.
In my research I've found that there is a problem with Steam and other games on Linux that changes the resolution but does not change it back and can be solved with the solutions described above.
However, my problem was different, and I could not find a solution, from these forums or others, so I had to reinstall the OS. I do believe it was an issue with the proprietary drivers, though I'm not even totally sure on that. I'm not going to run Steam with wine though in fear of it happening again. I'll just wait for the Linux client I guess -_-

I wouldn't say the problem is solved as if it ever happens again I'll have to reinstall my OS which is obviously not something I want to do every time I want to play Orcs Must Die. If anyone seems to be having this issue post here and I can share any info I might have (though I think I was pretty detailed above, if you read through it all). If anyone thinks they know the cause or a solution feel free to post it here for prosperity. Thanks ubuntuforums

---

