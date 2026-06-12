---
title: "no video for dvd but can play mpeg2 files"
date: 2007-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by steveyeager on 2007-11-27
I have installed ubuntu 7.10 and most everything works except dvd playback.  When I insert a DVD, Totem starts and begins playing the DVD as an audio disk.  Video is just the visualization effect.  The audio is correct.  And it starts right into the movie with no menus.

This goes for home made DVDs as well, with no encryption.  Still plays them with audio but no video.

I can play mpeg2 files just fine.

What can I try to resolve this?

---

### Post by ryanVickers on 2007-11-27
make sure you've got all the gstreamer plugins, and Ubuntu extras just to be same, and if possible xine as well :p

also, look for w32/64codecs and something along the lines of libdvd____... may have to add repositories... google it :p

---

### Post by steveyeager on 2007-11-27
I followed several links and got several gstream files as well as gxine.  I also tried ogle to see if another dvd player would work (specifically with dvd menus) and it works.  However, totem only plays audio (says it is reading from cdrom and not dvd) and gxine says 'No demuxer found - stream format  not recognized.' when trying to play it as a dvd.

Still not certain what to try now.

---

### Post by ryanVickers on 2007-11-27
exactly - I used to have [Automatix2]("http://ubuntuforums.org/showthread.php?t=564099") (if you want to give that a try) and it's super easy to install all the codecs for that from it, but just a warning! It was always perfect for me, but some people say it messes everything up!
It only has dapper, edgy, ad feisty, but I'm sure it will work... you also can pick 64 or 32 bit!

Point is, you still need the w32/64codecs and something along the lines of libdvdcss2 or libdvd___...... (and automatix can install them for you...)

---

### Post by rune0077 on 2007-11-28
Totem can play most kind of video, but DVD is not fully supported yet. You can remove the visualisation somewhere in the menu to get normal playback instead, but you can't prevent Totem from starting up in the middle - this is caused, I think, by the DVD-menu which Totem does not yet recognize and tends to get very confused by :). Not much to do about, except give the developers some time to properly implement it. Until then, use another DVD-player.

---

### Post by steveyeager on 2007-12-02
Quite right, I guess.  I have successfully installed a gui for ogle and mplayer and both play dvd perfectly.  Ogle is not as polished, but even plays my star trek original series 4 episode  menus perfectly.  Mplayer is more polished and plays most menus.  So, now how do I surplant totem as my default player in favor of mplayer?

---

### Post by rune0077 on 2007-12-03
Under System > Preferences > Removable Drives and Media, you can select what programs to launch when you insert various media. Dunno if that's what you're looking for, but it should do the trick.

---

