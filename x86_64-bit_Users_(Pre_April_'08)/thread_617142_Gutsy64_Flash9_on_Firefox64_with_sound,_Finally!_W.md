---
title: "Gutsy64 Flash9 on Firefox64 with sound, Finally! With PulseAudio!!!"
date: 2007-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sabaki on 2007-11-19
After weeks of tortuous aggravation I finally got Flash working *with audio* on the 64-bit version of Firefox and Swiftweasel on Gutsy64!  Woohoo!
:guitar:

According to the 'knowledgeable', all I should have needed to do is install flashplugin-nonfree, which will automatically install nspluginwrapper and everything should work.

If only it did!!!

This is/was a clean 'Gutsy 64' installation, not an upgrade.

The Flash video displayed properly but there was no audio at all when playing any flash video.

I repeat, this is for Ubuntu64 with the 64-bit Firefox and/or 64-bit Swiftweasel with the flashplugin-nonfree installed. This is not Feisty and not Firefox32 and not Gnash.

I think I tried *everything*!!! Every suggestion... reinstalling flashplugin-nonfree, reinstalling alsa,  every environment variable, such as setting /etc/firefox/firefoxrc to FIREFOX_DSP="aoss", and FIREFOX_DSP="alsa", and starting Firefox with  'aoss firefox', and  etc., etc. and none of these suggestions worked for me.

Now I don't know how many people have had problems with Flash audio not working, but here are just a few of the posts and bug reports I've studied in trying to get it to work:

x86 64-bit Users: Please Help- Gutsy_64 Flash Audio Broken!
[http://ubuntuforums.org/showthread.php?t=601410](http://ubuntuforums.org/showthread.php?t=601410)

x86 64-bit Users: Alsa 1.0.14 64-bit - lib32asound required to fix skype / flash etc
[http://ubuntuforums.org/showthread.php?t=502377](http://ubuntuforums.org/showthread.php?t=502377)

x86 64-bit Users: Sound in firefox64
[http://ubuntuforums.org/showthread.php?t=445022](http://ubuntuforums.org/showthread.php?t=445022)

x86 64-bit Users: Firefox32, flash and pulseaudio
[http://ubuntuforums.org/showthread.php?t=460549&highlight=flash+audio](http://ubuntuforums.org/showthread.php?t=460549&highlight=flash+audio)

x86 64-bit Users: Playing sound from a 32bit app on a 64bit system with pulse
[http://ubuntuforums.org/showthread.php?t=486634](http://ubuntuforums.org/showthread.php?t=486634)

Here's some bug reports on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/153742](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/153742)

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/151849](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/151849)

Gutsy_64 Flash Audio Broken
[https://bugs.launchpad.net/ubuntu/+bug/159755](https://bugs.launchpad.net/ubuntu/+bug/159755)

Here's the thread that got me to try PulseAudio to try to solve this:
Gutsy Firefox Flash no sound  (it says [SOLVED] ... but not for me yet.
[http://ubuntuforums.org/showthread.php?t=590989](http://ubuntuforums.org/showthread.php?t=590989)

There are a whole bunch of threads on this in the Multimedia and Video forums, too. Here's a few:

Multimedia & Video: Flash no Sound - 7.10
[http://ubuntuforums.org/showthread.php?t=583995](http://ubuntuforums.org/showthread.php?t=583995)

Multimedia & Video: VLC and Flash audio not working
[http://ubuntuforums.org/showthread.php?t=602038](http://ubuntuforums.org/showthread.php?t=602038)

Another one "SOLVED"
Multimedia & Video: [SOLVED] firefox no sound
[http://ubuntuforums.org/showthread.php?t=598422](http://ubuntuforums.org/showthread.php?t=598422)

And this thread pointed me to another site...
Multimedia & Video: solution for no sound in Firefox flash
[http://ubuntuforums.org/showthread.php?t=600306](http://ubuntuforums.org/showthread.php?t=600306)
pointed to:
[http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/)
This didn't work for me either.

And maybe related, although for Gutsy32:
Multimedia & Video: Installed Amarok into Gutsy32, it killed my flash player sound...
[http://ubuntuforums.org/showthread.php?t=599091](http://ubuntuforums.org/showthread.php?t=599091)

And here's more folks posting about what sounds like the same problem:
Multimedia & Video: Youtube audio not working....
[http://ubuntuforums.org/showthread.php?t=330766](http://ubuntuforums.org/showthread.php?t=330766)

And another thread with 'picture but no sound'
Multimedia & Video: Adobe Flash not working in Firefox (Gutsy)
[http://ubuntuforums.org/showthread.php?t=588464](http://ubuntuforums.org/showthread.php?t=588464)


Ok, so it wasn't just me and my computer. I'm not sure how universal this bug has been but here, in a nutshell, is what I had to do to get it to work.

For better or for worse, I went the PulseAudio route.

I installed all the PulseAudio packages and configured everything I could to use it. I have had trouble with ESD off and on for years, and I think PulseAudio is, or will be, much better, especially for things that insist on, or conflict, with Esound. PulseAudio actually resolved several other problems I was having with sound in various apps.

But Flash still didn't work. No audio. I tinkered and configured and tried editing config files, environment variables, and all the other confusing stuff... I tried just about every tip or suggestion posted in all of the threads above and every combination! And I'm pretty methodical and have been administering Linux boxes since 1997 and have a quite a lot of training and experience.

I googled around and finally found a '.deb' package with PulseAudio's "libflashsupport". It didn't work either. I tried compiling libflashsupport myself and apparently it required libpulse >= 0.9.7 and Gutsy only had libpulse-0.9.6.

Then I found another libflashsupport .deb file that was supposed to work with Gutsy. I tried it, and it didn't work either.

So I started using the ldd command on every library file in that libflashsupport package and found that one file, libpulse-simple.so was missing a dependency for libasyncns.so.0. So I installed the libasyncns0 package in Synaptic and and it still didn't work! Ok.. it needed the 32-bit version of libasyncns. So I installed libasyncns0 on another computer running feisty32 and copied the needed file from my Fiesty computer to the /usr/lib32 directory on my Gutsy64 box, and viola!!!

Flash with sound!!! Finally!

So, this worked for me. I don't know if there are other, more workable solutions, and I don't know if this will work for anybody else. It is not an easy solution, probably not for beginners, but it is a solution. It is possible to make Adobe Flash work with PulseAudio on Gutsy64!

Now if I can just get PulseAudio to work with JACK!


Chuck Bell (Sabaki)


Motherboard: ECS RS482M
Processor: AMD Athlon 64 3500+ (2200MHz)
Memory: 1G DDR Ram
On board video: ATI RS482 [Radeon Xpress 200] (64Mb)
On board AC '97 audio:
ATI RV410 [Radeon x700 Pro (PCIE)] (256Mb)
Add-on sound  Ensoniq ES1370 [AudioPCI]
Monitor:  NEC Multisync LCD1760V (default resolution 1024x1280)


Ubuntu64 'Gutsy'

Oh yeah, and I finally got the ATI fglrx drivers (fglrx_8.42.3) with AIGLX to work, too! 


---------------------
There is no real substitute for direct observation.

---

### Post by Kilz on 2007-11-19
Just one question,  did you post on it what actually fixed the issue to the bug reports? Letting users know is all fine and good, but if the developers (who seldom read the forums) dont know about it, it will never get fixed.

---

### Post by Sabaki on 2007-11-19
> **Kilz said:**
> Just one question,  did you post on it what actually fixed the issue to the bug reports? Letting users know is all fine and good, but if the developers (who seldom read the forums) dont know about it, it will never get fixed.

It has been now, at least to a couple of the bug reports. It isn't even really a fix, but a kludgy work-around, as PulseAudio is not installed by default, and there is no libflashsupport or 32-bit libasyncns0 packages in the repositories. It worked for me, and maybe someone can use this information.

---

### Post by exactt on 2007-11-22
i have some question as i don't get it fixed right now...

<quote>
Then I found another libflashsupport .deb file that was supposed to work with Gutsy. I tried it, and it didn't work either.
</quote>
where did you get the debs? which version of them? were they i386 or AMD64? what was the error message when you started firefox and launched a flash clip with sound?
maybe: ALSA lib ../../../src/pcm/pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so ???

<quote>
So I started using the ldd command on every library file in that libflashsupport package and found that one file, libpulse-simple.so was missing a dependency for libasyncns.so.0. So I installed the libasyncns0 package in Synaptic and and it still didn't work! Ok.. it needed the 32-bit version of libasyncns. So I installed libasyncns0 on another computer running feisty32 and copied the needed file from my Fiesty computer to the /usr/lib32 directory on my Gutsy64 box, and viola!!!
</quote>
1. there is only one library file in libflashsupport, right? it is /usr/lib/libflashsupport.so
2. if i do ldd /usr/lib/libpulse-simple.so i get:
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002b1ad2692000)
        libpulse.so.0 => /usr/lib/libpulse.so.0 (0x00002b1ad28ad000)
        libcap.so.1 => /lib/libcap.so.1 (0x00002b1ad2aeb000)
        librt.so.1 => /lib/librt.so.1 (0x00002b1ad2cef000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002b1ad2ef8000)
        libm.so.6 => /lib/libm.so.6 (0x00002b1ad30fd000)
        libc.so.6 => /lib/libc.so.6 (0x00002b1ad337e000)
        /lib64/ld-linux-x86-64.so.2 (0x0000555555554000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0x00002b1ad36d9000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0x00002b1ad38e2000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002b1ad3afe000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002b1ad3e0f000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002b1ad4012000)
  nothing about a libasyncns.so.0
3. I also can't find the libasyncns.so.0 on my gutsy 32-bit install where flash together with pulseaudio is working just fine.

thx for your help

---

### Post by loganm10 on 2007-11-22
I have 64-bit gutsy and 64-bit firefox and flash-nonfree worked out of the box for me, it was very easy, I just go somewhere like youtube and it says at the top I need a new plugin, I click next a couple times and it installs flash with the 32-bit libraries, sound and everything works great

---

### Post by Cappy on 2007-11-22
To get that 32-bit library you can install getlibs here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and then run ```
 sudo getlibs -32 libasyncns.so.0
```

That /usr/lib/alsa-lib/libasound_module_pcm_pulse.so is in package libasound2-plugins but that's the 64-bit version. If you need the 32-bit version getlibs can't get it because it falls into a filter I placed to keep from downloading debug libraries. You can download the 32-bit packages at [http://packages.ubuntu.com/gutsy/libs/libasound2-plugins](http://packages.ubuntu.com/gutsy/libs/libasound2-plugins) though and then ```
dpkg -x packagename_i386.deb newfolder4extract
sudo cp -R newfolder4extract/usr/lib/* /usr/lib32
```

---

### Post by exactt on 2007-11-22
thanks for your replies. i got a bit further by removing .asoundrc and .asoundrc.asoundconf from my home directory. now i have a new error message:

ALSA lib ../../../src/pcm/pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave

which led me directly to

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/150129](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/150129)

now i am stuck again...

EDIT: the message remains the same no matter if i have the libflashsupport.so installed or not. BTW do i need a 32-bit or 64-bit version of this lib. I had both installed but nothing changed...

---

### Post by nstamoul on 2007-11-23
I followed the instructions but still no luck here.

I got a fresh install of gutsy amd64,pulseaudio install ofc.

When i open FF and launch a youtube video i get the following repeatedly:

ALSA lib ../../../src/pcm/pcm_route.c:1113:(_snd_pcm_route_open) Unknown field route_policy

Any suggestions?

---

### Post by exactt on 2007-11-24
small update:

removing asound.conf was not bringing me further but backwards. i found this out as vlc and mplayer weren't working as well. when putting asound.conf back these apps were working. 

so with flash i am back here:

ALSA lib ../../../src/pcm/pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so

---

### Post by exactt on 2007-11-24
@Cappy

> 
That /usr/lib/alsa-lib/libasound_module_pcm_pulse.so is in package libasound2-plugins but that's the 64-bit version. If you need the 32-bit version getlibs can't get it because it falls into a filter I placed to keep from downloading debug libraries. You can download the 32-bit packages at [http://packages.ubuntu.com/gutsy/libs/libasound2-plugins](http://packages.ubuntu.com/gutsy/libs/libasound2-plugins) though and then ```
dpkg -x packagename_i386.deb newfolder4extract
sudo cp newfolder4extract/usr/lib /usr/lib32
```

i have copied the libasound_module_pcm_pulse.so to /usr/lib32/alsa-lib but firefox is still looking in /us/lib/alsa-lib ...

suggestions?

---

### Post by evilXhwnd on 2007-12-12
> **exactt said:**
> @Cappy



i have copied the libasound_module_pcm_pulse.so to /usr/lib32/alsa-lib but firefox is still looking in /us/lib/alsa-lib ...

suggestions?


I have the same issue. anyone have any ideas?

---

### Post by Cappy on 2007-12-12
I made a typo; that should have been
```

dpkg -x packagename_i386.deb newfolder4extract
sudo cp -R newfolder4extract/usr/lib/* /usr/lib32

```
(recursive copy)

Don't forget to make sure to
```
sudo apt-get install libasound2-plugins
```
also.

If nothing helps you may want to see if 
```
ldd /usr/lib/alsa-lib/libasound_module_pcm_pulse.so | grep -i 'need'
```
returns anything.

I don't know anything about pulse audio (other than what it is) so I'm shooting a bit in the dark.

---

### Post by lean on 2007-12-23
It worked fine.

This is what I did (PulseAudio must already be installed and working):


wget [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
sudo dpkg -i getlibs-all.deb
sudo getlibs -32 libasyncns.so.0

wget [http://jean-christophe.dubacq.fr/public/source/amd64/libflashsupport_1.0_2219-1_amd64.deb](http://jean-christophe.dubacq.fr/public/source/amd64/libflashsupport_1.0_2219-1_amd64.deb)
sudo dpkg --force-overwrite -i libflashsupport_1.0_2219-1_amd64.deb

sudo apt-get install libasound2-plugins

---

### Post by laceration on 2008-02-16
I always try the easiest way first!

I too, have had countless headaches getting flash in firefox to work in amd64.  I had it working, then it disappeared.  I don't know if it was a firefox update or an Ubuntu one or what. 

I installed Flash 9.0 r115, which, if I remember, is available in Synaptic Package Manager when you enable pre-release updates from system>administration >software sources.  But then the sound didn't work.

 I installed PulseAudio from the instructions at [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) and followed all the instructions *untli* the Flash part. 

 I clicked the links in Lean's post and let the Gdebi installer do it's stuff.  I got an error message on the second link--I guess it didn't even install.  But finally Pandora is working again!:)  Maybe I just needed to install PulseAudio.

To whom it may concern: Please don't break Flash again, I might lose it.

---

