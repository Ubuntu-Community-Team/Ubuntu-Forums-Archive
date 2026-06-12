---
title: "VLC full screen behind top panel"
date: 2005-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by BoyOfDestiny on 2005-11-07
Hi, I'm using VLC .8.4 test1 from the breezy repo

 (rant: you know, the one they put in a little before breezy was released, the interfance looks off, the always on top in the menu doesn't work, and it doesn't play mkv's [.8.2 did]).

Anyone know why it doesn't go full screen properly... tvtime goes fullscreen fine... I think it was fine on my 32-bit ubuntu box (this might have been the stable release though... .8.2)

I think it's because of wxwindows instead of GTK...

Any tips/solutions?

---

### Post by EvanCarroll on 2006-07-22
1) Settings->Preferences

2) Check "Advanced Options" (bottom right)

[INDENT]a) Video->Output Module->Video Output Module = Xvideo extention video output

b) Xvideo->Alternate Fullscreen method[/INDENT]

Hope that helped, a few years late but this problem is often occuring even in Dapper.

---

### Post by Duccio on 2006-10-15
This has solved my problem 50%...

Fullscreen first looked this way:
[[IMG]http://img256.imageshack.us/img256/5863/screenshoton4.th.png[/IMG]](http://img256.imageshack.us/my.php?image=screenshoton4.png)

Now that I changed preferences like EvanCarroll suggested, VLC's fullscreen at first looks ok, but than if I come back to non-fullscreen and again to fullscreen, here's how it looks:
[[IMG]http://img265.imageshack.us/img265/3680/screenshot1qp4.th.png[/IMG]](http://img265.imageshack.us/my.php?image=screenshot1qp4.png)

You see, there's still the upper panel! Any hints?

---

### Post by Duccio on 2006-10-22
I forgot to say I'm under Dapper, AMD64, Desktop.

---

### Post by Disastorm on 2006-10-22
Im pretty sure therse no way to fix it in 0.8.4.  However, this problem is fixed in 0.8.5 from what I've heard.  Unfortunately, I could never figure out how to compile the damn thing.  I wish someone would put it in the dapper repos.  I believe it is in the edgy repos if you feel like upgrading to that.

---

### Post by Duccio on 2006-10-23
Thanks. Can't find a single word on [http://developers.videolan.org/vlc/NEWS]("http://developers.videolan.org/vlc/NEWS"), anyway I'll wait till it's in the dapper repositories.

---

### Post by deltaf on 2006-11-11
The problem still exists in Edgy. I'm using the 64-bit edition with VLC 0.8.6.

Any fixes out there?!

---

### Post by eNtoS on 2006-12-09
not really a fix but a workaround:

play your vid
enter fullscreen (bar is still there)
press "s" on your keyboard to stop playback
click the play button

vlc should now snap back into fullscreen, but without the gnome app bar

---

### Post by Disastorm on 2006-12-13
Thanks, thats good to know, but I wish they would fix this thing.

---

### Post by chojin on 2006-12-19
That doesn't work either (64bit, 0.8.6).

This is a really silly bug - totem goes fullscreen... gah...

---

### Post by SolaceDisparaged on 2007-01-13
anybody get a fix for this yet???
I'm having trouble with this as well...i've fiddled around with about as many options as VLC has, and i figured out the half-full screen, where it covers teh bottom bar but still not the top. the stop/play thing doesn't work for me.
Ubuntu Dapper, nvidiaglx, amd64

---

### Post by SolaceDisparaged on 2007-01-13
oh, cancel that last message...sort of.
I figured out the the stop/play technique of making it work, and it does work..but is there an ACTUAL fix available for this somewhere?
if anyone figures this out please let me know

---

### Post by bennybawlz on 2007-02-01
Just noting that I, too, experience this problem in VLC 0.8.6 on an AMD64 installation of Edgy Eft (Ubuntu 6.10).

---

### Post by henriquemaia on 2007-02-12
> **EvanCarroll said:**
> 1) Settings->Preferences

2) Check "Advanced Options" (bottom right)
[INDENT]a) Video->Output Module->Video Output Module = Xvideo extention video output

b) Xvideo->Alternate Fullscreen method[/INDENT]Hope that helped, a few years late but this problem is often occuring even in Dapper.

This fix still works. Thanks for posting it. :)

---

### Post by oqnet on 2007-02-13
I moved the gnome bar from the top of the screen and that fixed the problem as well.  As soon as you lock the gnome bar to the top of the monitor it shows up in full screen.  Unless you use the other work around.

---

### Post by hamil on 2007-04-26
> **henriquemaia said:**
> This fix still works. Thanks for posting it. :)

Yes it works, but I still have the annoying top line showing up ... Is there no way to get rid of the top-line also. This was not an issue with x86 .. Why is this happening??

---

### Post by viljamih on 2007-05-16
that toppanel showing over fullscreen has not affected me, because i view videos on other monitor (twinview 2x 1440x900), where arent any panels.. but there is another, maybe somehow connected problem.. it seems that vlc cant understand that full resolution.. there is always about 10% missing from bottom.. 16:9 videos shows just fine (then that 90pix border makes aspect ratio just right), but anything else would have black borders on 3 sides of picture.

and then, there is more.. i dont know is it gnome or what, but when changing videos to show fullscreen, this twinview setup prettymuch randomizes wich screen it will show.. it happens with totem and mplayer also.. it's little annoying to fiddle fullscreen and back several times before it will go to that monitor i want.

---

### Post by david_2001 on 2007-05-16
> **hamil said:**
> Yes it works, but I still have the annoying top line showing up ... Is there no way to get rid of the top-line also. This was not an issue with x86 .. Why is this happening??
Used to happen for me when I was running i686 as well.  Just closing and restarting vlc after selecting the alternate fullscreen method fixed the visible top panel problem then and now (and rumning compiz cures it completely - no need to select the alternative method!)

---

### Post by fakie_flip on 2007-06-06
> **EvanCarroll said:**
> 1) Settings->Preferences

2) Check "Advanced Options" (bottom right)

[INDENT]a) Video->Output Module->Video Output Module = Xvideo extention video output

b) Xvideo->Alternate Fullscreen method[/INDENT]

Hope that helped, a few years late but this problem is often occuring even in Dapper.

That worked in Feisty 64 bit version except that when I leave fullscreen and then go back to it again, it no longer works and the top panel is over the movie again. Also I have a green line going across the screen at the bottom portion of the movie that only shows in full screen mode with vlc. I am thinking of uninstalling vlc and just using totem-xine. It works fine without any problems. I tested the same movie in totem-xine to be sure that the green line wasn't a defect in the movie, and it wasn't.

---

### Post by ballison on 2007-06-12
I'm in 64bit Feisty Fawn, everything updated. 

First I followed EvanCarroll's advice, which fixes 50% of the problem, exactly like Duccio.

> **EvanCarroll said:**
> 1) Settings->Preferences

2) Check "Advanced Options" (bottom right)

[INDENT]a) Video->Output Module->Video Output Module = Xvideo extention video output

b) Xvideo->Alternate Fullscreen method[/INDENT]

Hope that helped, a few years late but this problem is often occuring even in Dapper.

then, 
when the video starts playing, I have to enter full screen mode as quick as damn possible, and that works.

If I enter too late, it won't work, and I'll be blighted by the top bar. Maybe this will help someone.

---

### Post by jmac19 on 2007-06-12
> **ballison said:**
> I'm in 64bit Feisty Fawn, everything updated. 

First I followed EvanCarroll's advice, which fixes 50% of the problem, exactly like Duccio.



then, 
when the video starts playing, I have to enter full screen mode as quick as damn possible, and that works.

If I enter too late, it won't work, and I'll be blighted by the top bar. Maybe this will help someone.
am havin the same problem as u this aint a fix but it works for me i belive the problem to be a metacity bug doesnt happen in E17 or when using a composite manager switch on desktop effects ur problem should be fixed

---

### Post by jw5801 on 2007-06-19
As an alternative to using the "alternate fullscreen method" (I've had vlc crash whilst fullscreen using the alternate method and not being able to switch to any other windows to fix it), you can leave the normal "fullscreen" (opens a new window with only a titlebar), and then use gnome to put this window to fullscreen (stops displaying the gnome-bar and the titlebar of the window, you can do it for any window). You can enable a global shortcut key to do it (otherwise alt+space will get you to the menu) and it eliminates the problem of the top bar returning.

EDIT: I apologize. I posted the above away from my linux box, so I thought the fullscreen option for the gnome window display was in the standard window menu. It actually isn't, so you'll need to open System > Preferences > Keyboard Shortcuts, and there will be an option for it under the "Window Management" section called "Toggle fullscreen mode."

---

### Post by crjackson on 2007-06-19
I hope you don't mind if I chime in with a VLC question.  I have this strange thing hapening and I just wanted to know if you guys observed the same.

When I play a DVD move of any kind, the edgeds are smooth and clean.  It other words it looks like it's supposed to.  If however I change to full screen or rezie the window the images show square/rectangular blockiness (for lack of a better descriptions).  NOTHING I do can bring it back to the proper look.  I've tride locking the aspect ratio, and selecting the exact 16:9 ect... as opposed to to "AUTO".  Nothing works except closing the player and starting it over again.

BTW this is NOT just VLC that does this.  Totem does the same thing to a lesser extent.  Is this a CODEC issue?  If so how would one attack this problem?

---

### Post by jw5801 on 2007-06-30
hmm... does it do it if you start the DVD in fullscreen mode? That could be a work-around if you wanted to watch the movie in fullscreen. Otherwise, I have no idea what could cause the problem though or how to fix it.

---

### Post by crjackson on 2007-06-30
> **jw5801 said:**
> hmm... does it do it if you start the DVD in fullscreen mode? That could be a work-around if you wanted to watch the movie in fullscreen. Otherwise, I have no idea what could cause the problem though or how to fix it.

Yeah, it does it regardless.  Also, I can't seem to get it to JUST PLAY a DVD.  I have to open each VOB file and play them one at a time.  Is there a setting for this?

---

### Post by jw5801 on 2007-06-30
Do you have the library you need to play mainstream encrypted DVD's?
```
sudo apt-get install libdvdcss2
```
That would explain why it wouldn't play... otherwise I have no idea. I've never seen the problem before.

---

### Post by crjackson on 2007-06-30
> **jw5801 said:**
> Do you have the library you need to play mainstream encrypted DVD's?
```
sudo apt-get install libdvdcss2
```
That would explain why it wouldn't play... otherwise I have no idea. I've never seen the problem before.

Yes - It occurs on ALL video not just css encrypted ones.  I do have the file already though.

---

### Post by jamo88 on 2007-07-27
hey thanks!
the toggle full screen mode worked! :)
i was freaking out watching those ...bars :P

---

### Post by jw5801 on 2007-07-27
No probs! I thought it was an innovative solution :p
By the way, this is apparently a bug in Metacity (the gnome window manager), as I'm now using compiz and not getting the error anymore. But compiz has all of it's own bugs. Hopefully this will all be fixed in gutsy!

---

### Post by etstar on 2007-08-17
Yeah... nothing I've done works other than putting it in auto fullscreen mode and then leaving it there until whatever i'm watching is over. if i leave fullscreen and re-enter the bar at the top is there... urrgh.

---

### Post by etstar on 2007-08-18
> **jw5801 said:**
> As an alternative to using the "alternate fullscreen method" (I've had vlc crash whilst fullscreen using the alternate method and not being able to switch to any other windows to fix it), you can leave the normal "fullscreen" (opens a new window with only a titlebar), and then use gnome to put this window to fullscreen (stops displaying the gnome-bar and the titlebar of the window, you can do it for any window). You can enable a global shortcut key to do it (otherwise alt+space will get you to the menu) and it eliminates the problem of the top bar returning.

EDIT: I apologize. I posted the above away from my linux box, so I thought the fullscreen option for the gnome window display was in the standard window menu. It actually isn't, so you'll need to open System > Preferences > Keyboard Shortcuts, and there will be an option for it under the "Window Management" section called "Toggle fullscreen mode."

perfect. thanks! i don't even mind the extra keystroke.

---

