---
title: "build firefox 1.5 beta in linuxppc?"
date: 2005-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by guoweiok on 2005-11-05
anyone here has built firefox 1.5 beta himself?
just can not pass the xft step, i have tried freetype2 instead, still no luck!

---

### Post by monway on 2005-11-06
[QUOTE=guoweiok]anyone here has built firefox 1.5 beta himself?
just can not pass the xft step, i have tried freetype2 instead, still no luck![/QUOTE]
I'll be looking into that area. I'm going to be building a bunch of stuff for backports-ppc. I'm probably the only guy right now that's going to be doing it. I'm not sure. But regardless I'll be doing what's available to me. I'll try getting 1.5 firefox working. If I do I'll post a how-to or simply wait for the backports and see if I include it there. Either way I'll inform everyone if there's a 1.5 available for ppc. cheers.:D

---

### Post by farruinn on 2005-11-06
That's good news.  Where are you backporting from? Dapper? Debian? Upstream?  If I can get my hands on a G4 tower (which might be possible) I'd be willing to help.

---

### Post by guoweiok on 2005-11-07
this is good! thanks, monway!
btw, is it possible to give some clue on how to build firefox now?

---

### Post by ssam on 2005-11-07
i had a go trying to build firefox 1.5 on powerpc a few weeks ago but did not get very far. its such a strange build process that i could have a made a mistake somewhere.

if you need testing help let me know

sam

---

### Post by monway on 2005-11-09
[quote=farruinn]That's good news. Where are you backporting from? Dapper? Debian? Upstream? If I can get my hands on a G4 tower (which might be possible) I'd be willing to help.[/quote]
sorry for replying to this post so late. I'm so busy with checking things out with dapper. I'm currently testing and building things with dapper. If I get enough support and interest in the things that are built for ppc it will probably be passed onto release in time if not backports. There's no backports available yet as far as I know but I'll post anything that is working and probably sticky a list of things that work and compiled. I'll also probably host some files on my .mac if people are desperate but again I am not the official backport person or hosting any backport at this time. If you have a request send me a private message and I'll see about what i can do for you or what kind of software to build. Thanks again guys do help out the ppc folks. If anyone can help please do .. at least contact me first before going in and wasting time trying to find answers. I'll do my best to please. Cheers all.

---

### Post by monway on 2005-11-09
[quote=ssam]i had a go trying to build firefox 1.5 on powerpc a few weeks ago but did not get very far. its such a strange build process that i could have a made a mistake somewhere.

if you need testing help let me know

sam[/quote]

great I'll post news when i can , whenever I can hopefully soon i'll have things going. right now i'm pretty much the only mac guy who's willing with balls to build. If you have any solutions submit them to the ppc areas of this forum or private message me if you need help, i'll try my best. The best way to contact me is private message.. finding all my posts is a pain in the ass. 
and thanks for your support. cheers.

---

### Post by monway on 2005-11-09
[quote=guoweiok]this is good! thanks, monway!
btw, is it possible to give some clue on how to build firefox now?[/quote]
Let me share with you how i do things which might help you. I know this is corny and ironic way to express this but everything you need to know is in the docs of source files or on the website where you obtain the sources from. Firefox like mozilla browser itself has a make file generator on site. It's not for the faint of heart or inexperienced but also not impossible. I just read whatever i can get my hands on and ask questions as I go with people and contribute. That's how I got to be where I am today. I was once someone like you who's curious..
Don't give up .. join us. That's what Ubuntu is all about and more. good luck! :)

if you need some help you can always private message me and i'll do my best to help you. take care.
-Monway

---

### Post by ssam on 2005-11-12
has anyone got a firefox 1.5 build to work on powerpc ubuntu?

there is a bug report [https://bugzilla.mozilla.org/show_bug.cgi?id=301936](https://bugzilla.mozilla.org/show_bug.cgi?id=301936) which points to a gcc bug [http://gcc.gnu.org/bugzilla/show_bug.cgi?id=20297](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=20297)

---

### Post by ssam on 2005-11-13
it builds fine under ubuntu x86

---

### Post by khc on 2005-11-13
I've been building firefox ppc for my own use for more than a month now. Unfortunately [https://bugzilla.mozilla.org/show_bug.cgi?id=313386](https://bugzilla.mozilla.org/show_bug.cgi?id=313386) seems to be showing up, but (combining with session saver) isn't severe enough to affect me most of the time.

If anyone want to host the file (it's a tarball), let me know.

---

### Post by ssam on 2005-11-13
i could probably host it. would you be able to email it?

i'd really like to be able to build it though. could you post your .mozconfig and any other clues to how your doing it. which gcc are you running?

---

### Post by guoweiok on 2005-11-13
yes, please share your .mozconfig.

---

### Post by khc on 2005-11-15
I don't think I want to email a 8MB file :-) Do you have a FTP site or something?

mozconfig attached. You probably want to change the build path and path to gcc.

---

### Post by ssam on 2005-11-15
khc

i have sent you a ftp server, user, and pass via private message. let me know if that works.

i'll try and sort a way that people can download it.

ssam

update.

i am ready to go live as soon as i get the file.

---

### Post by ssam on 2005-11-15
hmm i am having a go with you .mozconfig. it seems to be going strong. i think the gcc-3.3 might be the trick

i put 

```

CC=/usr/bin/gcc-3.3
CXX=/usr/bin/g++-3.3

```

and installed gcc-3.3 and g++3.3 in synaptic. i am still willing to host the build though. should the official branding be diabled if we're going to share it?

---

### Post by ssam on 2005-11-15
the first attempt failed with errors about ld (linking i think). so i stripped out most of the mozconfig 

```

. $topsrcdir/browser/config/mozconfig

mk_add_options MOZ_OBJDIR=firefox-build

CC=/usr/bin/gcc-3.3
CXX=/usr/bin/g++-3.3

```


I am now posting using my shiney new firefox 1.5 build :-)

thanks

---

### Post by khc on 2005-11-15
Cool, do you still want my build? Also, do you experience:

[https://bugzilla.mozilla.org/show_bug.cgi?id=313386](https://bugzilla.mozilla.org/show_bug.cgi?id=313386)

---

### Post by khc on 2005-11-15
Also, according to one ubuntu bug report, -fno-strict-aliasing is needed to prevent some bug on mozilla-related products.

---

### Post by ssam on 2005-11-17
i cant replicate that bug on my system, i opened 30 tabs (though most of them where empty) and draged them around lots, also dragged a file to nautilus, and go a save as dialog. sorry

i think i might put my own build up on the website if people are still interested.

---

### Post by pvz on 2005-11-17
[QUOTE=ssam]
i think i might put my own build up on the website if people are still interested.[/QUOTE]

I would be very interested.. thanks.

---

### Post by khc on 2005-11-19
[QUOTE=ssam]i cant replicate that bug on my system, i opened 30 tabs (though most of them where empty) and draged them around lots, also dragged a file to nautilus, and go a save as dialog. sorry

i think i might put my own build up on the website if people are still interested.[/QUOTE]

Interesting, maybe it has to do with some of the compiler options/firefox config options that I am using. I will try to do a clean build tonight.

-khc

---

### Post by ssam on 2005-11-21
i should have a build uploaded this afternoon

---

### Post by ssam on 2005-11-21
done :-)

download from [http://www.tygier.co.uk/linux/firefox.html](http://www.tygier.co.uk/linux/firefox.html)

these instructions should work

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

please post reports of how it works for you.

---

### Post by khc on 2005-11-24
[QUOTE=ssam]i cant replicate that bug on my system, i opened 30 tabs (though most of them where empty) and draged them around lots, also dragged a file to nautilus, and go a save as dialog. sorry

i think i might put my own build up on the website if people are still interested.[/QUOTE]

Turns out the bug is [https://bugzilla.mozilla.org/show_bug.cgi?id=305970](https://bugzilla.mozilla.org/show_bug.cgi?id=305970) which has a patch attached, seems to have fixed the issue for me.

---

### Post by tijs on 2005-11-24
Thanks a lot for this build, much better than the present "stable" 1.0.7 release which is horribly unstable for me (on a G4).

It is impossible, however, to update to the latest RC3. This is what comes up when you open Firefox beta2 powerpc from a shell, try to check for updates and when it crashes:

[PHP]./run-mozilla.sh: line 131:  5472 Illegal instruction     "$prog" ${1+"$@"}
[/PHP]

Oh well, back to the big Mozilla package again, hope the final FF 1.5 comes out soon, which will also have a powerpc build for Linux I hope...

---

### Post by khc on 2005-11-24
[QUOTE=tijs]Thanks a lot for this build, much better than the present "stable" 1.0.7 release which is horribly unstable for me (on a G4).

It is impossible, however, to update to the latest RC3. This is what comes up when you open Firefox beta2 powerpc from a shell, try to check for updates and when it crashes:

[PHP]./run-mozilla.sh: line 131:  5472 Illegal instruction     "$prog" ${1+"$@"}
[/PHP]

Oh well, back to the big Mozilla package again, hope the final FF 1.5 comes out soon, which will also have a powerpc build for Linux I hope...[/QUOTE]

Disable autoupdate, when I build it, I personally don't even have that feature compile in. Autoupdate isn't going to work because mozilla doesn't build linuxppc binaries.

Extension updates, however, works fine.

---

