---
title: "WoW Launcher Updating Tools problem help"
date: 2012-04-22
forum: Wine
---

### Post by Eliyah on 2012-04-22
Hello!

After spending some hours trying out to install World of Warcraft in Kubuntu 11.10 with wine 1.5 and wine 1.4 I found a solution for me.
As described in several forums there's a problem with updating the launcher tools. For me for example it  hangs up after a few seconds. I tried it out with disabling P2P, another wine-version, but nothing worked for me.
Finally I found a nice solution by updating the tools manually and I want to share this solution for everyone who has the same issue like me

I wanted to install the game from the Client-Installer available on Battle.net
First it works until the game wants to update the Launcher Tools. Cancel this and follow the next steps

1. Download the updated tools from [http://patchup.info/launcher/#toolszip](http://patchup.info/launcher/#toolszip)
2. copy the included files into your World of Warcraft folder
3. start the launcher (wine Launcher.exe)
4. be happy :)

My game is downloading at the moment I'm writing this and I hope I can help some of you with the same problem

My system:
- Kubuntu 11.10 64Bit
- wine 1.5.2

---

### Post by dforthman on 2012-04-26
I love you. I've been trying to get WoW to work all day after doing a fresh 12.04 installation. Tried anything and everything I could think of and never got it to work.

This worked like a charm and I'm finally getting to install the client. Thanks for sharing this!

---

### Post by naggu on 2012-04-28
This solved my launcher problem. I clean installed Ubuntu 12.04 64-bit and was having issues updating launcher. Still cannot get Game/downloader preferences window. It will be just blank screen.

Now my WOW client is downloading at full speed :)

---

### Post by jinyopy on 2012-04-28
I just downloaded Ubuntu and just registered to say thanks for helping me... I was about to pass the whole game piece by piece from my old laptop but i saw this. Thanks... Time saver. :D

---

### Post by TheFlamingBush on 2012-05-07
Great fix thankyou... im using 10.04, and ran into this problem but it fixed the download problem for me instantly :)

---

### Post by Smakone on 2012-05-08
How does the game run with this solution?
Does wine crash?

---

### Post by Eliyah on 2012-05-08
I'm playing WoW with this solution now for two weeks and have no problems. Even after I updated my system to kubuntu 12.04 64Bit the game is running perfectly for me.

No problems ingame or wine crashes.

---

### Post by farfromport on 2012-07-13
I registered just to tell you thank you for publishing this, made my day.

---

### Post by Crossbow on 2012-08-30
This is EXACTLY the problem I'm having, but that link no longer works. 
:frown:

---

### Post by linuxninja39 on 2012-09-01
The link is not working for me either. Anyone know where we can get the file?

---

### Post by Crossbow on 2012-09-01
Maybe this?

[http://patchup.info/wow/downloads/]("http://patchup.info/wow/downloads/")

I downloaded the one for Windows but still can't launch the game. The last message in the log is that the downloader stopped communicating with the launcher. No idea what to do about that.

---

### Post by Crossbow on 2012-09-02
Okay, I KNOW if I start a new thread on this I'm going to get smacked down for not having searched previous threads, even if I link to the ones that did not help me. 

We tried this:
[http://us.battle.net/wow/en/forum/topic/6412402228?page=2#27](http://us.battle.net/wow/en/forum/topic/6412402228?page=2#27)

My sister was helping me. She wrote this:

> At step 4 where I typed:
     wine -opengl Wow.exe

It returned the following error message:
     wine: cannot find L"C:\\windows\\system32\\-opengl.exe"

I found opengl.dll, but no opengl.exe when I looked in the directory of the error message.

I don't really know what that means. I know when I try the launcher OR the background downloader and open the system monitor it says they are sleeping and in "pipe_wait." I don't know what that means so I let each for for a couple hours, nothing happened. WoW-4.3-5.0.15890-enUS-Downloader.exe gives me the "checking for updates" message but the system monitor still says it's sleeping and in pipe+wait. I let that alone overnight, with no change. 

Running:
Ubuntu 12.04
wine 1.5.5

---

### Post by cwwilson721 on 2012-09-02
Wrong order...

It's:
```
wine Wow.exe -opengl
```

That means Run wine, open Wow.exe, using opengl. The way you had it was Run wine, then it had no clue what you meant after that because there is no '-opengl' command for wine to run

---

### Post by Crossbow on 2012-09-03
I let this update overnight. Game is fully loaded now and can play. The sound had a horrible crackling and was cutting out and the game was freezing and when it crashed it threw me all the way out of Ubuntu. 

I found a thread on how to fix the crackling sound, and that worked but only for the crackling. I found another that said to enter exact values into the audio on Wine instead of using the system defaults, but my Wine config doesn't have that option, just a drop down menu. 

Other threads said I must kill Pulseaudio, but still others said I must have Pulseaudio. Another said I need to tinker with ALSA but I don't know where to find that. So. Ongoing problems:

Sound cuts out
Graphics/movement freeze
Game boots me completely out of the OS when it crashes

Running: 

Ubuntu 12.04
Wine 1.5.12
GeForce 8300GS
NVIDIA 304.43

ETA: Killing Pulseaudio made no difference.

---

