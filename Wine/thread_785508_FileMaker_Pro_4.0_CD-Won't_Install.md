---
title: "FileMaker Pro 4.0 CD-Won't Install"
date: 2008-05-07
forum: Wine
---

### Post by lefo on 2008-05-07
Using 8.04, latest Wine, and a full copy of FileMaker Pro 4.0.  I've been trying to launch the installer in Wine, but I get permissions problems.  I'm told I'm not the Owner.  I'm trying to get this installed so I can install FMP 5.5 update from CD, which ironically, WILL launch and go through Wine for setup.  Problem is, it has to find a valid copy of FMP4 before it will do it's job.

Any suggestions?

TIA

lefo

---

### Post by Mr_B on 2008-05-07
Well, my install of FileMaker Pro 5.0v3 was without errors, but when I open my database script, a lot of the buttons don't work making it un-usable. In our custom database app built in FileMaker, the button that should bring up a list of vendors brings up a blank list. The next/previous date buttons do nothing. 
So even if you get it installed does not mean it works :-(
I need to get VMware working...

---

### Post by lefo on 2008-05-07
Thanks!  That helps a lot.  Still don't know why Wine won't run the installer from the CD, and even copying over files from CD to a folder on the desktop, nothing works.  I can't even copy/paste into the Wine-Windows directory.  I'm really-really new to all of this, and don't want to muck up my Permissions, but this has now turned into a mission for me.

Thanks again,

lefo

---

### Post by lefo on 2008-05-13
Okay, *some* success, but now I've got another problem.  I was able to install FMP 4.0 Complete Install using 'gksudo nautilus', and it DID install.  Then, I ran FMP 5.5 updater, and it too installed.  Here's the funny thing.  Apparently, when you get the root permissions to finally get this thing installed, you have to have root permissions to launch the app!  LOL  Well, what would be the best way to:

[LIST=1]
[*]Change the permissions so my user login can launch the program
[*]Add FMP to Wine's List of Program Apps. (It Didn't)
[*]And, finally...where's the best place to store the FMP files (and if it's outside the Wine Folder, how to circumnavigate the globe to get it into my Documents Folder in my Home folder?
[/LIST]

I'm so new to all this it hurts, but I'm bashing my way around.  BTW, I absolutely LOVE Ubuntu Hardy!  I gave up WinXP Pro SP2 because of all the antivirus junk slowing me down along with all the other junk that goes with it.  Other than having to tweak my Wacom Graphire Mouse and my ATI 9550 card by hand (and, thanks to previous posters for that help!), everything else I had connected to my Compaq desktop worked right out of the box!  Coolest OS I've ever used (and, I also used to be an Apple Power Rep)

TIA to anyone who can answer the above questions.

lefo

---

### Post by lefo on 2008-05-15
***Bump***

Any takers?

TIA

lefo

(PS: Figured out #3)

---

### Post by lefo on 2008-05-19
Okay...Success!  I'm able to create a launcher and put it in the Wine menu.  FMP 5.5 now launches (woo-hoo!).  I've been able to set up permissions in a folder in my User Documents folder, and I can save, edit and update files.

Whoo!  That was interesting.

lefo

---

### Post by NCFC on 2009-01-04
> **lefo said:**
> Okay...Success!  I'm able to create a launcher and put it in the Wine menu.  FMP 5.5 now launches (woo-hoo!).  I've been able to set up permissions in a folder in my User Documents folder, and I can save, edit and update files.

Whoo!  That was interesting.

lefo

That's great that you've fixed your problem but why don't you explain step by step just how you did it. I'm sure there are others that may have the same issue as yourself.  

That's supposed to be the purpose of using Linux, edit and return back to the community.

---

