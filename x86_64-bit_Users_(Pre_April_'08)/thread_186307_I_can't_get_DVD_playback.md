---
title: "I can't get DVD playback"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by jjf on 2006-06-01
I go through this crap every fresh linux install, but usually after an hour of tinkering I've got DVD playback.  No luck this time with my AMD64 that I just installed Dapper LTS on.

I've installed libdvdcss2 by downloading and installing a .deb for the amd64 from somebody's website.  

I still can't get VLC to do anything.  The "open disc" option doesn't work.  If I try to "open a file" and choose files inside the "video_ts" folder it just hangs.

I've tried totem-xine, totem-gstreamer, xine, and mplayer.  None of them will play a DVD.  I'm extremely frustrated right now, especially because to watch King Kong tonight I'll just have to boot into Windows where VLC actually #$*@# works.  

I've searched these forums and have tried a variety of different things that people say work for them, and then put an annoying little smiley like it's all cheery and it ought to work for everybody if they'd just recompile totem with a xine backend or whatever.

Sorry for my tone, I'm just blowing a little steam.  Really if anybody could give a just-barely-above-noob some help with this, I'd really appreciate it.  Thanks.

---

### Post by BoyOfDestiny on 2006-06-01
[QUOTE=jjf]I go through this crap every fresh linux install, but usually after an hour of tinkering I've got DVD playback.  No luck this time with my AMD64 that I just installed Dapper LTS on.

I've installed libdvdcss2 by downloading and installing a .deb for the amd64 from somebody's website.  

I still can't get VLC to do anything.  The "open disc" option doesn't work.  If I try to "open a file" and choose files inside the "video_ts" folder it just hangs.

I've tried totem-xine, totem-gstreamer, xine, and mplayer.  None of them will play a DVD.  I'm extremely frustrated right now, especially because to watch King Kong tonight I'll just have to boot into Windows where VLC actually #$*@# works.  

I've searched these forums and have tried a variety of different things that people say work for them, and then put an annoying little smiley like it's all cheery and it ought to work for everybody if they'd just recompile totem with a xine backend or whatever.

Sorry for my tone, I'm just blowing a little steam.  Really if anybody could give a just-barely-above-noob some help with this, I'd really appreciate it.  Thanks.[/QUOTE]

I wouldn't trust misc repos... I'd say you should un-install the decss.deb you got, just in case it conflicts with these steps...

Anyway, no worries, I've got DVD playback no problem.

With universe and multiverse enabled (I guess you do already), grab everything with gstreamer.10 in it (minus the documentation and -dev). 

Then (make sure you have closed synaptic after updating), and from a terminal run

**sudo /usr/share/doc/libdvdread3/examples/install-css.sh**

Pop in a DVD and enjoy. Should just launch with totem (I recommend sticking with totem-gstreamer, actually works for me in dapper.) I no longer dislike totem. :)

EDIT: I realized I put the smiley... Anyway, it does work, and isn't hard to do. Sucessfully tested on 3 dapper boxes (although 1 of which is 64-bit)

---

### Post by feight on 2006-06-02
Don't forget you need build-essential, gcc, etc. before running the script for it to work. These programs aren't installed by default. Pay attention to the packages it suggests you install before hitting enter, if you didn't install them yourself hit ctrl-c and install them.

---

### Post by jjf on 2006-06-03
Thanks for the help; I did get it working.  I nuked my AMD64 install and went with the i386.  Then I installed 

- build-essential
- everything gstreamer.10 (except anything that said -doc)

and used easyubuntu to get the latest libdvdcss2.  One thing that gave me a little frustration for a while was that I left a DVD in the drive to test.  Totem continued to tell me it couldn't read the DVD.  I had to remove and reinsert the DVD before it would play.  Apparently when you first pop the DVD in (and not when you hit "play"), Ubuntu decides whether it can decode it or not.

Thanks again.

---

### Post by modestmelody on 2006-06-03
How did you get VLC to install in Dapper?  I keep getting this in synaptic:
vlc:
 Depends: libdbus-1-1 but it is not going to be installed
 Depends: wxvlc but it is not going to be installed

---

### Post by henriquemaia on 2006-06-04
[quote=modestmelody]How did you get VLC to install in Dapper?  I keep getting this in synaptic:
vlc:
 Depends: libdbus-1-1 but it is not going to be installed
 Depends: wxvlc but it is not going to be installed[/quote]

Post your sources.list so we can find out what the problem is.

Do:

```
gedit /etc/apt/sources.list
```

---

