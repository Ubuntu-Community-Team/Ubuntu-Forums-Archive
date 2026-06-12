---
title: "Help!  Can't get x86_64 flash 10 working on Firefox (Hardy)"
date: 2009-03-31
forum: x86 64-bit Users
---

### Post by stuntmonkey on 2009-03-31
I am at my wits' end.  I would like to get the x86_64 version of flash working with Firefox on my Ubuntu installation without the nspluginwrapper, but have had no luck so far.

Some background, I'm currently running Hardy with Firefox 3.08 (upgraded from 3.03 in the process of flailing for a solution).

I was previously running flash 9 using the nspluginwrapper, which worked but was very unstable.

I believe I removed all the old flash and nspluginwrapper stuff, as instructed.

I then downloaded the alpha flash plugin (libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz), untar'd it, and copied it to ~/.mozilla/plugins.  Restarted firefox, and did "about:plugins".  Hmmm, no flash.  How curious.

I then flailed around assuming that I didn't have the right plugin directory, and ended up copying it to (at least) the following locations under /usr/lib64:

./iceape/plugins/libflashplayer.so
./firefox-addons/plugins/libflashplayer.so
./mozilla/plugins/libflashplayer.so
./flashplugin-nonfree/libflashplayer.so
./xulrunner-addons/plugins/libflashplayer.so
./firefox/plugins/libflashplayer.so
./iceweasel/plugins/libflashplayer.so

None of these did the trick.  I am pulling my hair out, and there's just plain not enough left to be doing that.

Help!!

---

### Post by philinux on 2009-03-31
sudo updatedb

then 

locate libflashplayer.so

On my system it only exists in /home/username/.mozilla/plugins/libflashplayer.so

---

### Post by stuntmonkey on 2009-03-31
Thanks for the quick reply.  Here's the output from locate:

/home/username/.mozilla/firefox/plugins/libflashplayer.so
/home/username/.mozilla/plugins/libflashplayer.so
/home/username/flash/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/iceape/plugins/libflashplayer.so
/usr/lib/iceweasel/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so

I could try wiping out the other copies of libflashplayer.so...?  But then I'd be back (approximately) where I started ...

---

### Post by philinux on 2009-03-31
Get rid of all but the one in your home directory.
/home/username/.mozilla/plugins/libflashplayer.so
Thats the one you need.

gksu nautilus

and remove flash from synaptic.

---

### Post by stuntmonkey on 2009-03-31
Okay, I removed all of the other versions of libflashplayer.so.  locate confirms that the only copy on the machine is in /home/user/.mozilla/plugins/libflashplayer.so.

Did a search for "flash" in synaptic and confirmed that no packages in the search list are listed as installed.

Still no joy, unfortunately ...

---

### Post by kevmitch on 2009-03-31
I have had success using the [flashplugin-nonfree_2.5_amd64.deb ]("http://packages.debian.org/sid/amd64/flashplugin-nonfree/download") from Debian on Intrepid. This is also nice because then apt knows that flash is installed and will hopefully set it up for you too. 

You might want to make sure that you don't have an other flash player installed 

```
sudo aptitude purge gnash
```

You should also check that your flash-mozilla.so alternative is pointing to /usr/lib/flashplugin-nonfree/libflashplayer.so 
```
sudo update-alternatives --configure flash-mozilla.so
```

---

### Post by stuntmonkey on 2009-03-31
I installed flashplugin-nonfree_2.5_amd64.deb.  I can see that it's installed under synaptic (1:2:5).

"sudo aptitude purge gnash" resulted in 0 packages being found.

"sudo update-alternatives --config flash-mozilla.so" tells me that "There is only 1 program which provides flash-mozilla.so".

Still no flash showing up in about:plugins, though ...

---

### Post by WilliamJenningsBryan on 2009-04-01
Also find/delete all copies of flash-alternative.so

That normally fixes it for me.

---

### Post by stuntmonkey on 2009-04-01
Darn, there doesn't appear to be anything called "flash-alternative.so" on my system..

---

### Post by Vico Vicario on 2009-04-01
For me the home directory didn't work. I placed the downloaded flash in /usr/lib/firefox-addons/plugins/ and it worked for me.

V.

---

### Post by stuntmonkey on 2009-04-01
I went ahead and tried "/usr/lib/firefox-addons/plugins/" again, but to no avail ..

There must be some way to either ask firefox what its default plugin directory is, or else to manually force it to pick up a plugin that's not in a standard location ...

Oh, just for reference, here's the info that firefox provides on its Help:About screen:

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.8

---

### Post by philinux on 2009-04-01
Sorry to state the obvious but one step you have to do is close then reopen firefox for the changes to take place.

What you got in 

```
about:plugins
```

---

### Post by stchman on 2009-04-01
> **stuntmonkey said:**
> I am at my wits' end.  I would like to get the x86_64 version of flash working with Firefox on my Ubuntu installation without the nspluginwrapper, but have had no luck so far.

Some background, I'm currently running Hardy with Firefox 3.08 (upgraded from 3.03 in the process of flailing for a solution).

I was previously running flash 9 using the nspluginwrapper, which worked but was very unstable.

I believe I removed all the old flash and nspluginwrapper stuff, as instructed.

I then downloaded the alpha flash plugin (libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz), untar'd it, and copied it to ~/.mozilla/plugins.  Restarted firefox, and did "about:plugins".  Hmmm, no flash.  How curious.

I then flailed around assuming that I didn't have the right plugin directory, and ended up copying it to (at least) the following locations under /usr/lib64:

./iceape/plugins/libflashplayer.so
./firefox-addons/plugins/libflashplayer.so
./mozilla/plugins/libflashplayer.so
./flashplugin-nonfree/libflashplayer.so
./xulrunner-addons/plugins/libflashplayer.so
./firefox/plugins/libflashplayer.so
./iceweasel/plugins/libflashplayer.so

None of these did the trick.  I am pulling my hair out, and there's just plain not enough left to be doing that.

Help!!

Follow my tutorial on Flash 10.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

---

### Post by stuntmonkey on 2009-04-01
No offense taken, I've been shutting down all instances of Firefox and restarting after each step.  Ya gotta make sure to rule out the obvious, though...

I get the following for installed plugins:
[B]
Default Plugin[/B] (/usr/lib/xulrunner-addons/plugins/libnullplugin.so)
**Demo Print Plugin for unix/linux** (/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so)
**DivX Browser Plug-In** (/usr/lib/mozilla/plugins/gecko-mediaplayer-dvx.so)
**QuickTime Plug-in 6.0 / 7** (/usr/lib/mozilla/plugins/gecko-mediaplayer-qt.so)
**RealPlayer9** (/usr/lib/mozilla/plugins/gecko-mediaplayer-rm.so)
**Windows Media Player Plug-in** (/usr/lib/mozilla/plugins/gecko-mediaplayer-wmp.so)
**gecko-medialplayer 0.6.0** (/usr/lib/mozilla/plugins/gecko-mediaplayer.so)
**iTunes Application Detector** (/usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so)
**Totem Web Browser Plugin 2.22.1** (/usr/lib/totem/gstreamer/libtotem-basic-plugin.so)
**Helix DNA Plugin: RealPlayer G2 Plugin-In Compatible** (/usr/lib/totem/gstreamer/libtotem-complex-plugin.so)
**VLC Multimedia Plugin (compatible Totem 2.22.1)** (/usr/lib/totem/gstreamer/libtotem-cone-plugin.so)
**Windows Media Player Plug-in 10 (compatible; Totem)** (/usr/lib/totem/gstreamer/libtotem-gmp-plugin.so)
**DivX(r) Web Player** (/usr/lib/totem/gstreamer/libtotem-mully-plugin.so)
**QuickTime Plug-in 7.2.0** (/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so)

I believe I am looking for "Shockwave Flash", correct me if I'm wrong.

---

### Post by stuntmonkey on 2009-04-01
> **stchman said:**
> Follow my tutorial on Flash 10.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

Thanks for the pointer to the tutorial!  Unfortunately, I just ran through it and it doesn't appear to have solved my problem.

---

### Post by kevmitch on 2009-04-01
Maybe there's something funky with your profile. Try creating a new one and staring firefox with that. 

```
firefox -CreateProfile new && firefox -P new
```

(don't worry that should leave your existing profile untouched).

Oh while your at it, are then any messages in the terminal when you run those commands?

---

### Post by stuntmonkey on 2009-04-01
Holy crap, it's working!

I followed kevmitch's suggestion and tried creating a new profile and running firefox from the command line.

When I did, I noticed that it complained about a missing shared library when trying to load libflashplayer.so:

```
LoadPlugin: failed to initialize shared library /home/username/.mozilla/plugins/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]
```

Well, THAT was new information!  It appeared to only give me the error when a new profile was created, too.  If I just ran firefox from the command line I didn't get any errors on startup.  (Perhaps I could have wiped the plugin database, too, by deleting pluginreg.dat and seen the same thing..?)

I went ahead and searched for information on that specific error, and it looks like the plugin is assuming that certain libraries will be symbolically linked in /usr/lib to various names.  I began creating symbolic links for the shared libraries - each one I added would give me a new missing library when I ran Firefox.

Maybe the libraries were linked correctly at one point on my system and uninstalling one of the packages wiped the links out?  Not sure.  But here's what I did to get it working:

```
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplcs4.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
```

After that, I was able to see Flash under my plugins page, and I was able to play videos on YouTube (first one was my daughter doing raspberries for the first time :p).

A big **THANK YOU!!!** to everyone who offered suggestions in this thread, I never would have figured it out without all of the help!

---

### Post by stchman on 2009-04-01
> **stuntmonkey said:**
> Thanks for the pointer to the tutorial!  Unfortunately, I just ran through it and it doesn't appear to have solved my problem.

It is important to make sure and autoremove the flashplugin-nonfree package.  This will make remove the nspluginwrapper package as well.

I have used this procedure on (3) different 64 bit machines running Hardy.

---

### Post by kevmitch on 2009-04-01
I did an 

```
apt-file search <filename>
```

on those symlink targets and I get the following packages

libnspr4-0d:
libnss3-0d:
libnss3-1d:

You might want to do an ```
aptitude reinstall <packagename>
``` on those in case anything else is out of place.

---

### Post by philinux on 2009-04-01
Good news then. ):P

---

### Post by stuntmonkey on 2009-04-01
> **kevmitch said:**
> 
You might want to do an ```
aptitude reinstall <packagename>
``` on those in case anything else is out of place.

Ah!  Good advice.  I went ahead and did an "aptitude reinstall" on those packages to be on the safe side, and everything is still working fine.

Thanks again, everybody!

---

### Post by Yellow Pasque on 2009-04-02
I know  your issue is solved, but I'm curious about something:
> Mozilla/5.0 (X11; U; Linux x86_64; en-US; **rv:1.9.0.3**) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.8
This caught my eye. It looks like your FF is(was?) pointing at on old version of Gecko (xulrunner).
Can you look at the about screen again and see if it changed since you created a new profile?

If it still says rv:1.9.0.3, can you post output of:
```
ls -la /usr/lib | grep xul
```
Thanks.

---

### Post by stuntmonkey on 2009-04-02
> **Temüjin said:**
> I know  your issue is solved, but I'm curious about something:

This caught my eye. It looks like your FF is(was?) pointing at on old version of Gecko (xulrunner).
Can you look at the about screen again and see if it changed since you created a new profile?

If it still says rv:1.9.0.3, can you post output of:
```
ls -la /usr/lib | grep xul
```
Thanks.

Sure thing - checked Firefox and got the following, same as before:

```
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.8

```
Just for good measure, I created a whole new profile using the instructions from earlier and checked again with the Firefox that popped up from the command line - same thing.

Here's the output from the ls -la:
```

user@localhost:~$ ls -la /usr/lib | grep xul
drwxr-xr-x   3 root root     4096 2008-07-11 10:41 xulrunner
drwxr-xr-x  11 root root     4096 2008-11-11 08:56 xulrunner-1.9.0.3
drwxr-xr-x   4 root root     4096 2008-05-23 14:33 xulrunner-addons
```

---

### Post by Yellow Pasque on 2009-04-02
That's odd. If you've been downloading updates, you should have xulrunner 1.9.0.8
[http://packages.ubuntu.com/search?keywords=xulrunner&searchon=names&suite=hardy-updates&section=all](http://packages.ubuntu.com/search?keywords=xulrunner&searchon=names&suite=hardy-updates&section=all)

---

