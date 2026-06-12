---
title: "gutsy ati x1950"
date: 2007-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by xieu90 on 2007-10-22
hi everyone 
I have a little cute ati his x1950 256 mb  pci express vi card
some days ago I installed gutsy and installed its driver through envy

with a bunch of animation in compiz fushion my computer ran unstable  (slow, freeze)
and finally today I heard a bunch of sound from my hardware (don't know from where)
it sounded like my computer restart or something was burn down  (didn't check it yet)
but xp still run, ubuntu too

then I restarted my computer by reset button
first I get ubuntu is running in slow graphic mode 
I did something configuration, nothing
then i went into ubuntu, and used envy
then restarted
and now I get a total black screen (after beautiful booting screen)

so I blindly typed my username + password + blindly open a movie inside my computer 
so I heard login sound, the sound of the song, so my ubuntu is still alive
but its master is blind now
what should I do now ?
at least I need to go into ubuntu again, to copy my files from there to xp then reinstall that baby 

and how should I install ati driver in gutsy ?
in feisty I used this way and it worked well for me
[http://ubuntuforums.org/showthread.php?t=516033&page=5](http://ubuntuforums.org/showthread.php?t=516033&page=5)

but in gutsy something is wrong, though I managed to install ati driver but somehow I feel something is wrong with this driver here
(no idea)
[http://ubuntuforums.org/showthread.php?t=576356&page=3](http://ubuntuforums.org/showthread.php?t=576356&page=3)

---

### Post by xieu90 on 2007-10-23
no one ?

---

### Post by SKiFF on 2007-10-23
same problem with x1950, waiting for an answer

---

### Post by mstrzerg on 2007-10-23
I had a similar problem with the same card when I installed xgl.  I was able to get into the desktop and uninstall it and go back to the ati restricted drivers. Eventually I had to scrap the entire project and start over.

---

### Post by xieu90 on 2007-10-23
....
I think I managed to uninstall xgl
with this code
sudo apt-get --purge remove xserver-xgl  in recovery mode
and this code
sudo apt-get --purge remove fglrx

but it couldn't find this package

I think ubuntu somehow uninstalled the video card, that is why it can't show me anything when I log in

so how can I install a new video driver for it ? (the worst one is enough, I don't need the flashy one for x1950 for now)

---

### Post by SKiFF on 2007-10-23
FFS I spent last 20 hrs trying to make this work, have they not tested ANY ATIs when releasing this...its like IM having a dejavu about how retarded and raw vista is ...

---

### Post by utUtu on 2007-10-23
> **xieu90 said:**
> ....
I think I managed to uninstall xgl
.....
so how can I install a new video driver for it ? (the worst one is enough, I don't need the flashy one for x1950 for now)

```

sudo apt-get install xserver-xorg-video-ati

Then edit your xorg.conf driver to "ati'  .  Look for the line that says "flgrx"?

```

:popcorn:

---

### Post by ACLerok on 2007-10-23
When I dist-upgraded from 7.04 to 7.10, I received the same problem.  Here's what I did.

First, rename (keep a backup) your /etc/X11/xorg.conf and then try and do "aticonfig --initial" followed by "aticonfig --overlay-type=Xv" typed into a terminal.  That should get your xorg.conf back to square one.  

If that doesn't work, disable your restricted drivers, and follow one of the guides to install fglrx 8.40.1.  

After I upgraded to 8.40.1 following the wiki.cchtml.com guide, I was able to get X working, and so far Compiz-fusion has been stable for me, whereas in 7.04 it would crash almost immediately.

---

### Post by xieu90 on 2007-10-23
now I will try the two guide above

I have just come back from recovery mode
I found out that my xorg.conf has disappeared along with x11 folder

when I type fglrxinfo I got this
error: unable to open display :0
I tried this code
sudo apt-get install fglrx
but there wasn't any package like that (don't even remember its name , I did that in synastic or sy something hehehe)

my goal now is to get the bookmark from firefox could anyone tell me how to get it from terminal (recovery mode)
how to export it to html into my xp ?
after getting that damn important little thing I will kill ubuntu once again

this 7.10 is a tough guy !

---

### Post by ACLerok on 2007-10-23
> **xieu90 said:**
> now I will try the two guide above

I have just come back from recovery mode
I found out that my xorg.conf has disappeared along with x11 folder

when I type fglrxinfo I got this
error: unable to open display :0
I tried this code
sudo apt-get install fglrx
but there wasn't any package like that (don't even remember its name , I did that in synastic or sy something hehehe)

my goal now is to get the bookmark from firefox could anyone tell me how to get it from terminal (recovery mode)
how to export it to html into my xp ?
after getting that damn important little thing I will kill ubuntu once again

this 7.10 is a tough guy !

The reason that you're getting the error: unable to open display :0 message may be because you're in recovery mode and fglrx.ko isn't loaded into the kernel.  It also may be because you don't have any fglrx drivers installed at all...

try doing a "locate xorg.conf" to see where your xorg.conf is.  I have a hard time believing that it just disappeared!

---

### Post by xieu90 on 2007-10-23
I'm full now, a great sumo !!!
after cleaning dishes I will try to locate xorg.conf

before I get back could you tell me how to install fglrx driver in recovery mode ?
mama, I'm pregnant now !!!

---

### Post by ACLerok on 2007-10-23
I wasn't able to install fglrx in recovery mode, but I was able to fix my xorg.conf using the vesa driver so that I could at least start X in 640x480.  From there I was able to disable the restricted drivers, download the 8.40.1 drivers from ATI's website, and use wiki.cchtml.com to install 8.40.1.

---

### Post by xieu90 on 2007-10-23
hi
so it didn't disappear
I just "mistyped" x11 with X11
hehehe
so you were right
I tried everything you told me but ....


except this
If that doesn't work, disable your restricted drivers, and follow one of the guides to install fglrx 8.40.1.

After I upgraded to 8.40.1 following the wiki.cchtml.com guide, I was able to get X working, and so far Compiz-fusion has been stable for me, whereas in 7.04 it would crash almost immediately.




how can I disable it ?
yeah and I found a way to do it in ubuntu now Ctrl Alt F1 
and when I press Ctrl Alt F7 it comes back to graphic mode (i think) but I hear the sound of ubuntu far far away with blind eyes (not blue eyes like Elton John !)

so what should I do now ?
should I do something with xorg.conf ? 
(yeah copy it and post it here would be ... I will try to copy it to xp, if you really really need it (but give me the copy code, is it cp or something ?))


yeah I forgot to mention
that in Ctrl Alt F1 I typed fglrxinfo
and I got this
Xlib: connection to ":0.0" refused by server 
Xlib: Invalid MIT-MAGIC-COOKIE -1 key
error: unable to open display :0


if I have to "repair" xorg.conf then which command do I have to use ? I think gedit won't work, I think I saw nano , I tried it but then I got lost there

---

### Post by ACLerok on 2007-10-23
In order to disable the old (8.37.9) drivers that come with Gutsy, you have to go in either Preferences or Administration from the menu, and find the "Restricted Drivers" menu item.  Make sure that it's unchecked for the ATI Drivers.  I wish that I could post some screenshots for you, but I'm doing this from work...

So you've got Compiz-fusion running then?  I'm a little confused.  In order to enable/disable Compiz, you should find the "Appearance" menu item in the Preferences or Administration sections.  There will be a tab for you to choose the amount of Desktop Effects you want.

---

### Post by xieu90 on 2007-10-23
I think compiz is still on my computer
actually my gutsy with 8.40 ati driver is still alive
but after booting at welcome screen where I have to type my username and password to log in at that point my monitor is totally black, so I can log in but I can not see anything
that is why I have to press Ctrl Alt F1 or use recovery mode
so there is no GUI now

it doesn't even tell me ubuntu is running in low graphic mode
even you give me screenshots I won't be able to do anything there, cause I won't be able to know where to point my mouse to
except if I use keyboard

so if I login (blindly) then I press Alt F1 then go right 2 times then I'm there then I have to go up x times
press enter then some tab or shift tab then space then maybe enter

(I don't know how to restart !!!!)

I think I will have to sleep now
then tomorrow go to damn university then come back and continue fighting
I wonder what actually happened back then, I heard some voice then I  restarted the computer by reset button then the all horror starts now I have to hug this stupid xp x64
mama !!!

---

### Post by Yellow Pasque on 2007-10-31
any updates on this?

---

### Post by Bjecas on 2007-10-31
Not that I'm into the subject, but if you get to a graphical login prompt, I'm guessing this isn't really a gfx driver problem... I'd say it's something you turned on that's causing it.

This might sound dumb, but have you tried logging in with the root user into Gnome/KDE? 

If all you want is to save your firefox bookmarks, then backup the profile folder ( ~/.mozilla/firefox/*.default ) into your windows partition, or a pen drive, or a floppy, or something. Once in windows, configure your firefox to use that profile folder - I did this once but I don't remember exactly how it's done, check the Firefox docs!

Hope it helps! 

[SIZE="1"]
"*Computers let you make more mistakes faster than any other human invention, with the possible exceptions of handguns and tequila.*" Mitch Ratcliffe(?)[/SIZE] :)

---

