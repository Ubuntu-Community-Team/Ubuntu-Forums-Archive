---
title: "WoW works great!  War3?  Not so much..."
date: 2008-08-20
forum: Wine
---

### Post by k1ngb0b0 on 2008-08-20
Hello everyone.

I have World of Warcraft installed (using wine) and it works perfectly.  I also have warcraft 3 installed and it works....less than perfectly, here's my problem.

WoW video options let you run in 'window' mode.  They also give you options to maximize the window, and prevent resizing.  Why is this important?  Because if you run in this fashion you use your desktop gamma and visual settings, instead of the games.  It helps if you alt tab between programs or cube rotate to run other things.  Now, these are video options in WoW and not in Wine.

I can't get this same thing to work with War3.  If I run in window mode the game is really hard to play because of the boundaries of the screen.  Things like scrolling and moving units is very difficult because moving the mouse to the top doesn't move the screen well.

Does anyone know if there is a way to set up my war3 to work like WoW?  There's no individual video options like I had with WoW and that's what worries me about it.  

I'm hoping someone here has had a similar problem and found a solution :guitar:

---

### Post by k1ngb0b0 on 2008-08-26
I found out my problem.

There's currently a winebug that causes a crash when users alt tab or switch workspaces.  

There's a patch floating around that is supposed to fix this bug, but the problem is that I use 64 bit Unbuntu and the patch is for 32 bit.  Does anyone know if someone made a 64 bit version of this patch, or how I can rig my wine to work?

---

### Post by shae on 2008-08-26
You can try using wine from my repository (see link in my signature).  I apply the appropriate patches for it to work with Warcraft 3 (while hopefully not breaking anything else).

---

### Post by kvelandia on 2008-08-26
I haven't had so much luck with WoW.
Everytime I log in it crashes, showing error 132.

When I run it in my Win (disgusting but...gotta play) it works perfectly. I would reaaaally love to solve this in order to get rid of WinXp once and for all.

PS: someon told me to try cedega...I am downloading it right now, but still interested in learning how to make it work with WINE

---

### Post by thumper13 on 2008-08-26
> **kvelandia said:**
> I haven't had so much luck with WoW.
Everytime I log in it crashes, showing error 132.

When I run it in my Win (disgusting but...gotta play) it works perfectly. I would reaaaally love to solve this in order to get rid of WinXp once and for all.

PS: someon told me to try cedega...I am downloading it right now, but still interested in learning how to make it work with WINE

WoW is an interesting beast in Ubuntu. There is 2 forum posts you could look for specifically, they are step by step installations, one by a fellow named Sammi, and the other is by Spydr and some numbers afterwards. As well, there is a page on WoWWiki about wow in linux. Unfortunately I don't have the pages bookmarked, so you'll have to find them. As far as I know, on an Nvidia video card, WoW works flawlessly, and of ATI, the only problem I have is my minimap turns white when I'm in a building. Nothing major. 

As far as your crashing when it loads up, did you add the Apply To Forehead addon? I'm pretty sure that would fix the issue.. Either that or using the config.wtf file that is advised to be used in the walkthrough...

Here's Sammi's walkthrough: [http://ubuntuforums.org/showthread.php?t=579378&highlight=World+Warcraft](http://ubuntuforums.org/showthread.php?t=579378&highlight=World+Warcraft)

and Here is the Spydr one I talked about: [http://ubuntuforums.org/showthread.php?t=654681&highlight=wow+ati](http://ubuntuforums.org/showthread.php?t=654681&highlight=wow+ati)

Regardless of whether or not you have an ATI, I'd download and install the two files on the bottom of the second thread, because it is a proper working config.wtf file, and the Apply To Forehead addon is there as well.

Hope this helps.

---

### Post by k1ngb0b0 on 2008-08-26
> **shae said:**
> You can try using wine from my repository (see link in my signature).  I apply the appropriate patches for it to work with Warcraft 3 (while hopefully not breaking anything else).


See the only thing is that Warcraft 3 works fine, it's just the alt tap and desktop change bug crashes it.

I'd hate to mess with wine and reinstall, it might end up ruining my WoW installation (and I'd be worse off than I am now).  If it would fix my problem though I'd do it.

---

### Post by atvar on 2008-08-27
Following the instructions, the WoW installer gives me this output:

```
 The folder "Z:\mnt\linux1\World of Warcraft\Cache.temp\WDB.temp" could not be created. (ConflictManager::CreateObjects)
```

Probably just a n00b mistake, but I've been looking for hours, and haven't found any solution. Permissions problem? :(

**EDIT:** Found the issue, and yes it was a n00b thing. First, it was a permissions issue. I edited the permissions of the area of the install, and even created a folder named "World of Warcraft" and gave it full-access to be sure. I got the same error, and continued my research for an hour or so. Gnawing away at the few remaining possibilities, I deleted the folder, then the installer ran fine. XD

So, a word of advice to those who follow; *Let the installer create the folder!*

---

