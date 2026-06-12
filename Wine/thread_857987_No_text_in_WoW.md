---
title: "No text in WoW"
date: 2008-07-13
forum: Wine
---

### Post by kipman on 2008-07-13
Hi all,

I am having a problem with WoW in Wine on 8.04. Vid card Radeon 9000

When running it, everything runs fine for a few seconds, then the text disappears for everything - even in the WoW menu (pressing esc). Not sure if it&#347; related but also when indoors the minimap appears white.  

wtf config file contents shown below - (additional parameters at top of file).

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET UIFaster "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET doodadAnim "0"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "450.000000"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET locale "enUS"
SET coresDetected "1"
SET videoOptionsVersion "1"
SET accountName "XXXX"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET spellEffectLevel "0"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET realmName "Bronzebeard"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "14"
SET minimapZoom "0"
SET Gamma "1.000000"

---

### Post by kipman on 2008-07-14
Ok so i have tried nearly everything.. removing and re-adding lines in the wtf config file, disabling the firewall. And it&#347; a shame its not working cause it appears to be running the fastest I have seen it go. But the text just wont work. It still disappears after the character model is loaded. All text. I thought there may be an error message in the terminal after loading wow from there, but no. 

Ok So now I have it down to when I go from indoors to outdoors (or visa versa). I have read in the how-to: 

¨Alternatively try using the linux minimap add-on, possible compatibility issue with XGL.¨ 

What does this mean?

---

### Post by flytripper on 2008-07-14
dunno, maybe try installing the ms extra fonts ..can anyone point to the repos for that?

---

### Post by kipman on 2008-07-14
> **flytripper said:**
> dunno, maybe try installing the ms extra fonts ..can anyone point to the repos for that?

Well i would have thought that too, but I had installed the fonts before i started the install. Plus the fonts only disappear when i move indoors (plus the mini-map goes white). So im not really sure. I mean i can play it when outdoors but then thats only half the game really isnt it. 

After looking at all the troubleshooting tips it mentions something about a linux- minmap addon / gfx bug, but its a little difficult to find any info on this. Anyone know anything about it.

---

### Post by barato on 2008-07-14
I also had this problem. What you will need to do is go into your .wine/Windows/fonts directory and to download the Tahoma font into that directory.
Here is a link for the font : [http://www.fontstock.net/download/11080/Tahoma.html](http://www.fontstock.net/download/11080/Tahoma.html)
After you put the font into that directory then the game should work perfectly, text and all

---

### Post by kipman on 2008-07-15
> **barato said:**
> I also had this problem. What you will need to do is go into your .wine/Windows/fonts directory and to download the Tahoma font into that directory.
Here is a link for the font : [http://www.fontstock.net/download/11080/Tahoma.html](http://www.fontstock.net/download/11080/Tahoma.html)
After you put the font into that directory then the game should work perfectly, text and all

Thanks for your help, i really appreciate it. But it doesn't work for me. The problem isn't that the text is displaying incorrectly, everything works perfectly, until i go indoors it disappears along with the mini-map (goes white).

I know that there is an issue when going from indoors to outdoors (or visa versa) but every troubleshooting page mentions downloading a Linux mini-map addon, which I cant find any info on anywhere.    

Any ideas?

---

### Post by thisismalhotra on 2008-07-15
The add-on is called Appytohead or Applytoforehead, google it.
All it does is disables you minimap cause that is what cause the bug. I don't remember but there is a way to disable your minimap from the wtf file. google that too

GL

PS: I will try to find the link, if I do I will post them

---

### Post by Mahinva on 2008-07-15
Here's a link to ApplyToForehead:

[http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html](http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html)

Personally, I have not encountered the problem of my minimap blanking to white upon entering inside buildings. If I've read correctly, this is because I'm using an nVidia card.

However, my husband, who uses a ATI Radeon 9800XT, has this problem. His minimap whites out inside buildings, and has also whited out in instances - he has run Blackfathom Deeps without a minimap, and the same I'm sure for Razorfen Kraul. I have read that ATI will be fixing this problem hopefully soon in a driver update. I am wondering if this white minimap has been a problem to ATI users for a while, or if this suddenly occured. I just got my husband's computer switched over to Ubuntu a few days ago so I'm learning how to work with his system, as well as my own.

As I haven't used ApplyToForehead, I can't offer much advice on it. However, if you find yourself unable to use your minimap when in an instance, you may want to consider one of the many instance map addons - they can't show you where you are like the minimap can, but they do provide an overview of the entire instance. InstanceMaps is the addon I use, although there are several others.

As far as the text not displaying, I am at a loss. The font face does not change when you go from indoors to out, so it shouldn't be the issue of not having X font. Have you tried running the game without **SET gxApi "opengl"** by any chance? This could be an issue with your driver - that's what it sounds like to me. Unfortunately, I don't have much experience with ATI cards, or Wine/WoW, since I'm a fairly new user.

> **flytripper said:**
> dunno, maybe try installing the ms extra fonts ..can anyone point to the repos for that?

Extra MS fonts can be found in the Synaptic Package Manager. Search for "msttcorefonts". WoW's default fonts are as follows:

* FRIZQT__.ttf (the main UI font)
* ARIALN.ttf (the normal number font)
* skurri.ttf (the 'huge' number font)
* MORPHEUS.ttf (Mail, Quest Log font)

This last bit of informations taken from [http://clearfont.co.uk/readme.html#Install](http://clearfont.co.uk/readme.html#Install) Clearfont is a font replacement addon that allows users to change the game's default fonts from a pre-defined package. Alternatively, you could download or make your own packages.

Finally, if you wanted to try changing the fonts without the use of an addon, you could create a folder called "Fonts" (capitol is important) and place it within WoW's folder. You want it to be alongside the Interface folder, NOT inside it. Place your fonts into the Fonts folder and rename them as stated above. To restore fonts to their defaults, you may simply just need to remove the Fonts folder. If that doesn't work, you'll want to download the actual fonts and stick them into the Fonts folder - deleting your custom fonts in the process.

It may be worth a shot, but I do not think the type of font you have is the problem.

---

### Post by Spydr4590 on 2008-07-16
Note: You have to do this or text will become unreadable, and this does increase your FPS..

 Registry Tweak for FPS Boost

Open a terminal window, (konsole/terminal/x terminal etc..), type regedit and press enter. This will start Wine's registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same.

   1. Find HKEY_CURRENT_USER\Software\Wine\
   2. Highlight the wine folder in the left hand pane by left clicking on it. The icon should change to an open folder.
   3. Click right on the wine folder and select [NEW] then [KEY].
   4. Replace the text "New Key #1" with OpenGL (CaSe Sensitive).
   5. Right click in the right hand pane and select [NEW] then [String Value].
   6. Replace "New Value #1" with "DisabledExtensions" (CaSe sensitive).
   7. Then double click anywhere on the line, a dialog box will open.
   8. In the value field type "GL_ARB_vertex_buffer_object" (without the quotes). 

Note: If you are unable to rename the newly created key "New Key #1" to "OpenGL" then expand the left hand pane of the regedit window using the vertical divider bar. You should now be able to change it. A known bug in Wine is causing this unwanted behavior.

You should see a significant performance gain.

---

### Post by kipman on 2008-07-16
Thanks all. I really do appreciate it. I have found that if i close the minimap when going indoors fixes the problem, well not really fix, but good enough. Thanks again!

---

### Post by Dlambert on 2010-08-28
I know this may be REALLY LATE, but i got it to work by installing he chinchilla Mini map add-on:KS:KS:KS:KS:KS!

---

