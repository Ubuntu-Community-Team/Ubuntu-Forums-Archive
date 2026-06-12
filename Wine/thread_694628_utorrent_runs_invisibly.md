---
title: "utorrent runs invisibly"
date: 2008-02-12
forum: Wine
---

### Post by varangian on 2008-02-12
Last time I booted this machine utorrent was running fairly happily under wine with just the odd quirk. Today I log on and run the launcher and it appeared nothing was happening. On closer inspection I noticed network activity and found wineserver and utorrent in the process list, so utorrent started but didn't get show a window. A cli launch gives the following:

fixme:msvcrt:__lconv_init  stub
fixme:heap:HeapSetInformation 0x110000 0 0x458b00 4
fixme:heap:HeapSetInformation 0x610000 0 0x458b00 4
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 16 lpiArray 0x33ed58
fixme:keyboard:UnregisterHotKey (0x20026,1): stub

so it's obviously not a happy bunny. OS is Gutsy and Wine version is 0.9.46. The OS has had all the automatic updates applied though I didn't notice any for Wine in the recent batches. The utorrent executable hasn't changed since the original install. I'm tempted to nuke everything and try a re-install as that won't take long but any more elegant solutions always welcome.

---

### Post by Jimmey on 2008-02-12
uTorrent likes to stay on the desktop that was in use when it was launched. Try switching between desktops.

You can get a more recent version of wine by following the steps provided on [http://winehq.org](http://winehq.org)

---

### Post by hyperair on 2008-02-12
Instead of using uTorrent, why don't you try some native torrent programs? Examples include:
KTorrent (my favourite-has pretty much everything uTorrent has, and more)
Deluge Torrent (Slightly less features than KTorrent, but still very good, integrates well on a GNOME desktop)
Transmission
Azureus

---

### Post by oedipuss on 2008-02-12
Try deleting the file "settings.dat" in .wine/drive_c/windows/profiles/application settings/utorrent . (I may be off by a couple of dirs, it's around there though) . 
This will reset all utorrent settings to the default ones, which can be a pain sometimes, but it also makes my utorrent window reappear.
I think this bug happens when I try to switch desktops after I've launched utorrent but before it actually appears, but it's difficult to pinpoint.

---

### Post by hyperair on 2008-02-12
I'd like to mention that when I ran uTorrent on Wine ages back, I always got annoyed with the interface being laggy and all, so I just let it run invisibly, and activated the WebUI. That's where I controlled the program.

---

### Post by varangian on 2008-02-12
Thanks for all the above suggestions/comments. I don't think it was the desktop - I always run it on desktop 2 to keep it out of the way. The settings.dat I'll try next time - I'm in XP mode as I want to record some TV and it's one of those devices with no driver support. Love the idea of letting it run invisibly all the time and using the web UI so I'll give that a go as well.

Re other bittorrent clients I have tried them but Ktorrent/Transmisson don't yet have the features I like. Azureus I haven't tried on Ubuntu but I stopped using it on XP as utorrent did all I needed better. Deluge very nearly does it for me - a couple of missing features I could work around - but I found a few obvious (i.e. process dies type) bugs and I found that even if I limited the u/l to just under the max. my connection supports Deluge did a quite effective job of borking all other connectivity. If I set the u/l rate to unlimited it would kill it stone dead - minutes to load very basic web pages and the like. Hopefully later releases of Deluge will resolve such issues as I'd prefer a native (and open) solution.

---

### Post by hyperair on 2008-02-13
What missing features did you notice in KTorrent? It's done everything I've ever wanted, and more.

---

### Post by Ferrat on 2008-02-13
Im running utorrent with no problems at all, just use the systray icon to hide and show it?

---

### Post by smac4president on 2008-02-13
I just had this exact same problem.  Ran uTorrent for about a month with no problems but suddenly I can't pull it up.  When I do try to open it, it starts to draw a constant 4-5% cpu also.

Deleted settings.dat AND settings.dat.old and that seemed to get me back in, minus my settings/scheduler of course.

I don't like KTorrent cause it draws a constant 10% or so cpu on my computer even after a few reinstalls and I don't see the point of wasting that energy all night if I can draw .25-.50% with uTorrent + wine.

---

### Post by varangian on 2008-02-25
This has happened a couple of times to me now. I can't spot any common factor or action on my part so far. Oddly the suggested action of deleting settings.dat (and the .old) didn't quite work for me. Deleting the entire folder where this and the resume.* files lived did, however, so this is obviously the source of the problem. Perhaps something was being cached elsewhere.

Also odd was that the 2nd time around the restart fixed a problem I had with max u/l speeds. In XP I'd always set allowed an unrestricted u/l rate when only seeding and throttled it back while downloading. In Wine I found this didn't work, utorrent either thought it wasn't downloading when it was or just ignored the alternate setting altogether so I had to keep manually changing the u/l rate. No idea why it suddenly works, perhaps I restored my preferred settings in a different order, but it's compensation enough.

Re the question about Ktorrent I'll check it again. Thinking about it I last looked at it 6 months ago and a zillion eager coders may well have added in whatever I missed about it.

---

