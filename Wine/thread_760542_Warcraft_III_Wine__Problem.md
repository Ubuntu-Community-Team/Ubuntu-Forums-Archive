---
title: "Warcraft III Wine  Problem"
date: 2008-04-20
forum: Wine
---

### Post by DocHolliday2006 on 2008-04-20
Hey guys. I'm brand new to wine. I installed it, then installed Warcraft III. The game loads just fine, and I can navigate menus, etc. I can even watch the intro movies, but I renamed the movies folder folder because I was told that might be causing problems, so they're no longer playing.

My problem is that when I click on campaign and try to load the first mission, the loading bar freezes after it's loaded about 2/3 of the way every time.

The wine readme suggests that I switch to a default of OpenGL, but it tells me to go into regedit and find a file that appears to be absent.

It says:
	
"REGEDIT4" - Why four? Is it different from regedit?

"[HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III]
"Gfx OpenGL"=dword:00000001 "

I get to Warcraft III but there is no GFX OpenGL setting that I can find.

---

### Post by Hairy_Palms on 2008-04-20
you need to run tft with the opengl switch, add -opengl to the command you are using to run it.
also the movies have always worked fine for me.

---

### Post by DocHolliday2006 on 2008-04-20
I don't know what tft is.

I'm not using the console, so I'm not using a command. I'm going through the applications tab, going to wine, and then going into warcraft 3 that way. Could I alter the .exe file to do it?






> **Hairy_Palms said:**
> you need to run tft with the opengl switch, add -opengl to the command you are using to run it.
also the movies have always worked fine for me.

---

### Post by funguy on 2008-04-21
I've never used the -opengl myself and it works fine. You should post your config file so we can see what you got going on. Make sure you erase the private info, like your name.

---

