---
title: "WOW Question.."
date: 2008-01-30
forum: Wine
---

### Post by sinteres on 2008-01-30
Hello, I'm very new to Linux, and I am trying to get WOW working. I have read a lot of the forums and guides to get it working. I have it almost there, but I've run into an issue that I am not finding anyone posting about.

When I launch Wow, my character models do not show up, I can see their weapons and armor, but no character. When I select one of them, the game loads, but freezes a few minutes into the game.

I've tried modifying the wtf file, but if I add:

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"

The game won't load at all, I've tried changing the SET gxApi "d3d" as well with the same results. 

I have done the registry hack and loaded the applytoforehead add on as well. 

Any help would be greatly appreciated.

Thank you,
sinteres

---

### Post by Vadi on 2008-01-30
Quick question, have you tried with Compiz off? This could be a driver problem.

In the terminal, do **metacity --replace** to disable compiz (**compiz --replace** will get it back).

---

### Post by sinteres on 2008-01-30
Vadi, thank you so much for the suggestion. I tried this and receive the same results.

Thank you

---

### Post by Vadi on 2008-01-30
Okay, so not a compiz/driver problem..

Can you try launching WoW from the terminal? Then it might give clues as to why as it crashing. (I don't know the command for that, sorry - I don't have WoW. Try and find out the terminal command the launcher invokes if you can).

---

### Post by sinteres on 2008-01-30
Well it does not show the character models before it crashes. So I start the game and all is ok, I can see all my characters listed, but none of them have models. The game will stay like this and not crash, but when I choose one of the characters and the game loads, I get into the world, then a few minutes later it just freezes, maybe because it can't load the character models of the other users in the game? I think if I can fix the issue with the character models not showing up, then it should fix the game crashing/freezing..

Thanks

---

### Post by pissedoffdude on 2008-01-31
What kind of graphics card do you have? Have you properly installed the correct display drivers?

---

### Post by Laibcoms on 2008-01-31
I am not sure with this, but if you have NVIDIA, install the real NVIDIA driver.

I haven't tried running WoW using the FLOSS NVIDIA driver.  I switched to the official driver before trying to run WoW and all is well (except for the wine-related bug where WoW will always crash upon exit/logout).

---

### Post by sinteres on 2008-01-31
I'm using an onboard intel card.. I'm not sure the model number and I'm not sure how to find that in Ubuntu.. sorry.. 

I believe the drivers are installed properly, everything else seems to run fine graphically, I can change the resolutions.

Thanks,
Sinteres

---

### Post by Resonance378 on 2008-01-31
Even though this is posted for an ATI card it might be worth a shot: [http://www.wowwiki.com/Linux/Wine/Troubleshooting#ATI_no_Object_Textures.2FModels](http://www.wowwiki.com/Linux/Wine/Troubleshooting#ATI_no_Object_Textures.2FModels)

I have an ATI card and had to use this.  As far as you'll hear from a great number of people - WoW will not run on an onboard Intel Video chipset.  Don't let that stop you from trying though - your success could help out a couple hundred people; just post what you did if you get it working.

---

### Post by Vadi on 2008-01-31
> **sinteres said:**
> I'm using an onboard intel card.. I'm not sure the model number and I'm not sure how to find that in Ubuntu.. sorry.. 

I believe the drivers are installed properly, everything else seems to run fine graphically, I can change the resolutions.

Thanks,
Sinteres

I found Hardinfo ([click]("http://www.getdeb.net/category.php?id=3")) to be a very useful program to hardware information.

---

### Post by sinteres on 2008-02-01
Resonance378 - Thank you for your suggestion, this seemed to describe my problem exactly, unfortunately I added the

SET M2UseShaders "0"

in the wtf file and it did not make a difference. 

Vadi - I downloaded the hardinfo program, and this is what it is reporting:

-Computer-
Processor		: Intel(R) Celeron(R) CPU          530  @ 1.73GHz
Memory		: 1025MB (489MB used)
Operating System		: Ubuntu 7.10
Date/Time		: Fri 01 Feb 2008 02:47:44 AM CST
-Display-
Resolution		: 1280x800 pixels
OpenGL Renderer		: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA Intel
-Input Devices-
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 PS/2 Mouse
 AlpsPS/2 ALPS GlidePoint
 Power Button (FF)
 Power Button (CM)
 Lid Switch
 Sleep Button (CM)
 Microsoft Basic Optical Mouse
-Printers-
No printers found
-IDE Disks-
-SCSI Disks-
Optiarc CD-RW CRX880A
ATA Hitachi HTS54168


Thanks,
sinteres

---

