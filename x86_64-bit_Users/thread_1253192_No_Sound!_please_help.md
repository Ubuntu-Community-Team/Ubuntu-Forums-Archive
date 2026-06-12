---
title: "No Sound! please help"
date: 2009-08-29
forum: x86 64-bit Users
---

### Post by kazneus on 2009-08-29
I just installed jaunty on my new computer and there's no sound: speakers or headphones. Please help me. I'm new to linux but I'm so fed up with windows... If I can't get sound working I'm going to have to go back to XP (buuuuuhh...)

---

### Post by sailthesea on 2009-08-29
You could be missing some of the media support package Try in Synaptic or:
Open a terminal in Applications > Accessories
and copy/paste these 3 lines

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

This normally gets everything into place
Good Luck! And welcome:)

---

### Post by kazneus on 2009-08-29
Thanks very much for the help, but this did not work. everything seemed to run fine but I got the message: 'E: Couldn't find package gstreamer0.10-pitfdll' at the end of the last script. Still no sound : (
maybe there is another way? My computer is a laptop: the sound card is ATI Technologies Inc SBx00 Azalia (Intel HDA) if that helps.

---

### Post by sailthesea on 2009-08-29
OK this may help 
System > Administration > Synaptic Package manager
Look in multimedia and see if you can find anything relating to your audio card Try installing those
The fix in my last post was a bit out of date Sorry

---

### Post by sailthesea on 2009-08-29
There is also this link

[http://linuxpoison.blogspot.com/2009/04/multimedia-support-in-ubuntu-904-jaunty.html](http://linuxpoison.blogspot.com/2009/04/multimedia-support-in-ubuntu-904-jaunty.html)

 Generally ubuntu doesn't come with multimedia codecs installed you have get them yourself(legal issue)
 There are some good stickies in the forums to help you But they are hard to find because the UCF search engine is errrmm not that great 
Google the site itself for better results

---

### Post by kazneus on 2009-08-29
So I did as you suggested, but still no sound. The good news is flash runs pretty well now and I learned about all the programs available through synaptic package manager. Is there anything else you can think of to try?

Thanks again

---

### Post by sailthesea on 2009-08-30
Hello there Boy that was a LONG day at work!
Hows it going?

Any audio yet? Its sounds like your card is not natively supported in ubuntu
Try System>admin>hardware drivers see what comes up If you need a restricted driver you will probably need to find and download it Not something I ever enjoyed having to do:(
Post your results and also your hardware specs and lets get to the bottom of this!:)

---

### Post by kazneus on 2009-08-30
so yeah I followed everything on the Comprehensive Sound Problem Solutions Guide sticky to the letter ( I'm pretty sure) and installed the driver for Intel HDA. The full name of my soundcard is ATI Technologies Inc SBx00 Azalia (Intel HDA) - or at least that's what was listed when I put 'aplay -l' then 'lspci -v' into the terminal. My processor is AMD Turion x2 dual core mobile RM-74, and I've got about 3 gigs of ram. the Kernel is 2.6.28-15-generic

Thanks again for helping me out. It's been a steep learning curve on Ubuntu trouble shooting procedure, but I've learned a lot. I'm quite taken with the Linux community - somebody from the UK I've never met is taking the time to help out a newbie all the way in america (central pennsylvania).

---

### Post by Yellow Pasque on 2009-08-31
You might want to try upgrading ALSA with this script. [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by Nz! on 2009-08-31
I have the same problem, and none of the solutions posted here helped me.

Thank you.:P

---

### Post by sailthesea on 2009-08-31
I just thought does everyone have the volume UP?

---

### Post by sailthesea on 2009-09-01
Any joy you guys? 
A bump on this while I see if there is any more info

---

### Post by garvinrick4 on 2009-09-02
Just in case you did install ubuntu restricted extra's.
Sounds like everything working except sound in video's flash and such.

Just in case.

---

### Post by ApEkV2 on 2009-09-02
".....in america (central pennsylvania)"

central PA

i live there tooooooo

@ Nz! try gstreamer-properties in the terminal if it pops up, try changing the "Audio" "default output" to ALSA (if you have ALSA installed) then select your output device (might have to restart the comp afterwards).

If that doesn't work be sure to redo the options you change back to default (usually autodetect).

---

### Post by mmdmurphy on 2009-09-03
I always hated the "me too" posts, and so, here I am. "me too". I have ubuntu 64 Jaunty installed on an HP elite e9180f. 9 gigs of ram, 8 core, everything WAS running fine. I triple boot, and all worked. I booted to linux last night, it said updates were available, I installed them, and I rebooted. 
When it came back up, well, I have sound, but not "sound" more like noise. Sounds like a bad ground wire, or that noise you get when you plug in speakers with the computer running - but very quiet. Rebooted to Vista 64, and everything is fine = NOT a hardware issue. How can I "undo" this?:confused:

---

### Post by chrism66 on 2009-09-03
"Me Too" Just upgraded my desktop to Jaunty and no sound at all spent better part of last night and today trying to get it too work.

---

