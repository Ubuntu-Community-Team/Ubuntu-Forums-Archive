---
title: "Video (inc. Flash) playback dies soon after following suggested fixes"
date: 2008-05-11
forum: x86 64-bit Users
---

### Post by netsurfau on 2008-05-11
Since upgrading to Hardy, I've had an on-going problem with watching any sort of video file.

I've uninstalled & reinstalled flash a number times (even trying different extra files eg: Ubuntu restricted extras without any lasting fix), and to start with video playback works.  But, only for about 4-5 times, then all I get is a gray box.

I just followed the directions given in - [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490) - purged then re-installed Flash, restarted FF and Flash was working, as was another site that uses Windoze format streaming video files.  I restarted FF again, everything still seemed to be working OK then, when trying to watch a video on a site linked off Digg.com ([http://gameroom.mlgpro.com/view/sVrwsulpz7BwQU.html](http://gameroom.mlgpro.com/view/sVrwsulpz7BwQU.html)) back to the gray box and every site that was just working, now has gray box as well.

I upgraded to Hardy using the 'Alt' AMD64 disk, from Gutsy and sys config is:

AMD AM2 64bit 6000+
4Gb RAM
Gigabyte M/board with nVidia Chipset 
nVidia 8600 GTS Super video card

As you will understand, this is extremely frustrating.  It seems I fix the issue, only to have it return in a short space of time.

Any ideas? Anyone?

](*,)  <- sick of doing this!

---

### Post by Yellow Pasque on 2008-05-11
Start firefox from the terminal and see what error message the program outputs. File a bug report on Launchpad (preferably after searching for similar reports).

---

### Post by netsurfau on 2008-05-12
No errors reported when stating FF from terminal.
Terminal just went to next line for input.

---

### Post by Zorael on 2008-05-12
I get the same thing, with or without libflashsupport so it's likely not pulse-related. This is, of course, on an x86_64 installation so my flash is nspluginwrapped by default.

I started a thread about it, with some terminal output and screenshots attached for illustration: [http://ubuntuforums.org/showthread.php?p=4936499](http://ubuntuforums.org/showthread.php?p=4936499).


At first, embedded flash will just often fail to draw, leaving a white box instead. Right-clicking this box will properly spawn a popup menu with the only alternative being 'About Flash Player 9', so it seems to me the plugin was initialized properly but failed to load the content somehow. Refreshing the page once or twice or five times may or may not make it play. However, after a while it'll "break" and leave grey boxes, which cannot be right-clicked. There is no particularly interesting terminal output and the browser must be restarted for the plugin to work once more.

It was suspected to be a pulse thing. As far as I've gathered, people were having issues with flash crashing their firefoxes caused by a semi-unstable libflashsupport (correct me if I'm wrong), to which one solution was to remove that library - breaking pulse compatibility with flash - and another to use an nspluginwrapper built for i386 systems. When flash would then try to crash the browser, nspluginwrapper would then act as a buffer and crash in its stead. This is proposed as the be-all-end-all workaround, but for us with x86_64 installations we're already running nspluginwrapper.

To troubleshoot, I removed flash completely and worked my way back to the point where sound once again worked for me (see the thread for that little adventure), but what is obvious is that flash was still sketchy with or without sound being properly passed to pulse. So if this was caused by libflashsupport, removing it would disable sound but increase stability, and it did one of those things.

As I mentioned there, sound in flash would *only* work in pulse if I used an svn snapshot of libflashsupport that I found by searching these forums, which makes me wonder how other x86_64 FF3 users got theirs to work.


In fact, if it works for you, I'd like to know the package versions of your nspluginwrapper and libflashsupport.
```
$ apt-cache policy nspluginwrapper libflashsupport
$ ls -l /etc/alternatives/mozilla*
```
Perhaps all of this can be solved by building a bleeding edge svn snapshot of nspluginwrapper, but the svn source I did manage to find wouldn't compile, as of yesterday.

Returning back to firefox-2 is not an option available to me, since FF2 goes unresponsive on me under the slightest load. For instance, opening ubuntuforums.org and middle-clicking five forum sections at once will make compiz flag the window as 'not responding' and fade it out. After perhaps 20-30 seconds it will have finished loading. Huge tagclouds will cause the same thing, making me suspect it has to do with sites containing lots and lots of links.

I end up using nspluginwrapper anyway if I use Opera, since the point of the wrapper is to provide "Netscape plugin support" to non-mozilla browsers, no? And since the suggested solution to stop flash from crashing firefoxes on i386 installations is to *install* nspluginwrapper, I get the feeling I'd only carry the plague with me.


Tagging the thread for interest, would love to hear more from those of you for whom it Just Works™.

---

### Post by Zorael on 2008-05-12
Curiously enough it does seem to work without hitches in Opera 9.50b2. At least on the first ~10 youtube tries.

---

### Post by Colonel Kilkenny on 2008-05-12
> **Zorael said:**
> Curiously enough it does seem to work without hitches in Opera 9.50b2. At least on the first ~10 youtube tries.

That is because Opera is not using nspluginwrapper. Opera is capable of running 32-bit plugins on its own. So there is no need for nspluginwrapper with Opera.

---

### Post by nightfrost on 2008-05-12
> **Colonel Kilkenny said:**
> That is because Opera is not using nspluginwrapper. Opera is capable of running 32-bit plugins on its own. So there is no need for nspluginwrapper with Opera.

If this really is true, shouldn't opera be able to use sun's 32-bit plugin and we would have all the 64-bit java problems solved? :-)

---

### Post by Zorael on 2008-05-12
Crossposting here since it's relevant to both discussions.
> **Zorael said:**
> I've found that I don't need a browser restart when it breaks completely (grey box, no right-click popup, as the earlier attached screenie shows); I just need to navigate away from any and all pages currently trying to display flash content. Of course, the next page I go to with flash content may break it again right away, but at least I don't have to restart the program.

I haven't been able to compile nspluginwrapper from source yet (about which I'll likely post a new thread), but I did try downgrading to the build Rashad Tatum posted over at [https://bugs.launchpad.net/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/nspluginwrapper/+bug/177856). ([http://launchpadlibrarian.net/11224902/nspluginwrapper_0.9.91.5-1ubuntu2_amd64.deb](http://launchpadlibrarian.net/11224902/nspluginwrapper_0.9.91.5-1ubuntu2_amd64.deb)). No noticeable improvement.

I'm reluctant to switch to Opera; the would-be "extensions" seem more like toys. I'm not sure I want an analog clock widget. Linux's FF3 - while still much slower than the Windows version - works great except for this one issue.

---

### Post by nightfrost on 2008-05-12
> **Zorael said:**
> Crossposting here since it's relevant to both discussions.


I'm reluctant to switch to Opera; the would-be "extensions" seem more like toys. I'm not sure I want an analog clock widget. Linux's FF3 - while still much slower than the Windows version - works great except for this one issue.

Agreed, but it would be nice to switch to opera when I need to do some of my bank errands, rather than fire up virtualbox + a 32 bit operating system to do that :-p

---

### Post by Kilz on 2008-05-12
> **netsurfau said:**
> Since upgrading to Hardy, I've had an on-going problem with watching any sort of video file.

I've uninstalled & reinstalled flash a number times (even trying different extra files eg: Ubuntu restricted extras without any lasting fix), and to start with video playback works.  But, only for about 4-5 times, then all I get is a gray box.

I just followed the directions given in - [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490) - purged then re-installed Flash, restarted FF and Flash was working, as was another site that uses Windoze format streaming video files.  I restarted FF again, everything still seemed to be working OK then, when trying to watch a video on a site linked off Digg.com ([http://gameroom.mlgpro.com/view/sVrwsulpz7BwQU.html](http://gameroom.mlgpro.com/view/sVrwsulpz7BwQU.html)) back to the gray box and every site that was just working, now has gray box as well.

I upgraded to Hardy using the 'Alt' AMD64 disk, from Gutsy and sys config is:

AMD AM2 64bit 6000+
4Gb RAM
Gigabyte M/board with nVidia Chipset 
nVidia 8600 GTS Super video card

As you will understand, this is extremely frustrating.  It seems I fix the issue, only to have it return in a short space of time.

Any ideas? Anyone?

](*,)  <- sick of doing this!

Did you follow the Hardy instructions in the flash sticky within the last 5 days??

---

### Post by netsurfau on 2008-05-12
>Kilz - That was one of the last suggested fixes I tried.
I searched through the forums and tried any fix that looked like it may work.  Unlike some, who were only losing sound, it either worked or didn't work.

At this stage it looks like I might have a temp fix:

Completely remove FF 3b5 and install FF 2.0.0.14 using the Synaptic Package Manager.

Did that this morning and have all video formats & flash working properly.  Will wait till June/July(?) when FF 3.0, as in full working release, becomes available and see how it goes.

Based on my experience, there is some issue with FF 3b5 and how it uses plugins, in Hardy.  What is going to make this issue (bug?) harder to fix is, there are no error messages that I could find being logged when Flash fails.

Now, all I need is the nVidia driver issue to be fixed.  Only have one app (Google Earth) affected so, not a major concern or priority.

---

### Post by Colonel Kilkenny on 2008-05-13
> **nightfrost said:**
> If this really is true, shouldn't opera be able to use sun's 32-bit plugin and we would have all the 64-bit java problems solved? :-)

To be honest I'm not expert in anyway nor have I idea what is the situation with Java atm but Opera does not use plugins with Java. Opera connects directly to JRE. 
Anyway, atm Java is not working at least for me with 64-bit Opera. And it probably should be working because if I have understood correctly the problem in general is that there is no plugin for 64-bit Java. But Opera does not need plugin so there's no problem, except that there is problem because atm it ain't working :)

Here's old blog post from Opera dev:
[http://my.opera.com/csant/blog/2007/10/26/32-bit-plugins-in-64-bit-opera](http://my.opera.com/csant/blog/2007/10/26/32-bit-plugins-in-64-bit-opera)
Note that the situation has changed since. Everything should be okay atm. and 64-bit Opera should be using 32-bit plugins just fine without any modifications.

---

### Post by nightfrost on 2008-05-13
> **Colonel Kilkenny said:**
> To be honest I'm not expert in anyway nor have I idea what is the situation with Java atm but Opera does not use plugins with Java. Opera connects directly to JRE. 
Anyway, atm Java is not working at least for me with 64-bit Opera. And it probably should be working because if I have understood correctly the problem in general is that there is no plugin for 64-bit Java. But Opera does not need plugin so there's no problem, except that there is problem because atm it ain't working :)

Here's old blog post from Opera dev:
[http://my.opera.com/csant/blog/2007/10/26/32-bit-plugins-in-64-bit-opera](http://my.opera.com/csant/blog/2007/10/26/32-bit-plugins-in-64-bit-opera)
Note that the situation has changed since. Everything should be okay atm. and 64-bit Opera should be using 32-bit plugins just fine without any modifications.
Yes! On my 32-bit machine, I have sun-java6 installed, -jre -bin, but not plugin. Opera shows java applets just fine. On the 64-bit machine it doesn't. My uninformed guess would be that it should, in fact, be able to show java content on the 64-bit machine as well. Hm. Strange.

---

