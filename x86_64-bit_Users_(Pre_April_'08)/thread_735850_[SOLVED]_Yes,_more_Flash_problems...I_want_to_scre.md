---
title: "[SOLVED] Yes, more Flash problems...I want to scream!"
date: 2008-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Udibuntu on 2008-03-26
Hi guys,

I know half the Ubuntu forum is dedicated for Flash problems, but I can't seem to open the episodes in [Southpark new website]("http://www.southparkstudios.com/")...

I use FF64 but revert to FF32 per Kilz's step by step, but no dice.

I've uninstalled gnash, installed swfdec using Synaptic, still, no dice..

I'm using Flashblock and Adblock (I disabled them but no Southpark episode)...

Please..I need my fix :confused:

Thanks,

Udi

---

### Post by Bubba64 on 2008-03-26
I couldn't get it to play either and I have every thing needed for it to work I think it may be the site. Now it works when I allowed popups, are you blocking cookies or java.

---

### Post by bailbath on 2008-03-26
I just tried the link you gave and it works fine for me! I use Firefox 3 in hardy beta 64 bit.I use w64 and non free flash from synaptic.
IAN

---

### Post by Udibuntu on 2008-03-26
Thanks Bubba for checking this.

This problem occurs in other Flash movie sites (online TV and stuff), but it didn't piss me off so much :mad:

I allowed this site to pop up, and I can see the PLAY icon. When I right click the frame where the Flash should be, I see all the info related to the Flash - play, pause, full screen etc, but not the movie itself...

I'll keep looking...if anyone can share a solution I'd greatly appreciate it.

Udi

---

### Post by Bubba64 on 2008-03-26
I use a 32 bit computer so I have no real answer for you but this thread might.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by Udibuntu on 2008-03-26
Hi Ian, thanks.

I'm with  Firefox/2.0.0.12 on Ubuntu-feisty64bit.

Enabled Java, pop ups, Flashblock is disabled...no dice.

Udi

---

### Post by grumpymole on 2008-03-26
That site seems to work fine for me.

Hardy 64bit using the default FF3b4 (also 64bit, I assume).  No AdBlock.

Previously, I had problems getting flash to work and had to follow recipes of copying files around etc.  I could get some flash sites to work this way, but not all.

Then, II reinstalled with Hardy Beta and did not follow any of these threads.  Instead, I just installed flashnonfree-plugin though synaptic and it works fine for me.

Not sure if that helps.

Cheers

---

### Post by Udibuntu on 2008-03-26
Cheers Warren.

I think FF3 is a little too hardcore for me at the moment....

Udi

---

### Post by firecat53 on 2008-03-26
I have flash on 64-bit swiftweasel working via the nspluginwrapper (works with the South Park site). I believe I installed it using a script provided by Kilz. FYI, here are the locations of the various libflashplayer.so files . . . maybe you can match this up with your installation. This is also the older version of flash, per Kilz instructions, which works when the newest 115 version will not.

/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

Try to start from scratch .... find all the files above (locate libflashplayer), delete them, and then try using Kilz's script to install it again.

Good luck!
Scott

---

### Post by Udibuntu on 2008-03-26
Thanks Scott.

rm'ed all the files mentioned, then re-ran Kilz's script.

Tested on Southpark site: Flash works just fine, episodes run fine except there is no image, i.e play bar is there, Flash right-click options are there, but no movie....

I'm starting to think this is not a Flash player problem...any ideas?

Thanks again,

Udi

---

### Post by gaussian on 2008-03-27
> **Udibuntu said:**
> Thanks Scott.

rm'ed all the files mentioned, then re-ran Kilz's script.

Tested on Southpark site: Flash works just fine, episodes run fine except there is no image, i.e play bar is there, Flash right-click options are there, but no movie....

I'm starting to think this is not a Flash player problem...any ideas?

Thanks again,

Udi

How about just running a 32bit Firefox+Flash? 

I have a chrooted 32-bit environment mostly to run Flash websites (Webkinz in my case, it does not work well with nspluginwrapper). There are other applications also that I use that need 32-bit libraries (e.g. Stata, Skype). I know it is a matter of taste how you want to run 32-bit applications and lot of people say that chrooting is an overkill. There guides in this very forum to other approaches for running a 32-bit Firefox+Flash.

P.S. Southpark seems to work well this way

---

### Post by Udibuntu on 2008-03-27
Cheers gaussian, I tried to use FF32 but still no Southpark episodes...

It's a tough test case, I wrote to their tech support and hopefully they'll have a clue on what's going on...

I switched to Windows (for the first time in more than 6 months...) and SP episodes loaded like a charm...

Weird stuff...

---

### Post by CIZZO20 on 2008-03-27
I just installed Hardy Heron yesterday. Right away i am having problems with flash.

My flash vids start and play for a few seconds before it just stops. It has no sound or anything but it always plays for about 3 to 4 seconds before just stopping in its place. I click play but nothing happens but if i skip the video up a little using the slider it will play again for 3 to 4 seconds then stop again.

I have tried letting firefox install the flash plug-in (which is that nonfree one i think) and i have tried swfdec and had no luck. I have tried installing firefox 2 and it does the same thing. 

I never had these problems in 7.10 . In 7.10 everything worked without any problems. Never even had sound issues with flash which i seen that was a issue with many other people in 7.10 .

[COLOR="Red"]Edit---- Sorry i posted this in wrong spot. All i seen was the topic and not where it was posted at. I am not a x86 64-bit User so please delete this post. going to post it in another spot.[/COLOR]

---

### Post by Udibuntu on 2008-03-27
Guys, I've re-installed FF32bit and got these results:

udi@udi-laptop:~$ firefox32
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(firefox-bin:20468): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

What gives here?********************************Please ignore, I've posted this output in Kilz's 32FF mega-thread

---

### Post by no1wantdthisname on 2008-03-27
On hardy 64 bit here.  It works, but it seems to slow down ff3.  The video plays fine if I don't touch anything, but freezes if I so much as move the mouse.

---

### Post by gaussian on 2008-03-27
> **Udibuntu said:**
> Cheers gaussian, I tried to use FF32 but still no Southpark episodes...

It's a tough test case, I wrote to their tech support and hopefully they'll have a clue on what's going on...

I switched to Windows (for the first time in more than 6 months...) and SP episodes loaded like a charm...

Weird stuff...

I tested again (I had only checked the trailers, now I watched a part of a full episode). It works perfectly with my setup. With very limited 64-bit experience (already a month) it seems that chroot approach seems to have its benefits. No hacking around with librarires. It is initially more work and sometimes you get mixed up with things like "Why can't my Firefox open a .doc link? Oooh, it is because I have not installed Openoffice on the 32-bit environment and it cannot see my 64-bit version". 

Another comment: my experience is that you need the newest flash (r115) to get most websites working. The new version might be buggy, might not work with Konqueror (and Opera?), might crash, but some websites are not functional without the newest.

---

### Post by Udibuntu on 2008-03-28
Thanks gaussian.

I'll dive a little into the chroot thing and see how I find it.

r115 is not recommended by the ancients, so I'll see if there's another way to work this out.

Thanks again,

Udi

---

### Post by gaussian on 2008-03-28
> **Udibuntu said:**
> Thanks gaussian.

I'll dive a little into the chroot thing and see how I find it.

r115 is not recommended by the ancients, so I'll see if there's another way to work this out.

Thanks again,

Udi

Seriously, I would go back and try r115 with 64-bit nspluginwrapper first. I know it is not recommended, but it is my experience with many kid websites that they don't work without the absolute latest Flash. I think the kid websites (Disney's, Webkinz, PBSkids etc) can be the hardest tests of Flash compatibility since they require all sort of interactions beyond playing video. This is cross platform: the same is at least true with my hand-me down PPC Mac (G3 Pinto) running OS X.

As for setting up chroot  followed the instructions from [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

The only thing I changed is to add the export DISPLAY declaration in the do_chroot script given there.

---

### Post by Udibuntu on 2008-03-28
OK man, I'll try the new one and see how it goes.

Hope I live to tell... :)

---

### Post by Kilz on 2008-03-28
> **gaussian said:**
> Seriously, I would go back and try r115 with 64-bit nspluginwrapper first. I know it is not recommended, but it is my experience with many kid websites that they don't work without the absolute latest Flash. I think the kid websites (Disney's, Webkinz, PBSkids etc) can be the hardest tests of Flash compatibility since they require all sort of interactions beyond playing video. This is cross platform: the same is at least true with my hand-me down PPC Mac (G3 Pinto) running OS X.

As for setting up chroot  followed the instructions from [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

The only thing I changed is to add the export DISPLAY declaration in the do_chroot script given there.

Chroots are not needed to run flash. They are complicated and take up lots of resources. They used to be necessary long ago when Breezy was released, but since Dapper drake they are next to useless unless you are doing development work. 
The original poster needs to stick with getting nspluginwrapper working. The site he wants runs just fine with the r48 plugin and nspluginwrapper. My guess is that he has tried 10 different ways that failed and they left files that are stopping flash, or he has the ia32-libs issue because the apt-mirror he is using is bad.

---

### Post by Udibuntu on 2008-03-28
Kilz, thanks for going through the trouble of searching for this thread.

Your are right, I did try 10 different methods, 10 times each (but removed leftover files, like someone suggested :cool: )

As I said in your mega thread about the r48, the problem was with Adblock.

Apparently I originally had something wrong with my Flash plugin setup, that's why when I first disabled Adblock I couldn't run the Flash in SouthPark site; When I re-installed the plugin I must have done it right, so when I disabled Adblock a second time I was able to see the vid.

What can I say besides a big Thank You...thank you!

udi

---

### Post by NeoAndersen on 2008-07-23
[LEFT][/LEFT]Hi!
  I have downloaded and installed Ubuntu amd64 aproximatelly 1 month ago so I am a beginner in linux...
My other windows hd is not booting anymore (NTLDR missing...) but I dont want to find how to fix its boot just to watch South Park in windows... Without windows I am forcing myself to learn how to deal with Ubuntu and I really want to learn all about Linux and Ubuntu!!

   How can I delete leftover files?
Which flash plugin I must reinstall?
Can I reinstall it using synaptic? I have installed adobe flash...  but seems to me I've  installed another flash plugin the first day I installed Ubuntu to watch youtube videos... if so How can I find all flash plugins to reinstall them?
I guess I dont have Adblock... I just find block pop-up on the mozilla menu...

---

