---
title: "going on 4 days, and I have yet to play a single round of team fortress 2"
date: 2009-01-09
forum: x86 64-bit Users
---

### Post by sshizzle on 2009-01-09
So far, I have to say that while ubuntu is nice for most things, getting my games to work has been an absolute nightmare.

It's looking more and more like I'm just gonna drop that green-green for Vista 64, which is the last thing I want to do.

I've had so many issues that I'm not sure where my problem now lies, but here is my situation:

I have 8.10, I've successfully installed Wine, Steam, Team Fortress 2...

I thought I had the video driver (180.22) installed correctly, but the the one time that I managed to actually load into a TF2 server, it looked like I was playing Duke Nukem circa 1995. I was getting about 1-2 fps, and my ping was something like 9000ms.

Is my driver the problem? I tried reinstalling an older one (177.82), and now I can't even get TF2 to load. I get errors like "No permissions to run tf" or something about "MountAppFilesystem() failed: SteamMountAppFilesystem(440,0,0x776a57c4) failed with error 1: The registry is in use by another process, timeout expired" when I try to run it again. Restarting steam doesn't work, neither does restarting system.

What is my issue with Wine?

Next...
I got so frustrated with Wine that I downloaded VirtualBox, installed WindowsXP, installed Steam, and am currently downloading TF2, but I suspect this will not work because VirtualBox uses some software driver emulator rather than the actual nvidia driver.

Is VirtualBox good for anything TF2 related? (playing or dedicated server?) Or is it just another dead-end?

---

### Post by Yellow Pasque on 2009-01-09
Why would you need Vista? Why can't you just dual-boot with Win XP and run your games there?

---

### Post by sshizzle on 2009-01-09
quick update:

I'm back to the point where I can play TF2, but I'm still getting only 15 fps and my ping is over 500. Normally I'm getting 60-80 fps with all the graphic settings maxed out, and my ping is usually 40-80ms.

I used envyng again, and installed the 177.82 driver. I'm going back to try an even older driver now, but I suspect that my problem still lies elsewhere...

People keep telling my to get the new drivers 180.22, which leads me to believe that someone has actually gotten TF2 working in 8.10 64bit. If anyone that reads this has ACTUALLY run TF2 inside 8.10 64bit, please say so.

---

### Post by sshizzle on 2009-01-09
> **Temüjin said:**
> Why would you need Vista? Why can't you just dual-boot with Win XP and run your games there?

I would like to have everything running inside Ubuntu, rather than dual-booting. First, its just kind of a pain in the ***. Second, why should I devote a partition of my HD to WindowsXP when it is apparently possible to do without it?

---

### Post by Yashiro on 2009-01-09
Because the software you want to run is written to run only on Windows.

Wine under Linux/MacOSX will NEVER run the most popular games as well as Windows.

So if you want to play games written for Windows, you sadly need Windows.

---

### Post by ushimitsudoki on 2009-01-09
I run TF2 under Wine in 8.10 amd64 with no problems. (Well, very minor problems: I can't get Japanese text to display properly.)

---

### Post by sshizzle on 2009-01-09
> **ushimitsudoki said:**
> I run TF2 under Wine in 8.10 amd64 with no problems. (Well, very minor problems: I can't get Japanese text to display properly.)

Great, so it can be done!

...now if you could just help me out a bit by answering a few questions about how you got it working...

What video card are you using?

What video driver are you using?

How did you install the video driver? envyng or manual install or other?

Did you load Steam and TF2 from the discs and then update, or did you install steam and download TF2?

Did you have to modify your game file/add console tags/or perform any other changes?

Any help would be appreciated!!!

---

### Post by ushimitsudoki on 2009-01-10
I'm running 2x8800GTS 512 (not SLI, so I don't think the 2nd one really matters in this case)
Drivers: 180.22 (Manually installed)
I installed Steam and then downloaded TF2
Launch options: -width 1920 -height 1200 -dxlevel 81

I needed to set up a Metamode to turn off one monitor, but that is a multi-monitor issue. 

I hadn't played in quite a while, so I just jumped on an played a bit of a game - everything worked as I remembered. Steam/TF2 has worked for me since Gutsy and countless Nvidia drivers. I've also played HL2 and Portal.

Framerate and ping seem fine to me.

---

