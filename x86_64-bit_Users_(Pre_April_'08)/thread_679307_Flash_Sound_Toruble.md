---
title: "Flash Sound Toruble"
date: 2008-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by jkzubu on 2008-01-26
I am re-posting this in the 64-bit forum.

I am running Ubuntu 7.10, AMD64-bit version and I am using Pulse Audio. My sound card is an Audigy SoundBlaster SE. This morning I installed the flash fix: flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb, as described in this post: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397).

This fix seems to have gotten the video portion of flash to work, but there is no audio for the videos in: Youtube, Yahoo and a few other websites I tested. Also, my audio for the login screen (bongo drums) no longer functions. The rest of my audio works beautifully: music in Audacious, Exaile, Rythmbox, even the system sounds (clicks, beeps, boings, etc.). Prior to installing this fix, flash would rarely work perfecly (with sound), would sometimes partially work, but mostly would never work. Especially, yahoo videos would never work. The flash fix seems to be working ok for video, but there is no audio.

I found this code:
mv ~/.asoundrc .asoundrc.old
mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old
in post #4 of this thread: [http://ubuntuforums.org/showthread.p...ox+pulse+audio](http://ubuntuforums.org/showthread.p...ox+pulse+audio)
and ran it in a terminal.

After a restart, all of my audio (and video) worked perfectly in flash videos (Youtube, Yahoo, etc.), but the rest of my audio stopped working (couldnt find the audio source or something). I was able to reset the audio using asoundconf, but now the audio portion of the flash videos is gone again (video still working) and the rest of my audio is back working to the way I described it above. I understand that there are known bugs with Flash and AMD64-bit, but I also know that all of the sound will work. It just appears that all of the sound will not work together...yet.

Can someone please answer the following:
What exactly are the mv scripts above doing?
Why do these scripts activate the flash audio and deactivate the other audio (for music and etc).
How can I get all of the sound to play nice together and make everything work?

Thank you.

JK

---

### Post by Kilz on 2008-01-26
The mv command is for moving or renaming files. The commands are for renaming 2 files. They rename setting files. These files would be remade as soon as the application they are used for started again. This is a common way to fix corrupted setting files.

---

### Post by jkzubu on 2008-01-28
Hi Kilz-

Thanks for your input.  I have read some of your other posts and find it to be great stuff.  Thanks for that, too.

I guess I was understanding that the mv command overwrites a file.  After a bit more thought, I suppose I should have been more specific, in that, what might be contained in the file that is over-written that allows sound to play in flash, but stop sound from working in my other applications?  And visa-versa; if all my other sound works then why not flash?

As I mentioned, the most persistent problem I am having with my new build based on the AMDx2 and the 64-bit OS has been with Flash and/or sound or both.  Well, after a bit more reading, this Adobe link: [http://www.adobe.com/products/flashplayer/productinfo/systemreqs/](http://www.adobe.com/products/flashplayer/productinfo/systemreqs/)
may have part of the answer.  Toward the bottom of the page reads, "Only Advanced Linux Sound Architecture (ALSA) is supported (OSS/ESD will not play audio; audio will silently fail). Only GTK2-based browser versions are supported."

...Hmm exactly?  Do you think that because I am running Pulse Audio, herein lies part of the explanation to my problem?  I do have Alsa installed, but I have PA selected as the sound system.  Is it possible for me to use Pulse Audio as my main sound system AND pipe Alsa for use in Firefox with Flash?  If yes, then do you know how this can be done?  I like PA because I can use the system sounds, which I don't believe work otherwise.

Thanks.

JK

---

### Post by Kilz on 2008-01-29
> **jkzubu said:**
> Hi Kilz-

Thanks for your input.  I have read some of your other posts and find it to be great stuff.  Thanks for that, too.

I guess I was understanding that the mv command overwrites a file.  After a bit more thought, I suppose I should have been more specific, in that, what might be contained in the file that is over-written that allows sound to play in flash, but stop sound from working in my other applications?  And visa-versa; if all my other sound works then why not flash?

As I mentioned, the most persistent problem I am having with my new build based on the AMDx2 and the 64-bit OS has been with Flash and/or sound or both.  Well, after a bit more reading, this Adobe link: [http://www.adobe.com/products/flashplayer/productinfo/systemreqs/](http://www.adobe.com/products/flashplayer/productinfo/systemreqs/)
may have part of the answer.  Toward the bottom of the page reads, "Only Advanced Linux Sound Architecture (ALSA) is supported (OSS/ESD will not play audio; audio will silently fail). Only GTK2-based browser versions are supported."

...Hmm exactly?  Do you think that because I am running Pulse Audio, herein lies part of the explanation to my problem?  I do have Alsa installed, but I have PA selected as the sound system.  Is it possible for me to use Pulse Audio as my main sound system AND pipe Alsa for use in Firefox with Flash?  If yes, then do you know how this can be done?  I like PA because I can use the system sounds, which I don't believe work otherwise.

Thanks.

JK

I dont quite know whats in the files other than settings. They are not on my computer. I can tell they are settings by the location.
[This file might help you.]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb")

---

### Post by Yellow Pasque on 2008-01-29
See this thread:
[http://ubuntuforums.org/showthread.php?t=655825](http://ubuntuforums.org/showthread.php?t=655825)

---

### Post by jkzubu on 2008-01-29
Beautiful, Beautiful, Beautiful.  Thanks Temüjin, That appears to have solved the problem.

JK

---

### Post by Kilz on 2008-01-29
Thank You Temüjin, I have added the link to my nspluginwrapper thread. Currently stickied thanks to Artificial Intelligence.

---

### Post by elliio on 2008-03-30
Thank You all SO MUCH!!!

Get some :popcorn:Popcorn... I'm about to blither on...

Currently running a clean install of xubuntu 7.10 Gutsy amd64 via alternate installer, + xubuntu team PPA to dist-upgrade to Xfce 4.4.2, +Flash-Player-Nonfree, + PulseAudio, + all the patched debs from Hardy...

The only thing left is to set up MPD + ((Xfmpc & Sonata) to compare)

if anyone on xubuntu amd64 needs help with the above setup, i archived my bookmarks, and could provide the links and whatnot if you need them.

I'm logging off to do a partimage via SystemRescueCD-1.0.0 (GREAT TOOL) [www.sysresccd.org](www.sysresccd.org) (try it)

BACK-UP BACK-UP and do your BACKUPS!!! :-)

ESPECIALLY when you get a golden snapshot of your WORKING GNU/Linux/<insert DE/WM here> setup....

I'm new to Linux and have been mucking up my setups and doing horrible things like granting myself root access rw to /usr and generally destroying my installs, until I finally caught on to SystemRescueCD and some basics of the command line and (x)ubuntu and ubuntu/GNOME before that.

What a rolllercoaster ride with the modern system and bleeding edge hardware with ATI proprietary drivers, AIGLX or Xgl (tried em both), Compiz-Fusion (on both ubuntu and xubuntu), and generally running my box as cavalier-ly as a Windows Power User (ahem! *face red*) I am learning my lesson.

AGAIN, THANK YOU ALL, having lotso RAM with amd64, AND working Flash plugin AND next-gen sound is TOO SWEET! Robyn sounds really good from YouTube! hehehe....

-elliio out!

:popcorn:

---

