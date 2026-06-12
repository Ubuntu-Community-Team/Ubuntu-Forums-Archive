---
title: "Alsa 1.0.14 64-bit - lib32asound required to fix skype / flash etc"
date: 2007-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by drplix on 2007-07-16
I have a new HP 6715b laptop with SoundMax/Azalia (Analog Devices AD1981) soundcard.  I'm running 64-bit Feisty.

The problem:  The default Feisty install detects this card and plays audio but will not record.  I need recording for VoIP (skype). I have dug around and it seems that the latest final Alsa 1.0.14 driver release is needed for this sound chip.   I have compiled and installed Alsa 1.0.14 by hand and now have a fully working soundcard (hurrah!).  However, I still have the default lib32asound v1.0.13 - but this library has to be updated for legacy 32bit apps to work (skype and flash audio is now broken (boo!)) [see this gentoo thread...[http://forums.gentoo.org/viewtopic-p-3806961-highlight-.html?sid=40255cb5c9f7f2ab93ae4592246e100e]](http://forums.gentoo.org/viewtopic-p-3806961-highlight-.html?sid=40255cb5c9f7f2ab93ae4592246e100e])

Question:  Does anybody know where/how I can get official deb packages for Alsa 1.0.14 64bit and the compatibility lib32asound 1.0.14?

Alternatively:  I have the alsa source but how do I compile libasound as 32 bit?

All help appreciated.  I am soooo close to fixing my sound problems!

Incidentally I think this might be part of the answer to some of the questions on the skype forum about 64bit ubuntu...[http://forum.skype.com/index.php?showtopic=88916](http://forum.skype.com/index.php?showtopic=88916)

---

### Post by Kilz on 2007-07-16
> **drplix said:**
> I have a new HP 6715b laptop with SoundMax/Azalia (Analog Devices AD1981) soundcard.  I'm running 64-bit Feisty.

The problem:  The default Feisty install detects this card and plays audio but will not record.  I need recording for VoIP (skype). I have dug around and it seems that the latest final Alsa 1.0.14 driver release is needed for this sound chip.   I have compiled and installed Alsa 1.0.14 by hand and now have a fully working soundcard (hurrah!).  However, I still have the default lib32asound v1.0.13 - but this library has to be updated for legacy 32bit apps to work (skype and flash audio is now broken (boo!)) [see this gentoo thread...[http://forums.gentoo.org/viewtopic-p-3806961-highlight-.html?sid=40255cb5c9f7f2ab93ae4592246e100e]](http://forums.gentoo.org/viewtopic-p-3806961-highlight-.html?sid=40255cb5c9f7f2ab93ae4592246e100e])

Question:  Does anybody know where/how I can get official deb packages for Alsa 1.0.14 64bit and the compatibility lib32asound 1.0.14?

Alternatively:  I have the alsa source but how do I compile libasound as 32 bit?

All help appreciated.  I am soooo close to fixing my sound problems!

Incidentally I think this might be part of the answer to some of the questions on the skype forum about 64bit ubuntu...[http://forum.skype.com/index.php?showtopic=88916](http://forum.skype.com/index.php?showtopic=88916)

[Have you tried a Gutsy package]("http://packages.ubuntu.com/gutsy/libs/lib32asound2")?

---

### Post by drplix on 2007-07-16
Yes I tried these.  But I get dependency failures. I'm new to Ubuntu (debian distros) I came from Open Suse so I'm not sure how to go about using the forward packages safely on Feisty.

Thanks for the suggestion!

---

### Post by drplix on 2007-07-18
I fixed my skype by compiling a 32 bit version of latest 1.0.14 alsa.  Briefly if you want to compile a library to 32bit when on the 64bit platform

1) Install libc6-dev-i386
2) Use .configure like...

> 
./configure --prefix=/home/your-home-here/root \
   LDFLAGS="-L/emul/linux/x86/usr/lib -m32" \
   CFLAGS="-L/emul/linux/x86/usr/lib -m32" 



Detailed instructions for the alsa lib are available here...

[http://gentoo-wiki.com/HOWTO_ALSA_and_TeamSpeak_on_amd64](http://gentoo-wiki.com/HOWTO_ALSA_and_TeamSpeak_on_amd64)

---

### Post by seanX on 2007-07-28
> **drplix said:**
> I fixed my skype by compiling a 32 bit version of latest 1.0.14 alsa.  Briefly if you want to compile a library to 32bit when on the 64bit platform

1) Install libc6-dev-i386
2) Use .configure like...




Detailed instructions for the alsa lib are available here...

[http://gentoo-wiki.com/HOWTO_ALSA_and_TeamSpeak_on_amd64](http://gentoo-wiki.com/HOWTO_ALSA_and_TeamSpeak_on_amd64)

Thanks.  This worked for me.  :).  Now I have sound in Adobe Flash in my 64-bit Firefox
setup.

I had to copy the resultant 32-bit libasound.so.2.0.0 file to the /usr/lib32/ directory
on my system.

To make a long story short, what happened a few days ago is snd-hda-intel 
sound cards stopped working with the latest Automated Ubuntu Updates (I think
there's a recent thread about this).  I had no sound on my system until I rebuilt the 
alsa-lib, alsa-utils, and alsa-driver from a slightly older version of the source.  This 
build was for 64-bit by default of course.

That let me have sound on my system, but Adobe Flash would not play any sound
since of course, I'm using a 32-bit plugin with nspluginwrapper (courtesy of the members
of this forum).  So, I had to rebuild just the alsa-lib source with the ./configure options quoted 
above.

I then copied the resultant 32-bit libasound.so.2.0.0 from ~/root/lib/ to /usr/lib32/ 
(overwriting any versions that were already there).

That fixed the sound in Adobe Flash while using nspluginwrapper with 64-bit Firefox.

Oh, by the way, don't try to copy the resultant 32-bit file into the /usr/lib/ directory (which
contains 64-bit libraries).  That'll screw up the sound on your system and cause many other 
problems.

Now, onto the next challenge... Installing and Configuring Beryl. :)  I'll probably be looking on this forum for help on that.

---

