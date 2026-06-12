---
title: "A brief explanation of Wine and my Wine packages"
date: 2005-11-17
forum: Wine
---

### Post by YokoZar on 2005-11-17
**What is Wine?**

Wine is a free, open source reimplementation of the Windows API.  In short, it lets you run Windows programs under Linux.  Wine isn't finished yet, so not every application works, however most of the important ones do.  For more information, see the Wine User's Guide that I helped write: [http://winehq.org/site/docs/wineusr-guide/index](http://winehq.org/site/docs/wineusr-guide/index)

**What is Cedega/WineX**

Several years ago, a company called Transgaming took the Wine code and turned it into a product called WineX, which was eventually renamed Cedega.  This was a commercial fork of Wine aimed at users running games.  After Transgaming did this, the Wine developers didn't like the fact that they didn't contribute any code back to the Wine project, so they changed the license to the LGPL.  The two programs are now different pieces of software, albeit with similar goals - Cedega is *not* an "improvement" on Wine, as none of the Wine code that has been written in the past few years is in Cedega.  Many applications, including quite a few games, work in Wine and *don't* work in Cedega.

Transgaming has done some development on their own to get Cedega to work with games and be easier to use, however without access to Wine's main codebase they've been unable to use the vast amount of work done on Wine in the past few years.  Now it looks like Cedega has finally reached the point where Transgaming's begun to fall behind even in the area they've been developing on their own - support for games.  

**I want to know if this application works under Wine**

The very first thing you should do is check the Application's Database: [http://appdb.winehq.org/](http://appdb.winehq.org/) - be aware, however, that some of the less popular entries haven't been updated for a while, so the information may be out of date and your application may work even if the last person to post there said it didn't.  We rely on users to keep the AppDB functioning, so if you figure out how to make an application work please post your results there (or, better yet, become a maintainer for the application).  You can even post testing results.

If you run into problems, post a message in the AppDB first before turning to this forum - your problem may not be Ubuntu specific, and there may be a general solution out there.  Alternative places to seek help are the #winehq IRC channel on freenode and the wine-users mailing list.

**What are these xwine and winesetuptk packages?**

These are extremely ancient packages that were accidentally left in the universe repository at release time.  Contrary to what the package descriptions say, they do not help configure Wine - in fact, they confuse and break things.  Don't install them, and don't run them.

**What Wine packages should I use?**

Because the Ubuntu repositories are frozen at release, the Wine package in universe is a bit old.  We had a major update after Breezy was released, so a newer Wine version is your best bet.  I will be working on putting up to date Wine packages into Dapper, which will then find their way into Breezy Backports, however until then you can use the WineHQ apt repository.  Follow the instructions here: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) - all you need is the binary package *wine*, so the instructions at the top of the page should be enough.

---

### Post by YokoZar on 2005-11-17
**How come DirectX games don't work?**

DirectX games *do* work in Wine - unlike Cedega, Wine natively implements DirectX9 rather fully, so games like Half Life 2 can run without having to be in DirectX7 mode.  The way Wine does this is to translate DirectX instructions into OpenGL, so if OpenGL is broken on your system Wine's DirectX will be as well.

The most common reason for OpenGL not working is that you haven't yet enabled the restricted Nvidia or ATI drivers.  Once you install the nvidia driver (ie, the package nvidia-glx), you must enable it by opening a terminal and typing "sudo nvidia-glx-config enable".

A good way to test whether or not OpenGL is working on your system is to try an OpenGL screensaver by going to system->preferences->screensaver.  Try a screensaver such as GLKnots and click preview.  If you get a blank screen or "preview not available", then OpenGL is not yet working and you need to enable it.

---

### Post by the_it on 2005-11-17
thanks.  very helpful.

I installed xwine on my system because I thought it would be useful.  Now I know it's better just to use the wine from cvs.

I only just learned recently that wine is about to overtake cedega in compatibility.  w00t for free software!

---

### Post by TaTaE on 2008-03-30
I really think this post should be sticky in the GAMES & LEISURE section.

---

### Post by Perfect Storm on 2008-03-30
[img]http://www.imageviper.com/displayimage/116046/0/necromancing.jpg[/img]

Please check our wine forum.

---

