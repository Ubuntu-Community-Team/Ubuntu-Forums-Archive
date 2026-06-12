---
title: "[SOLVED] high cpu usage by operapluginwrapper"
date: 2008-05-06
forum: x86 64-bit Users
---

### Post by tamoneya on 2008-05-06
I have been running 64 bit hardy and just recently I switched from firefox 3b5 to opera 9.50 beta.  I also have flashplugin-nonfree install.  Today I noticed that my computer was running a little sluggish.  I ran top and saw that there were two instances of "operapluginwrapper-ia32-libs" that were taking up 30% of my cpu each.  I think these are related to making the flash plugin work in 64 bit opera.  Does anyone know a way around this problem?  Has anyone else run into something similar?  I am considering uninstall flashplugin-nonfree if it speeds up my computer but I am curious to know what you guys think.

---

### Post by inphektion on 2008-05-06
Well at this point there is a newer version of opera just came out today so might as well be on that. 
[Here.]("http://snapshot.opera.com/unix/snapshot-1951/x86_64-linux/opera_9.50-20080506.2-shared-qt_amd64.deb")

I noticed my flash plugin was at 100% cpu so I uninstalled flashplugin-nonfree and then flash didn't work.  I reinstalled via the repo's, installed the new opera .deb and flash still didn't work. 

In Opera I went to Tools->Preferences->Advanced, Downloads on the left side.  Click on the swf extension and select Edit button.

When I went here the Use plug-in was selected but had the plugin as /usr/lib/mozilla/plugins/flashplugin-alternative.so

I changed it to /usr/lib/flashplugin-nonfree/libflashplayer.so

restarted opera.  Flash still didn't work.  Then I did an rm /usr/lib/mozilla/plugins/flashplugin-alternative.so hence removing the other plugin altogether.  Restart opera again.  Now flash works again.  Ran top.  Now instead of 100% cpu it fluctuats between 20-40% but only when I have a site open that is actively playing flash.  When I navigate away from a flash site the opera plugin wrapper drops off the charts.  This is acceptable to me as long as it only uses cpu when actively playing flash.

---

### Post by tamoneya on 2008-05-06
Thanks for the help.  I didn't realize they had another build up.  I wil try what you recommened and report back here if it works.

Thanks

EDIT: Like always the Ubuntu Forums never disappoint.  I was honestly expecting people to say that my only option was to not use flash anymore.  Worked perfectly.

---

### Post by inphektion on 2008-05-06
so before it was taking 30% all the time and now it behaves as it does on my system for you (ie 30% only when using flash site)?  Or is it taking less than 30% now?  I'm just trying to quantify normal behavior of it so I know.

---

### Post by tamoneya on 2008-05-06
it used to be running two processes both at 30% 24/7.  Now it is running one at 17-18% while playing a youtube video.  Once I close that tab it fall off of top.  Opera itself is running at about 2%.

---

### Post by tamoneya on 2008-05-06
after some more intensive testing it seems like the problem is not fully fixed.  It seems like everyonce and a while the operapluginwrapper gets "lost" and opera spawns another one.  The problem is that the lost one then goes and eats up a bunch of the CPU.  I was viewing some youtube videos and I had top going on my other screen.  I noticed that I had one operapluginwrapper process all the way at the top with 99% usage and then another one at 18%.  The 18% is the normal one from what I can tell and once I close the youtube window it disappears.

---

### Post by inphektion on 2008-05-06
Yea def isn't the best behaving thing.  Hopefully its fixed when out of beta I have conky running so if I see the wrapper jump up I'll just kill it.

---

### Post by tamoneya on 2008-05-06
i think it has more to do with flashplugin-nonfree than opera.  I hope that the open sourcing of flash creates an alternative to flashplugin-nonfree.

---

### Post by trash on 2008-08-03
> **inphektion said:**
> 
In Opera I went to Tools->Preferences->Advanced, Downloads on the left side.  Click on the swf extension and select Edit button.

When I went here the Use plug-in was selected but had the plugin as /usr/lib/mozilla/plugins/flashplugin-alternative.so

I changed it to /usr/lib/flashplugin-nonfree/libflashplayer.so

restarted opera.  Flash still didn't work.  Then I did an rm /usr/lib/mozilla/plugins/flashplugin-alternative.so hence removing the other plugin altogether.  Restart opera again.  Now flash works again.  Ran top.  Now instead of 100% cpu it fluctuats between 20-40% but only when I have a site open that is actively playing flash.  When I navigate away from a flash site the opera plugin wrapper drops off the charts.  This is acceptable to me as long as it only uses cpu when actively playing flash.

THANK YOU, worked here!:) I was getting worried i'd have to dump Opera because of this but now it is behaving nicely... Opera 9.51/32 bit

---

### Post by trash on 2008-08-07
was behaving... 6 pages open, not one of them running any flash and Opera and Operapluginwrap alternately hogging between 30-70% cpu all the time.

I guess this issue is not solved after all:(

---

### Post by n2dream on 2009-01-01
Thanks!  This solution worked for me on Hardy, using Opera 9.62.

---

