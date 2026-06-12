---
title: "Eclipse C/C++ CDT Europa freezes up"
date: 2007-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by chimera007 on 2007-12-25
Thank you for reading this post, and sorry about the extremely generic post name. 

Lets jump to the problem. I have eclipse cdt europa release 3.3.1.1 which freezes every time I open a file in a project. 

I have deducted that the problem of the situation is moving the computer out of my LAN. Eclipse works like it should when I am plugged into my homes LAN. Reason is that I have eclipse on a nfs mount, and i run it off that mount. 

When I left that LAN, i copied the eclipse folder into the HDD of the computer and that's when the problems arise. Forgot to mention, i also copied the workspace folder. When I load Eclipse, it asks for the workspace, like it usually does when it doesn't find the default one. When I load up Eclipse, it remembers the open files that i was previously working on, this is all great, but when i try closing or switching files on the tab area ( in my case "anr.h" to "main.h" ), it freezes.

This happen to me before, but when I went back home and plugged LAN and did the usual it all worked as it should have.

For those that have been lost into my words of complaint, here's a simple way to understand:

--At Home with the LAN: I run eclipse off an nfs mount (/media/data2/Eclipse). It works blazing fast.
--Leave home, say to go to university: I make a copy of both eclipse and the workspace. When i run eclipse i specify the workspace folder, and it remembers everything ( opened files, and projects ), but if i close/open a new file from the project it freezes for 1-2 minutes.

I have the nfs mounts on fstab in automount mode, but i disabled it to see if that had anything to do with the problem. 

So if anyone has had this or could guess from the description I made, please help.

I know it has vaguely something to do with being in LAN with the nfs fileserver and having the mounts.

EDIT:   Forgot to mention that editing the files, compiling and any other thing you can think up of, works. Again, the only thing that doesn't is opening a file in a project, or switching from opened files ( freezes )

---

### Post by zegenie on 2007-12-30
I'm having the same problems with my Eclipse installation. As soon as I switch from my wired connection to my wireless connection, Eclipse freezes "randomly". 

That is - "randomly" is as soon as I try to open a file. If I disable wireless networking, I can use eclipse as usual, but that's really not an option, as I need to be online, only with wireless instead of wired networking. It's really unusable as it is, but I'm not able to use eclipse at all when I'm connected via wireless. As soon as I hook it back onto the/any wired connection it works fine...

---

