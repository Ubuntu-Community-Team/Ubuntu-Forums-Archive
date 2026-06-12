---
title: "Problem executing StarCraft under Wine"
date: 2008-02-15
forum: Wine
---

### Post by JohnCardozo on 2008-02-15
Im trying to execute StarCraft under Wine but it show these message:

fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
wine: Unhandled page fault on read access to 0x0000087c at address 0x7d516481 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0000087c in 32-bit code (0x7d516481).

I think is something related with the video drivers or it's capability to execute OpenGL.
Thanks to anyone who could help me... I've been trying for an entirely month and nothing...

OS: 
	Ubuntu 7.10
Machine: 
	Dell XPS M1210
	Intel Centrino Duo
	2 Gb RAM
Video:
	nVidia Go 7400 graphics card	
Wine:
	wine-0.9.54

---

### Post by Sugi on 2008-02-16
It looks like you are having issuses with your DirectDrawRenderer.

> DirectDraw Mode
You must have DirectDrawRenderer in the registry set to "gdi" (which is the default) for Diablo to work. If you have changed it to "opengl" at any point then the game will crash after the Blizzard logos.

Even though, that is for diablo, it will work for anything requiring DirectDrawRenderer.  Try it.  The odd thing is, Starcraft was one of my firest and easiest games to install.  :-/  So, at least it should be too hard to play.

By the way, Your laptop specs are quite close to mine.  You could do a lot heavier gaming if you wanted to. :)

Sugi

---

### Post by JohnCardozo on 2008-02-18
I'm kind of new in Linux. I've done some little things in Ubuntu. When you say that I must have DirectDrawRenderer in the registry set, you are refering to wine's registry or a system file? What do I have to do?

Thanks again...

---

### Post by JohnCardozo on 2008-02-18
If I have to update Wine's registry, what is the path where I should add the key?

Thank you

---

### Post by JohnCardozo on 2008-02-18
I have read that I have to activate DRI but I don't know how...

:s

---

### Post by lastredoubt on 2008-02-18
I was just told this myself by happyhamster, so full credit to him is due, but here's what he said in reference to me and Diablo II:

> - Just a long shot: try setting the DirectDrawRenderer to gdi in the wine registry (default = opengl).
A quick way of doing that is pasting the following lines in an empty text file and saving it as diablo2.reg (or any name of your liking).

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="gdi"

- Then import it into the registry using:

wine regedit diablo2.reg

- If you want to change that setting later (to opengl), either make another textfile and proceed as above, or just use the bare command:

wine regedit

- and change the setting manually. Good luck.

So there you are.  If you want to do it manually, type 'wine regedit' into terminal, and follow the file structure outlined above...double click on the entry and type it in.

---

