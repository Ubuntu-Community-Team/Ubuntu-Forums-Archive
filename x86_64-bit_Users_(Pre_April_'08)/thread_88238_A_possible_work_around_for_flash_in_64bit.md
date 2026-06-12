---
title: "A possible work around for flash in 64bit?"
date: 2005-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by DRF on 2005-11-09
I was watching a streaming online version of a BBC program about technology (there was an article on opensource that interested me on it) one of the hot links mentioned was a browser called 'flock' based on the same engine as firefox I believe.

Just remembered today that I intended to download the browser so went to [http://www.flock.com/](http://www.flock.com/) (the site design isn't really my style personally) which talks about the added features of flock etc. (integrated blogging and shared links/bookmarks etc).

Clicked on the 'developer page' link ([http://www.flock.com/developer/](http://www.flock.com/developer/)) and downloaded the latest preview release for linux (not the source/daily snapshot). Extracted flock-1.4.10.en-US.linux-i686.tar.gz and ran the file called 'flock' though nautilus (didn't ask to install just ran from the location extracted to)

Now I wasn't expecting much as it's pre-beta and it does look very firefox clone like but not too bad. However I went to a website with flash and got the customary "Click here to install flash" banner at the top of the window and out of boredom decided to try it (not expecting it to work) but it said "found Macromedia Flash plugin, click here to install", and after it installed the plugin all of a sudden the flash page (which didn't I've never seen work properly with swf or gplflash) worked as I would expect!

Now I'm not sure how come it's working. If it's not really macromedia flash but an opensource clone or if it works as this browser is 32bit running I assume using the ia-32 libs in breezy and those in the extracted browser.

But would be interesting to see if this works on other peoples AMD64 breezy installations or if it's just something querky that I did to my setup without realising.

Daniel

---

### Post by grsing on 2005-11-09
Works for me, too.  Interesting.  Now why can't they do this for Firefox?

---

### Post by queenorych on 2005-11-09
i didn't look at it, but its probably just a 32bit browser.  firefox 32bit will work too.  You just need a chroot, or firefox comiled for 32bit

---

### Post by grsing on 2005-11-10
Is there any real advantage to using 64bit Firefox (besides an infintesimal speed boost, since it's really limited by bandwidth, at least in my case)?

---

### Post by RAOF on 2005-11-10
No.

---

### Post by Mordok on 2005-11-11
I'm running Breezy 64 and I think I have flash working with Firefox.  I have these 5 items installed.  I started with the first 4 items as suggested by someone on here but then Firefox started quitting on a site a couple days ago and so I added the 5th item and it hasn't quit since.

gstreamer0.8-swfdec
libflash0c2
libflash-mozplugin
libswfdec0.3
swf-player

Of course I haven't had to shutdown/reboot this thing since then, so who knows if it is a solid solution.  Most of these things are in the Universe repositories.

---

### Post by Mordok on 2005-11-11
I guess that might not be the complete winning combination.  Firefox has already quit on me once since the last post I made.  Not sure why and it may have nothing to do with the flash situation at all.

---

### Post by willalbro on 2005-11-12
Flock worked for me just as described in the first post.

---

### Post by Jestar on 2005-11-12
After trying to force install the i386 packages, I tried this and it worked perfectly.

---

### Post by Sykil on 2005-11-12
Woah, it worked!

Now then, why doesn't it in Fx... perhaps we should ask the Flock devs?

---

### Post by Navyblue on 2005-11-13
Hope that you don't mind me asking. How do I run Flock from console?

I am running Kubuntu Breezy for AMD 64 btw, and I don't know if it is possible to run it from Konqueror. So I open up a console in the directory that I ectracted the files to, I typed "./flock". And I get:

```
./flock-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```

I have "libgtk2.0-0" package installed. What am I missing here?

---

### Post by nrayever on 2005-11-14
nice!!! it works!! maybe a howto for installing it, because i'm excecuting it from console, heheheh:D :D :D

---

### Post by Navyblue on 2005-11-14
[QUOTE=nrayever]nice!!! it works!! maybe a howto for installing it, because i'm excecuting it from console, heheheh:D :D :D[/QUOTE]


How did you get it to execute from the console?

---

### Post by DRF on 2005-11-14
queenorych - I did think that considering the similarities that a 32bit firefox might work but didn't have time to check which other browsers will do the same as the pre-compiled flock browser. I know about chroot but it sounds personally like a bit to much work if all you want is flash occasionally. Where as just extracting and running a 32bit browser isn't too much trouble at all.

grsing - For web browsing I doubt you will notice much of a speed difference between 32 and 64bit browsers except there are more plugin's supported on the 32bit browsers. I still use firefox 64bit normally more out of habbit though.

Navyblue - I'm not quite sure why it doesn't work for you. (I'm at work so can't check my installed packages but I can do later sometime), my install is still fairly fresh since the breezy upgrade. The only major requirement is the GTK2 toolkit and it sounds like this might be something related to that, might be that the Kubuntu doesn't install a couple of the GTK files that ubuntu does. Personally I was able to do it without running it from the console, it worked fine when I ran the file called 'flock' from nautilus. (But running programs that way means you won't see any warnings that are produced by the program). Sorry couldn't be more helpful, will have to look it up when I get some spare time at home.

Daniel

---

### Post by bonzodog on 2005-11-14
hrm...the browser opens, but If I try to open preferences or favourites, it crashes out.

---

### Post by Navyblue on 2005-11-14
[QUOTE=DRF]Navyblue - I'm not quite sure why it doesn't work for you. (I'm at work so can't check my installed packages but I can do later sometime), my install is still fairly fresh since the breezy upgrade. The only major requirement is the GTK2 toolkit and it sounds like this might be something related to that, might be that the Kubuntu doesn't install a couple of the GTK files that ubuntu does. Personally I was able to do it without running it from the console, it worked fine when I ran the file called 'flock' from nautilus. (But running programs that way means you won't see any warnings that are produced by the program). Sorry couldn't be more helpful, will have to look it up when I get some spare time at home.[/QUOTE]

Thanks for the reply and effort to help. My Kubuntu is fairly fresh as well (just reinstalled from scratch a couple fo days ago because of some problem that I can't solve). Apparently, it is as you said that some things are missing, but at the same time I am also suspecting there are some errors in the library linking (assuming such if linking is needed).

It probably isn't related, but just in case it does. This system apparently has some problem about its library, some GTK applications have some complaint about missing locale and interface appear gnomish despite having the respective packages installed. (which is also the reason that I reinstalled everything recently)

---

### Post by nrayever on 2005-11-14
[QUOTE=Navyblue]How did you get it to execute from the console?[/QUOTE]

in the directory where flock was uncompressed you should write: ```
./flock
``` and then hit return, that's all!!

---

### Post by Navyblue on 2005-11-14
[QUOTE=nrayever]in the directory where flock was uncompressed you should write: ```
./flock
``` and then hit return, that's all!![/QUOTE]

Oops, sorry for not being more clear, I meant what is needed to get it to run. I get this message at "./flock":

```
./flock-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```

And I have "libgtk2.0-0" package installed.

---

### Post by Navyblue on 2005-11-14
I have managed to run Flock! Though with lots of error message in console, but it runs, and scrolls much faster than Firefox.

For those who are interested, what I am missing is the "ia32-libs-gtk" package. I am not sure if this is installed in Kubuntu by default (but it doesn't seems to be). Installing this package also made openoffice2 uses KDE theme.

Then I installed the 32 bit Flash plug-in, and Flash site played nicely, and, with sound. Way easier than chrooting if your intention is just to occasionally visit flash site. Now, for my use, 64 bit K/Uubuntu is virtually as good as its 32 bit brethern. :)

Btw, I can't fire up the preference window too. If anyone how to get it to work please let us know here. If not possible, which file is storing these config? I probably want to sym-link it to my Firefox config file (if it will work).

---

### Post by RAOF on 2005-11-14
For all your flash needs, there is now a [howto]("http://www.ubuntuforums.org/showthread.php?p=491079#post491079") to get 32bit firefox + flash working.

---

### Post by Bender NZ on 2005-11-15
Works nicely for me.

Would be even better to have a .deb available, I might have a go at packaging after my exams.

Edit: If you actually like Flock over Firefox, you can follow the howto in the post above, but substitute the firefox path for the flock path and it will get the browser to stay stable instead of crashing when you open preferences.

---

### Post by joris.brus on 2005-11-15
Can't tell you how happy I am.. sound and everything works.
Now I can use [http://www.pandora.com](http://www.pandora.com) 

Thank you for posting this.

ps. It crashes for me too when I try to edit preferences
don't care right now though

---

