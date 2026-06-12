---
title: "WoW is a bit laggy!"
date: 2007-12-12
forum: Wine
---

### Post by Nando-san on 2007-12-12
I've tried i've looking around the posts, so sorry! I'm running WOW fine in wine... but when all the settings are in high or almost high, IT'S LAGGY as hell! I used to have Vista in this PC... i remember i had to download some driver because the screen would turn black for some seconds... BUT it never lagged... can any1 help me? If i turn every effect off it runs nice... but i want to run high (not smoking lol)! any help would be appreciated THANKS beforehand!:popcorn:

---

### Post by hikaricore on 2007-12-12
You need to say what mode you're running the game in. OpenGL or D3d?
Also your video drivers/hardware would be helpful.  Along with your resolution and what registry tweaks you've made per the many guides on the Internet and Ubuntu Forums for running  WoW via WINE.

I'm very sorry to hear that your machine was perviously infected with Vista.  Congrats on the recovery.

---

### Post by Nando-san on 2007-12-13
well that's the thing...it's just running on wine normally... i know for certain i don't have the SET gxApi "opengl" on the config because if have it on graphics start missing, and it performs VERY poorly. So i just launch it from the Desktop and it runs "fine". Aparently i don't know what graphics card I have, but in the Screens and Graphic menu of ubuntu it says I have an Intel 945. My preferable resolution is 1680x1050, but I can't get even near to it, and less likely in WoW when it runs on Wine, the screen size gets smaller... like a default play for WoW.

I HAVE NOT DONE THIS REGISTRY thing:
This is a simple registry edit for Wine that will dramatically increase the framerate in game. It is gathered from this thread on Ubuntuforums.org: [WWW] [http://www.ubuntuforums.org/showthread.php?t=303509](http://www.ubuntuforums.org/showthread.php?t=303509)

Open a terminal window, type regedit and press enter. This will start the Wine equivalent of the windows registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same.

   1.

      Find this key HKEY_CURRENT_USER\Software\Wine\
   2.

      Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
   3.

      Click right on the wine folder and select [NEW] then [KEY]
   4.

      Replace the text New Key #1 with OpenGL
   5.

      Click right in the right hand pane and select [NEW] then [String Value]
   6.

      Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
   7.

      Then double click anywhere on the line, a dialog box will open.
   8.

      In the value field type GL_ARB_vertex_buffer_object


maybe there's my problem...???

---

### Post by hikaricore on 2007-12-13
I'm sorry to say that the intel series of cards/drivers have terrible opengl support, which is why you'd be missing graphics when using this mode.
The game sometimes runs alright in d3d mode for the users of such gimped video hardware, but I'd have to suggest a lower resolution and lower detail settings.

If this is NOT a laptop system I suggest getting a decent Nvidia card and your troubles will be over.

---

### Post by Nando-san on 2007-12-13
but it used to run SO WELL on Windoes :'(! i'd hate to just make a Windows partition to just play this.... I know i would just start using Windows again, if that were the cause ANDI  DONT WANNA lol! thanks 4 the help though!...let me c what i can find searching, most helpful!

---

### Post by hikaricore on 2007-12-13
The only reason it ran well in ***dows is the card makes use of DirectX, the ***dows drivers were also written to properly use DirectX.  Since DX is a closed source vendor lockin device for Microsoft, there is a lot less Intel can do with its driver for Linux.

---

### Post by Nando-san on 2007-12-14
ohhh kk i got it lol! well let's see what can be done LOL! thanks!

---

