---
title: "iMac Post-install Sluggishness"
date: 2006-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Frank65 on 2006-03-28
Tried to install Ubuntu Sunday night, and there is a problem.

First the givens:  iMac G3, 700 MHz, 512 RAM, 80GB HD, Mac OS X 10.2.8.

What I did:

Backed up the whole Mac HD to an external Firewire drive.

Using OS X Install disk, repartitioned the Mac HD in half; one for Mac OS, one for Ubuntu. Repartitioned the Ubuntu half as free space.

Restored Mac OS to Mac HD. Checked to make sure all was good.

Booted Mac with Ubuntu 5.10 Install disk.

Selected "install-powerpc" from yaboot.

Followed all the steps - I let the install disk find the free space for Ubuntu.

Upon reboot, I got the dark "Ubuntu screen" with the thermometer where all the stuff gets loaded.  Then there's  a 2/3 gray bottom, 1/3 top black screen for about 20 seconds. A patter of bongo drum and the nice login screen. 

I enter name and password. 30 seconds later the startup tones. The cursor disappears, reappears and freezes. Move the mouse and the cursor moves to that spot about 10 seconds later. After a minute or so, Some little graphic "frames" show up on the login screen and black-background text bar overwritten the word "Password". Screen goes to dark brown sunset wallpaper and waits. After about a minute a tiny graphic appears in the lower left. After 3 more minutes there are menus and icons on the top bar, brown and gray squares in lower right. Cursor still frozen.

After 5 more minutes, cursor is free and tracks normally. Upon clicking an icon, it activates but the cursor disappears or freezes again. Then I shut the machine down and use my other iMac to post on this forum.

I have checked for the date bug and the results _do_ show the correct date and time.

Man, I was soooo close!  

Any help is greatly appreciated.

Frank65

---

### Post by linear on 2006-03-28
You need to disable **dri** in xorg.conf - just as you had to do for the Live CD (if I recall correctly). But at least after an install you only need to do it once.

---

### Post by Frank65 on 2006-03-28
DOH!! How could I have overlooked that???

Made the change and now all is right with the world. Once again, *linear*, thanks for bailing me out.

Now, should I install all 75 of the Available updates or should I use just a selection?

Thanks.

Frank65

---

### Post by jdp on 2006-03-28
The only reason I see for not doing them all is bandwidth: dial-up vs. cable/dsl.  There have been a few problems people have had with kernel updates, but htose seem fairly uncommon.

---

### Post by engla on 2006-03-28
[QUOTE=Frank65]Now, should I install all 75 of the Available updates or should I use just a selection?

Thanks.

Frank65[/QUOTE]
They should all be security and bug fixes, very few feature updates. If you are going to enable remote login or a webserver you should absolutely get them all, in other cases it's as above a question of bandwidth.

---

