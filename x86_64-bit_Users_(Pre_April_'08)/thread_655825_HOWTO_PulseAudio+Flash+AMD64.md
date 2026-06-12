---
title: "HOWTO: PulseAudio+Flash+AMD64"
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nuke Skyjumper on 2008-01-01
This post assumes that you already have Flash working under 64bit Firefox with nspluginwrapper on Ubuntu 7.10 Gutsy AMD64

So after a few hours of searching only to find a few "it works for me" posts without enough detail, and plenty of "it's not working" posts, I got finally got it working myself.

What you need is libflashsupport.so that knows to load the 32bit PulseAudio client libraries (had to modify it to do that), and the 32bit PulseAudio libraries themselves. Also needed was a 32bit libcap that PulseAudio depended on.

Modified packages are here:
[lib32cap1_1.10-14build1_amd64.deb]("http://nuklear.org/packages/lib32cap1_1.10-14build1_amd64.deb")
[lib32pulse0_0.9.6-1ubuntu2_amd64.deb]("http://nuklear.org/packages/lib32pulse0_0.9.6-1ubuntu2_amd64.deb")
[libflashsupport_1.0~2219-1_amd64.deb]("http://nuklear.org/packages/libflashsupport_1.0~2219-1_amd64.deb")

You should be able to just install these, restart firefox, and have Flash play sound via PulseAudio. Good Luck.

---

### Post by timeoff on 2008-01-02
Worked for me. Thanks....

---

### Post by Cappy on 2008-01-02
Where is the source code?

Did you build this from [http://pulseaudio.revolutionlinux.com/PulseAudio](http://pulseaudio.revolutionlinux.com/PulseAudio) ?

---

### Post by Nuke Skyjumper on 2008-01-04
> Did you build this from [http://pulseaudio.revolutionlinux.com/PulseAudio](http://pulseaudio.revolutionlinux.com/PulseAudio) ? 

Yeah, it's just the debian package from [http://pulseaudio.vdbonline.net/libflashsupport/](http://pulseaudio.vdbonline.net/libflashsupport/) modified to look in /usr/lib32, and compiled for 32bit.

---

### Post by helliewm on 2008-01-05
Brilliant thanks for posting this in the forum extremely useful. Works for me superbly. NOw to the the same to my 2 laptops.

Helen

---

### Post by helliewm on 2008-01-06
The web site with these debs on is now down. I wanted to put it on my laptop too.

Helen

---

### Post by Ender27182818 on 2008-01-10
Worked for me, thanks a ton for making this!

---

### Post by ~LoKe on 2008-01-10
Finally, PulseAudio works universally for me.  Thanks!

Next step is to threaten PA to support passthrough. ;)

---

### Post by dudeskeeroo on 2008-01-14
Freakin' sweet.  \\:D/This works like a charm...and like you, I had searched high and low without getting anything concrete (apart from failure tales) ](*,).  After spending most of the day on it I thought I would have to get the source myself. 

You have saved me a fair chunk-o-effort (but now I'll waste that time on Youtube!) 

Cheers! =D>

---

### Post by izm81 on 2008-01-27
AWESOME.  Thank you.  You've made this process SO much easier.  :)

Just a note for anyone if it doesn't work initially, uninstall those three packages, close ur browsers, and try installing them again.  That's what happened with my setup; I'm guessing I had a partially installed (non-working) solution the first time when I tried this.  uninstalling and re-installing worked.

Thanks again!

---

### Post by jkzubu on 2008-01-29
My post.

[http://ubuntuforums.org/showthread.php?p=4232211#post4232211](http://ubuntuforums.org/showthread.php?p=4232211#post4232211)

Thanks Nuke!

Solved the problem.  All of my sound is working.

JK

---

### Post by Nuke Skyjumper on 2008-02-17
I've been updating my Gutsy system with packages from Hardy, which recently broke audio in flash again. To fix this, you need to **remove** the lib32pulse0 package that you downloaded from this thread. Hardy now provides this in the ia32-libs package itself. You will also need an up to date libflashsupport, built for Hardy's updated pulseaudio:

[libflashsupport_svn20080217.deb]("http://nuklear.org/packages/libflashsupport_svn20080217.deb")

I built this from a subversion snapshot, but it works just fine. Hope this helps.

---

### Post by macross3003 on 2008-03-09
> **Nuke Skyjumper said:**
> I've been updating my Gutsy system with packages from Hardy, which recently broke audio in flash again. To fix this, you need to **remove** the lib32pulse0 package that you downloaded from this thread. Hardy now provides this in the ia32-libs package itself. You will also need an up to date libflashsupport, built for Hardy's updated pulseaudio:

[libflashsupport_svn20080217.deb]("http://nuklear.org/packages/libflashsupport_svn20080217.deb")

I built this from a subversion snapshot, but it works just fine. Hope this helps.

It works :D :guitar:
Thanks a lot

---

### Post by Mr_Ada on 2008-03-09
Thank you thank you thank you!!!!!

I can now hear on YouTube!!!!

I also had to go here:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

reboot and viola!

chris

---

### Post by Mr_Ada on 2008-03-09
I spoke too soon!!!  Argggg.  Now audacity won't play anything or record anything.


chris


Now Youtube is complaining about javascript or needing a plugin.  This is getting so old.

---

### Post by Redptc on 2008-03-12
I have been able to set up pulse audio and everything goes fine except for flash audio in firefox. I followed the instructions provided in the Ubuntu/Wiki.

I also know that my answer re Flash is right hear in this thread, but....I don't have AMD64 and I know very little about terminal commands.

Oops, looks like I bumbled my way through and finally got it to work! Thanks.

---

### Post by KhaaL on 2008-03-30
I envy everyone else in this thread, because for me flash videos still hangs after 2 seconds into the video... even  wtih the libflashsupport_svn20080217.deb package. 

I must have some really bad karma to make PA hate me this much

EDIT: I'm making progress in my search for what makes the sound FUBAR. seems like xine and amarok really dosen't go well with pulseaudio...

---

### Post by Washer on 2008-04-18
> **izm81 said:**
> AWESOME.  Thank you.  You've made this process SO much easier.  :)

Just a note for anyone if it doesn't work initially, uninstall those three packages, close ur browsers, and try installing them again.  That's what happened with my setup; I'm guessing I had a partially installed (non-working) solution the first time when I tried this.  uninstalling and re-installing worked.

Thanks again!this actually worked for me. I didn't believe it would. Thanks!

---

### Post by boekebaas on 2008-04-22
I've tried the main solution posted in this topic. Flashplayer with nspluginwrapper works fine, however, no sound at all. I have no problems with other sound related software (amarok, totem, vlc). I run ALSA and my soundcard is NVIDIA HDA (on motherboard). 

> **izm81 said:**
> Just a note for anyone if it doesn't work initially, uninstall those three packages, close ur browsers, and try installing them again.  ... uninstalling and re-installing worked.

I also did this... no effect.

> **Mr_Ada said:**
> Thank you thank you thank you!!!!!

I can now hear on YouTube!!!!

I also had to go here:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

reboot and viola!



I've also installed other pulse audio files as explained in the link above. After installation all sound in Ubuntu Gutsy stopped working and still no sound from flash (in some forums the opposite is reported: no more sound, except in flash). Not until deinstalling the same pulse audio files I had everything back on track ~ yet still no sound in flashplayer. What output/info of my system can I post to get some help? I'd really appreciate some guidance. thanks

---

### Post by SilverWave on 2008-04-27
Thanks guys this thread helped me trouble shoot my PulseAudio problems.

I had no sound in Totem if I left the "Sound" at autodetect.
Setting to ASLA worked for Totem but not Firefox flash.

Installed the tools and followed the instructions from here:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

started PulseAudio appelet and had a look around - found that the default device was my USB skype phone!

If I listened in on the phone I could hear the flash from the bbc iplayer in firefox!!!

Couldn't find a quick way to change the default device but for the time being just pulled the USB phone.

Rebooted all working including flash!

:)

Note1:
I didn't do this bit:
    *      Checkmark all three options under Network Access. 
    *      Checkmark Enable Multicast/RTP Receiver. 
    *      Checkmark EnableMulticast/RTP Sender. 
Note2:
I installed restricted drivers and libflashsupport.
(Then uninstalled and reinstalled and mucked about until I found the above work around).

Cheers!

---

### Post by KillaKurt on 2008-05-01
Hi uber-n00b here...I'm using 64-bit Gutsy and cannot get sound to work with flash.

I have two questions.  First one is...how do I set Firefox to use this PulseAudio??

I got the video to work but I'm not getting any sound.  Will the above .debs even work for me on 64-bit?

The nspluginwrapper DID uninstall my other flash plugins (nonfree + gnash).

Any info you need from terminal for this?  Please help, I want to get Rick Roll'd!! lol

---

### Post by Wolfygr on 2008-05-03
> **Nuke Skyjumper said:**
> I've been updating my Gutsy system with packages from Hardy, which recently broke audio in flash again. To fix this, you need to **remove** the lib32pulse0 package that you downloaded from this thread. Hardy now provides this in the ia32-libs package itself. You will also need an up to date libflashsupport, built for Hardy's updated pulseaudio:

[libflashsupport_svn20080217.deb]("http://nuklear.org/packages/libflashsupport_svn20080217.deb")

I built this from a subversion snapshot, but it works just fine. Hope this helps.

That worked for me!
Thanks a lot! :)

---

### Post by luke16 on 2008-05-26
The lib32cap1 won't install for me. 

I get this:

(Reading database ... 117919 files and directories currently installed.)
Unpacking lib32cap1 (from .../lib32cap1_1.10-14build1_amd64.deb) ...
dpkg: error processing /tmp/lib32cap1_1.10-14build1_amd64.deb (--install):
 trying to overwrite `/lib32/libcap.so.1.10', which is also in package ia32-libs
Errors were encountered while processing:
 /tmp/lib32cap1_1.10-14build1_amd64.deb

I tried manually removing that, but it still wouldn't work.

EDIT: I have it working, thanks to removing then reinstalling with firefox closed. This is without the first 2 packages installed, only installing the third one seems to have worked for me.

---

### Post by DerPflanz on 2008-06-03
I have the feeling I tried it all. To no avail. The cleanest I can get is this:

. uninstall all the .debs mentioned in the first post
. re-install ia32-libs (using synaptic)
. install the svn libflashsupport from this thread
. install the lib32cap1 from the first post (using --force-all, because it want to overwrite some files).
. all of the above with firefox closed.

Result: nothing. no sound in my flash.

---

### Post by luke16 on 2008-06-03
> **DerPflanz said:**
> I have the feeling I tried it all. To no avail. The cleanest I can get is this:

. uninstall all the .debs mentioned in the first post
. re-install ia32-libs (using synaptic)
. install the svn libflashsupport from this thread
. install the lib32cap1 from the first post (using --force-all, because it want to overwrite some files).
. all of the above with firefox closed.

Result: nothing. no sound in my flash.

I forgot to mention that I am using alsa instead of pulse, as alsa seems to work better and have better compatibility. This is probably why I didn't need to mess with the first two files. You might try it with alsa to see if it's just not working with pulse, or just not working period.

---

### Post by DerPflanz on 2008-06-04
As I understood it, Pulse is running on top of ALSA as the sound server, replacing esd.

---

### Post by Shakaboom on 2008-06-13
The first package needed failed to install. It got stuck on "Reading database...." Does that have to do with the post above that the server is down or something?

Please help, i've been trying for ages to get the sound of youtube and myspace to work on my hardy 64 bit (OSS, not ALSA, as i have Creative X-fi card)

---

