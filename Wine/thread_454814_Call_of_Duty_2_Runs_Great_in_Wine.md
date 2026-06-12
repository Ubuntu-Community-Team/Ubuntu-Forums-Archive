---
title: "Call of Duty 2 Runs Great in Wine"
date: 2007-05-25
forum: Wine
---

### Post by Jonathan2007 on 2007-05-25
I just wanted to let everyone know that Call of Duty 2 runs great in Wine. I am using 0.9.37   [http://appdb.winehq.org/appview.php?iVersionId=3794](http://appdb.winehq.org/appview.php?iVersionId=3794)

I used the DVD install version and installed it without a hitch (I am not sure how the CD version would work since that involves multiple CD's).
I then downloaded the 1.3 upgrader and installed that. It installed fine.
I then went online and found a 1.3 no-cd crack for single player.
I opened winecfg and changed the sound driver to OSS and Hardware Acelleration to Emulation and enabled Driver Emulation.
Then I opened the user.reg in ~/.wine folder and put this part in anywhere
> [Software\\Wine\\Direct3D]
"OffscreenRenderingMode"="backbuffer"
"PixelShaderMode"="enabled"
"UseGLSL"="enabled"
"VertexShaderMode"="hardware"
"VideoMemorySize"="256"
That allows Single Player to work correctly. I didn't put that in at first and then first few levels ran and then I hit a Directx error. Once I put that in the user.reg file it worked flawlessly.

I just played online and it worked great. The gameplay was as good or better than in Windows. I think I can finally dump Windows (although I may keep it around but I'll probably reformat and not install games and just use my Mepis Linux install now for games and regular desktop stuff).

The server I normally play on doesn't require Punk Buster so I don't have any issues with that (I have heard Punk Buster doesn't work correctly/at all in Wine).

The only issue I am having and have yet to resolve is sound. I am using the OSS driver as stated above which works a ton better than ALSA (which freezes me up immediately and quits the game). But I get a lag of about 1/2 - 1 second. It is really annoying and I have tried multiple combinations of audio driver settings and nothing gets any better than my above settings.

Anywho it is working good enough and I am so glad the Wine people are constantly making improvements and changes. Thanks Wine team!

---

### Post by jpdotkom on 2007-08-11
I had the sound lag issue but have now resolved it.

If you wanna test to see if your box is capable of 'miles sound' drivers then download 'the miles sound tools' and install with wine.

[http://www.radgametools.com/mssdown.htm]("http://www.radgametools.com/mssdown.htm")

After installation simply find an mp3 and run it.

As for the sound fix run 'winecfg' and go to the audio tab.
check 'OSS Driver'
Hardware Acceleration 'Full'
Default Sample Rate '22050'
Default Bits Per Sample '16'   <-- This defaults to '8'
Un-check Driver Emulation

Other settings:
CoD2MP_s.exe runs with XP libraries

ubuntu 7.04, wine 0.9.42

---

### Post by canopus4320 on 2007-10-13
thanks!! it worked just fine

i'm playing it under wine 0.9.46 and feisty, sometimes with some audio sync problems, but it runs almost just like under windows

my specs:
asus 7800gs pci-e
2 gb ddr2
athlon x2 4400
mobo asus m2n32-sli deluxe

---

### Post by dmn_clown on 2007-10-13
> **Jonathan2007 said:**
> [Software\\Wine\\Direct3D]
"OffscreenRenderingMode"="backbuffer"
"PixelShaderMode"="enabled"
"UseGLSL"="enabled"
"VertexShaderMode"="hardware"
"VideoMemorySize"="256"

A couple things here:  ```
wine regedit
``` to edit the registry, it will go a long way to eliminate some syntax errors in the copy-paste method.

> "OffscreenRenderingMode"="backbuffer" is kinda pointless as it is wine's default behavior

Useful registry keys can be found here: [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

The game plays better with a more recent wine 0.9.45+ fixes an annoying bug in single player.

Also the game does not play like it is in windows because no matter what settings you use, it defaults to the directx7 renderer and water is rendered as a blue plane rather than being a reflective surface.

---

### Post by Qwerty_ on 2007-10-14
Did anyone have trouble patching to 1.3?

---

### Post by Jonathan2007 on 2007-10-14
Check here for more info about upgrading to 1.3 [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3794](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3794)

---

### Post by wrecche on 2007-10-21
> **canopus4320 said:**
> thanks!! it worked just fine

i'm playing it under wine 0.9.46 and feisty, sometimes with some audio sync problems, but it runs almost just like under windows

my specs:
asus 7800gs pci-e
2 gb ddr2
athlon x2 4400
mobo asus m2n32-sli deluxe

Well I did all of this, it runs fine except that it forces my resolution to something bigger than I use by default, and also limits my frequency to 50hz. Making for a very crap game.. fps under 50. :(

I usually cap my fps at 125, so this is painful to play..  *sigh* spose I have to keep my windows partition afterall.. :(

:(

---

### Post by PLAY3ER on 2007-10-29
Hi all, i am having problem installing the game, i got the game via download from [http://www.direct2drive.com/]("http://www.direct2drive.com/") 

and i can't install it under 7.10 , the wine version i have is 0.9.37, i have also tried 0.9.47 nether have work, i have also tried using a windows installation by copying it to my linux drive, no luck, something about HTML rendering, and the thing it tells me to install doesn't install, i'd like to use Ubuntu over Vista, but, don't wanna quit gaming.

                         Thanks for all your help, also my PC specs are below

AMD 6000+
160GB HD /Vista-80GB-Ubuntu-30-Back up-30
2GB of DDR2 RAM
ASUS M2N4-SLI
Nvidia GeForce 8600GT (x2)
600W Power supply

---

### Post by Crafty Kisses on 2007-10-29
Yeah I really like CoD2, just never got it working. :(

---

### Post by desertboy on 2007-11-01
Works fine for me, no tweaking but only single player.

---

### Post by wingnux on 2007-12-30
IT works fine here but the movies won't display, I can only hear the audio =/ Any hints?

---

