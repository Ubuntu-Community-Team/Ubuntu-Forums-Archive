---
title: "[SOLVED] Japanese Shump Help (Touhou)"
date: 2007-03-17
forum: Wine
---

### Post by thenulldevice on 2007-03-17
I've been trying to get the Touhou Project series [http://www.shrinemaiden.com/MKAbout.htm]("http://www.shrinemaiden.com/MKAbout.htm") to work under Ubuntu with Wine.

I installed the games on a Windows box and then copied the directory over to Ubuntu.  The game itself loads, but the graphics are scrambled and the game itself is unplayable.

I was wondering if anyone has had luck with these particular games working under Wine.

---

### Post by hikaricore on 2007-03-17
I'm not sure if this is what you're looking for but if it is, there may be one working game in the series (didn't extensively check just saw a screenshot):

[http://appdb.winehq.org/search.php?sSearchQuery=Touhou](http://appdb.winehq.org/search.php?sSearchQuery=Touhou)

Sorry if it's the wrong game, but this is all I could find.

---

### Post by thenulldevice on 2007-03-17
That answers my question.  It seems as if it's not possible.  Quoting the section 'What Does Not Work' is says "The textures get messed up after starting the actual game, and makes it unplayable."  

It also got a "Garbage" rating under playability.  Looks like I'm going to need to install a Windows partition :mad: 

Thanks for the link, though!

---

### Post by hikaricore on 2007-03-17
Not a problem, one thing you may want to consider tho, if this software doesn't have a huge video card dependancy
(aka if it's 2d and NOT 3d) you may be able to run it in a virtual machine such as vmware.  With a virtual machine you
can setup a virtual computer right on your ubuntu/linux desktop and install any operating system you want on it.

In this case windows [insert version here].

This works great for 2d games which have small issues in wine, word processing software, graphic design
(photoshop), ect.  Sadly if it does use 3d vmware (or any other virtual machine) will fail you as well.

There is new support for 3d rendering in some versions of vmware, but this isn't anywhere near stable or fast.

Here's some overview info and a howto on vmware: [http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)
And of course I stole a screenie from the above post: [http://www.ubuntuforums.org/attachment.php?attachmentid=10151&d=1148757312](http://www.ubuntuforums.org/attachment.php?attachmentid=10151&d=1148757312)

---

### Post by dugan on 2007-03-18
I just found this by googing for "touhou" and "cedega".
[http://pooshlmer.com/touhouwiki/index.php/Running_in_Linux](http://pooshlmer.com/touhouwiki/index.php/Running_in_Linux)

---

### Post by thenulldevice on 2007-03-21
These games don't seem to work in a virtual environment, be it VirtualBox or VMWare.  That link to the Touhou Wiki looks like it might do it....but it looks like it might be a tad over my head.  If I have any progress I'll update.  Thanks for the help guys!

---

### Post by Syock on 2007-09-15
Latest version of Wine (0.9.45) manages to make it work! Hurrah for all Linux-using Touhou fans!

Can't play it fullscreen though. Things somehow glitch here and there. I managed to finish the first run till the ending, but then the ending doesn't display correctly. After that the screen freezes at the end of the credit although the game is still running.

---

### Post by moomoo5000 on 2008-03-24
does anyone know how to get touhou games to work on mac? (OSX 10.5)
someone has done it [http://blog.seiha.org/?p=295](http://blog.seiha.org/?p=295) something to do with extracting...
been dying to play it and i might have to resort to playing it in school if i can't get it to work on my mac > . >
thanks

---

### Post by ChronicMetamorphosis on 2010-11-30
What would be really cool, is that if the Touhou fans of the community came up with a way to configure every game perfectly and release it as its own operating system. Call it TouhouOS.

---

