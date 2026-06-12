---
title: "Weird graphic error with World of Warcraft"
date: 2012-06-21
forum: Wine
---

### Post by Kiraush on 2012-06-21
So I started using my laptop a bit more (My machine with Ubuntu on it) and so I've been learning my way around. So I decided to play World of Warcraft again, I read through a few forums and found out it was easiest just to install it on a Windows Computer and transfer it over, so that's what I did.
But when I log in at a certain altitude and everywhere below that point it looks like I'm sitting inside a tree, I just reinstalled Ubuntu and reupdated with the Software Center so all that so my drivers should be up to date. Any ideas?

By the way, it's not just that little area, it spreads as I walk.

[IMG]http://i.imgur.com/j0ou5.jpg[/IMG]
[IMG]http://i.imgur.com/v6rdA.jpg[/IMG]
[IMG]http://i.imgur.com/H46RX.jpg[/IMG]
[IMG]http://i.imgur.com/95Mvv.jpg[/IMG]

---

### Post by Slimmons on 2012-06-21
I'm not saying it's not a problem related to Ubuntu, but my computer that I just got rid of with an old ATI graphics card started doing that exact same thing when it was getting older.  The fan had died, and it was overheating.  It's not what they normally do before they die, but that's what happened to mine.  Any information on how old the computer is, or what kind of card/motherboard?

Also, I just noticed you had the green circle at the upper right hand corner.  I'm not sure how long you've been playing wow, but that means that you have patches that aren't essential to gameplay downloading.  There are HUNDREDS of errors associated with playing during those patches.  Sometimes when I log in before they are done, i get all sorts of cool graphical errors, but generally they go away once the patches/updates are complete.  Once again, I'm not saying it's not a Ubuntu problem, but there are definitely other variables here.

---

### Post by Kiraush on 2012-06-22
Fixed it!
This is what did it:
> 
**Enabling OpenGL**

 The Windows version of World of Warcraft supports 3D rendering using either Direct3D or OpenGL. However,  in Wine the Direct3D mode is supported only through an emulation layer  that runs on top of OpenGL. Therefor it's highly recommended that you  enable the OpenGL mode directly, instead of using it indirectly through  Direct3D. 
Find the file wtf/Config.wtf in your main WoW directory. By default it is found in /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/, where <username> is you computer login name.  
Open config.wtf using a text editor and add or change the following line: 
SET gxApi "opengl"

---

### Post by Dlambert on 2012-06-22
Please mark this thread as solved! ):P

---

