---
title: "Just switched to 64 - cnn video issue"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by LinuxConvertJune2006 on 2006-08-04
Hi all, I'd like to thank everyone who put together the scripts and step by step guides to help in getting a Dapper 64bit system up and running. So far so good. I would help anyone who is interesting in compiling all the steps/scripts into one program (firefox32/plugins/codecs/wine etc), seems like a worthy endeavor.

One note, the firefox32 script needs an update, the first line should be cd ~/Desktop/wine not Wine, and version .17 of that package doesn't exist anymore, its version .18 now (I'm guessing, it seemed to work for me).

Anyway my issue seems to be just getting CNN's video to work. I have mplayer running, can lauch it graphically, and it plays a test mpeg I had put together of a home movie. CNN's viedeo doesn't play but the sound plays fine. Anyone have any ideas?

Also, what about libdvdcss , how do I get that working (I'm going to backup movies legally using DVDShrink).

---

### Post by Kilz on 2006-08-05
> **LinuxConvertJune2006 said:**
> Hi all, I'd like to thank everyone who put together the scripts and step by step guides to help in getting a Dapper 64bit system up and running. So far so good. I would help anyone who is interesting in compiling all the steps/scripts into one program (firefox32/plugins/codecs/wine etc), seems like a worthy endeavor.

One note, the firefox32 script needs an update, the first line should be cd ~/Desktop/wine not Wine, and version .17 of that package doesn't exist anymore, its version .18 now (I'm guessing, it seemed to work for me).

Anyway my issue seems to be just getting CNN's video to work. I have mplayer running, can lauch it graphically, and it plays a test mpeg I had put together of a home movie. CNN's viedeo doesn't play but the sound plays fine. Anyone have any ideas?

Also, what about libdvdcss , how do I get that working (I'm going to backup movies legally using DVDShrink).

Thanks for the heads up, I havent updated the wine howto in awhile as I have been working on the Firefox scripts. Wine is just updated. [Here is a link to a page that tells how to use ]("http://www.tghc.org/staticpages/index.php/wine")wine. But you may be better off using k9copy for linux, its in the repositories.
The second issue is cnn. Cnn uses windows media player codecs. Im not sure there is a way to get them to work. The mplayer plugin isnt perfect, and when dealing with Microsoft proprietary formats its always iffy.

---

### Post by ylixir on 2006-08-05
you need the wm9 codecs installed for cnn video to work.  look at post #9 on [this thread]("http://www.ubuntuforums.org/showthread.php?t=188974") for an easy install of the firefox plug-in for 32bit mplayer, which will work with the win32 codecs.  it even works on 64 bit firefox :-D

---

### Post by LinuxConvertJune2006 on 2006-08-05
I read that link and I installed the 32bit version , downloaded 32-bit-firefox-mplayerplug-in-3.25-binary.tar.gz than extracted that ran 
sudo dpkg -i mozilla-mplayer_3.25-1ubuntu2_amd64.deb

I got a Y/N/O, ubnch of optins, selected the default option (I tihnk N) , same results, tried installing again, no options, tried CNN again, no luck, for my 32bit firefox, same result as before, *hurumph!*

As for k9copy, I tried it earlier but I don't see an option to create an ISO to make another DVD out of, just conversion to DIvx and such, I'll have to try some faq's.

---

### Post by Kilz on 2006-08-05
just to make sure we are on the same page. [This is k9copy]("http://k9copy.sourceforge.net/"). I dont see the convert to divx, there is an output device selector. You can chose your burner, or an iso file.

---

### Post by LinuxConvertJune2006 on 2006-08-05
Yeah my bad, I worded that incorrectly. What I meant, does it shrink to 4.7 GB automatically? I'll look into it, but it does detect my DVD's and seem to launch, I just have to start testing this stuff out.

On a side note, still no luck with WMV plugin (mplayer). I can download WMV files and play them fine, yahoo sports and cnn WMV plugins have audio but no video, very odd.

---

### Post by LinuxConvertJune2006 on 2006-08-05
I fixed the plugin issue , i didn't copy /usr/bin/mplayer32 and overwrite /usr/bin/mplayer , once I did that it worked fine. It was in that thread I just didn't do it!

Woohoo!

So far I haven't run into anything to prevent me from using 64bit version, just these plugins are a hassle, and that sn't Ubuntu or GNU/Linux's fault at all.

64bit Windows XP Pro wasn't even nearly as good as Ubuntu, lots of drivers issues.

Now if I can only get the autmount of my DVD's to be more frequent..I think thats a hardware issue, since on my 32bit Ubuntu box the same thing occured, and on my other Ubuntu box, the DVD automounts all the time with any DVD.

---

