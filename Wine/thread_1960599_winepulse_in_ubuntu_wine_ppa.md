---
title: "winepulse in ubuntu wine ppa"
date: 2012-04-17
forum: Wine
---

### Post by vladdy on 2012-04-17
Hey all,

Wine has rejected the winepulse patches for unrelated reasons to the patches themselves. As such the pulseaudio support isn't handled by wine, As such I plan on supporting it in this thread.

Quick Q&A (might be updated later):

Q: What versions of wine are supported?
A: At the moment I only do plan to do support new releases of wine, from 1.5.2 onward. However the patches themselves can be backported to 1.4 if there's demand for it.

Q: I want to know if a sound related bug is caused by winepulse or not.
A: Go to winecfg, in the tab 'libraries', enter 'winepulse.drv' in the box and click on add, click yes on the warning. Select winepulse.drv and change load order to 'disabled'. Now try to trigger your bug again, if it was a winepulse bug it shouldn't trigger any more. To undo the change: select 'winepulse.drv' and click 'delete'.
A2 (easier and preferred): From 1.5.3 onward, launch your program with WINENOPULSE=1 wine program.exe to temporarily disable winepulse for that program.

Q: So this bug is really a winepulse bug, how do I report it?
A: Leave a message here, I'm watching the thread. :)

Q: I'm a package maintainer for a different distribution, how do I get the latest patches?
A: If there's demand, I'll try to keep a public git tree you can use to generate patches from. Again reply in this thread!

Q: Sound works better than with winealsa!
A: Feel free to share it here too, I'm trying to see if it's worth maintaining these patches for everyone, so feedback is welcome.

Q: I'm using pulseaudio->jack with pulseaudio version less than 1.99.3 and sound works horrible.
A: [This commit]("http://cgit.freedesktop.org/pulseaudio/pulseaudio/commit/?id=311654766207b3776e2618ae63ac35115db48bbd") should fix things.

Q: Where are the patches?
A: I rebase the git tree around the time of every release, see [http://repo.or.cz/w/wine/multimedia.git/shortlog](http://repo.or.cz/w/wine/multimedia.git/shortlog)

Q: I get underruns/bad sound on some applications if I don't run another application with sound in the background. Sometimes killall pulseaudio helps.
A: Pulseaudio < 3.0 has a bug that was [fixed]("http://cgit.freedesktop.org/pulseaudio/pulseaudio/commit/?id=29f064aa3d3a83e275361aad3f9e7efdc84b8ad0") near the release of 3.0, try upgrading to pulseaudio 3.0 or newer.

---

### Post by YokoZar on 2012-04-17
Currently these patches are *included* in the Wine PPA that many of you are using (for wine1.5 package).  I may change this in the future to a different PPA, however, to keep it "official" (ie upstream).

Anyway, feedback appreciated.

---

### Post by HunterZ on 2012-04-18
That's incredibly disappointing to hear :(

I actually found this thread because I have been following the wine/multimedia.git commits and saw the following commit: [http://repo.or.cz/w/wine/multimedia.git/commit/8cb901e61446bd469f89de936133d2918fedbfd1](http://repo.or.cz/w/wine/multimedia.git/commit/8cb901e61446bd469f89de936133d2918fedbfd1)

I'd really like to know what the new excuse is for rejecting winepulse, as the previous excuse (an OpenAL audio engine) was thrown out some time ago. It completely boggles my mind that the Wine project leadership does not see this as a massive issue.

---

### Post by cogadh on 2012-04-19
I'm right there with you. It was one thing 4 - 5 years ago when the Pulse discussion started; almost no distros used Pulse, so no need to even consider wasting limited resources on it. But now, every major distro, for better or worse, has moved to Pulse. It makes no sense to continue stonewalling it. I understand that there are some technical issues involved, but the public perception is that the Wine "powers that be" are being petty about this whole thing and are failing to consider its impact on their growing user base. It is a completely baffling disconnect on their part.

---

### Post by HunterZ on 2012-04-19
The rumors of patch rejection by the Wine leadership seem to be exaggerated:

From [http://bugs.winehq.org/show_bug.cgi?id=10495#c352](http://bugs.winehq.org/show_bug.cgi?id=10495#c352) :
> [EMAIL="aeikum@codeweavers.com"]Andrew Eikum[/EMAIL]                                                  2012-04-19 07:22:20 CDT                    (In reply to [comment #351]("http://bugs.winehq.org/show_bug.cgi?id=10495#c351"))
> the Wine leadership seems to think that denying the prevalence of
> Pulseaudio is the best solution.

Nope. This stuff is hard and requires careful development and testing to create as few regressions as possible. We really wanted the ALSA->PulseAudio path to work, and we tried very hard to make it work for everybody. Trust me, we know about the prevalence of PulseAudio: we spent months trying to work around bugs in alsa-plugins, and the ALSA driver is full of hacks as a result.

Unfortunately, it turns out that alsa-plugins isn't robust enough for Wine's purposes. Because of the complexity of this problem and the large increase in work required to maintain yet another driver, we take the process of adding a new driver very seriously.

It has become clear that we need a PulseAudio driver, and one will get in eventually. Please continue to be patient as we work towards a solution that is acceptable for Wine. I promise there is active work being done on this.

---

### Post by cogadh on 2012-04-19
Well, that's good to hear, but at this point, I'll believe it when I see it.

---

### Post by HunterZ on 2012-04-19
That makes two of us.

---

### Post by vladdy on 2012-04-28
The comment by austin on the bug report is wrong, I have in fact given up on trying to get it in wine after the current maintainer decided to drop the patch without even looking at it.

And iirc aeikum planned to address it by rewriting my patch.. derp

---

### Post by HunterZ on 2012-04-28
> **vladdy said:**
> The comment by austin on the bug report is wrong, I have in fact given up on trying to get it in wine after the current maintainer decided to drop the patch without even looking at it.

And iirc aeikum planned to address it by rewriting my patch.. derp
Thanks for the update. That is not good news. I hope you don't mind that, as a concerned end-user, I have a desire to push back on that kind of behavior via the Wine bugzilla thread.

---

### Post by vladdy on 2012-04-29
I'm not sure that would do any good, doubt you can get it accepted into wine by upsetting people.

---

### Post by dino99 on 2012-04-30
wine 1.5.2 upgraded to 1.5.3 on Precise i386, using wine-ppa

fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit [http://ubuntuforums.org/showthread.php?t=1960599](http://ubuntuforums.org/showthread.php?t=1960599)

adding winepulse.drv seems useless

---

### Post by bibibobobibu on 2012-04-30
You don't even imagine how audio stuff is complex and badly designed.
For years, wine has tried satisfying everyone with workarounds and hacky code.
Even audio on Windows was a real pain.
Microsoft decided with Vista to completely rewrite the audio stack.
The new API is called MMDevAPI. Just google it and you'll see.

Have you ever looked at Andrew Eikum work ?
Or read his mails on wine devel mailing list ?
Just look at [http://source.winehq.org/git/wine.git/?a=search&h=HEAD&st=author&s=Eikum](http://source.winehq.org/git/wine.git/?a=search&h=HEAD&st=author&s=Eikum) and you'll see what I mean.
No one wanted to work on audio and now there are some developers willing to improve audio in wine which mean fixing wine AND pulseaudio or alsa upstream.
They are doing their best, really.

Like GDI has been painful for years, it's now not-complete-but-functional.
Give them some time and be respectful for these volunteers (or not but whatever) who spend time for such a big project.

---

### Post by glide007 on 2012-04-30
I also get the same message:

wine 1.5.2 upgraded to 1.5.3 on Precise i386, using wine-ppa

fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit [http://ubuntuforums.org/showthread.php?t=1960599](http://ubuntuforums.org/showthread.php?t=1960599)

with addition to my application message:  there are no compatible sound devices installed on this computer

Application: Cisco IP Communicator

If I try to change the Sound=Alsa with help of winetricks, I do not get any wine message but no audio, and get same message from application.

---

### Post by cogadh on 2012-04-30
> **bibibobobibu said:**
> You don't even imagine how audio stuff is complex and badly designed.
For years, wine has tried satisfying everyone with workarounds and hacky code.
Even audio on Windows was a real pain.
Microsoft decided with Vista to completely rewrite the audio stack.
The new API is called MMDevAPI. Just google it and you'll see.

Have you ever looked at Andrew Eikum work ?
Or read his mails on wine devel mailing list ?
Just look at [http://source.winehq.org/git/wine.git/?a=search&h=HEAD&st=author&s=Eikum](http://source.winehq.org/git/wine.git/?a=search&h=HEAD&st=author&s=Eikum) and you'll see what I mean.
No one wanted to work on audio and now there are some developers willing to improve audio in wine which mean fixing wine AND pulseaudio or alsa upstream.
They are doing their best, really.

Like GDI has been painful for years, it's now not-complete-but-functional.
Give them some time and be respectful for these volunteers (or not but whatever) who spend time for such a big project.

We all know how crazy audio is, but this has been an ongoing discussion for over 5 years now with little to no action taken and when solutions are presented, like this Pulse driver, they are shot down emphatically. We've given them plenty of time, they just don't seem to be willing to work together on this. Like I said before, this is the impression they are giving the public, whether true or not, they need to address this in a clear and concise manner, once and for all.

Also, you act as though Maarten has done nothing in comparison:
[http://source.winehq.org/git/wine.git/?a=search&h=HEAD&st=author&s=Lankhorst](http://source.winehq.org/git/wine.git/?a=search&h=HEAD&st=author&s=Lankhorst)

---

### Post by vladdy on 2012-05-01
To those who are curious about the winediag messages, I added them to redirect questions about winepulse to this thread where I can provide support. I only support problems that result from using winepulse, for other problems you will still have to ask winehq.org.

glide007: Oh, looks like your problem is not related to winepulse then if no message pops up. Feel free to contact wine through official ways and they should be able to help you. :)

EDIT: I would also like to ask you not to disable winepulse just because of the winediag messages I added, it is likely winepulse works better than winealsa for you, and if not I'll do my best to fix it, provided that you let me know about your issues.

---

### Post by killown on 2012-05-01
wine 1.5.3

fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit [http://ubuntuforums.org/showthread.php?t=1960599](http://ubuntuforums.org/showthread.php?t=1960599)


Oblivion game
The game starts and the sound works but when screen menu appear then it crashes 

fixme:gstreamer:no_more_pads Done
fixme:gstreamer:event_sink 0x649218c0 stub tag
fixme:gstreamer:event_sink 0x649218f0 stub tag
fixme:gstreamer:event_sink 0x64921920 stub tag
fixme:gstreamer:event_sink 0x64921950 stub tag
fixme:gstreamer:event_sink 0x64921980 stub tag
fixme:gstreamer:event_sink 0x649219b0 stub tag
fixme:gstreamer:GSTOutPin_QueryInterface No interface for {f185fe76-e64e-11d2-b76e-00c04fb6bd3d}!
fixme:gstreamer:GSTOutPin_QueryInterface No interface for {31efac30-515c-11d0-a9aa-00aa0061be93}!

I was able to play Oblivion before on 11.10 but after upgrade for ubuntu 12.04 I could't play anymore due to gstreamer issues

I am using a clean wine prefix, I don't know if I would report bug for wine team since it seems more a ubuntu problem, because I had a lot hour of gameplay with no problem and no crashes on 11.10 and I was using wine 1.5.2, also, I tried 1.5.2 on 12.04 too.

EDIT.

Fixed by removing gstreamer-plugins-ugly and disabling quartz

---

### Post by Mike Grant on 2012-05-05
Just a note to say I got the winepulse driver going in Fedora 16 with the standard wine package and it works hugely better than the alsa one, which would break up, underrun and sometimes crash.  The Pulse driver sounds great and hasn't had any glitches so far (ok, only one day and one app..).

A few quick notes on what I did (warning: ugly hack + not for the uninitiated):

```

 # ensure your Fedora wine version matches that of this git repo
git clone git://repo.or.cz/wine/multimedia.git # optionally, --depth 1
sudo yum install glibc-devel.i686 pulseaudio-libs-devel.i686  # YMMV
cd multimedia/
./configure --without-x --without-freetype  # we only want to build the pulse driver
make
cd dlls/winepulse.drv
chmod a+rX winepulse.drv.so fakedlls/winepulse.drv.fake
sudo cp winepulse.drv.so /usr/lib/wine
sudo cp winepulse.drv.fake /usr/lib/wine/fakedlls/  # optional..
cd /usr/lib/wine
# ugly hack, because I couldn't force it into the winecfg and didn't want to reinstall all of wine
sudo mv winealsa.drv.so no winealsa.drv.so-original
sudo ln -s winepulse.drv.so winealsa.drv.so
 # to restore the original
sudo  rm winealsa.drv.so ; ln -s winealsa.drv.so-original winealsa.drv.so

```Here's hoping this driver gets picked up by the Fedora packagers, at least until the wine devs come to their senses / finish their own pulse driver..

---

### Post by vladdy on 2012-05-05
> **Mike Grant said:**
> Here's hoping this driver gets picked up by the Fedora packagers, at least until the wine devs come to their senses / finish their own pulse driver..

First of all thanks and I'm glad about another happy customer. :-)
Second, no wine won't write their own driver, at best they'll rewrite my driver poorly.. wish I was kidding

---

### Post by cheako on 2012-05-07
Hello,
I'm re-packaging ubuntu-wine into my own cheako/wine4diabloiii ppa, I just want to clear up how I'm getting wine that runs Diablo III.

Firstly I want to outline how I've setup my sound testing environment. Mainly so that others can nic it but also so that my configuration is clear.

```
$ cat /etc/asound.conf
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
pcm.pasuspender {
        type asym
        playback.pcm {
                type plug
                slave.pcm "spdif:CARD=SB"
        }
        capture.pcm {
                type plug
                slave.pcm "null"
        }
}
ctl.pasuspender {
        type asym
        playback.pcm {
                type plug
                slave.pcm "spdif:CARD=SB"
        }
        capture.pcm {
                type plug
                slave.pcm "null"
        }
}
pcm.a52 {
@args [CARD]
@args.CARD {
type string
}
type rate
slave {
pcm {
type a52
bitrate 448
channels 6
card $CARD
}
rate 48000 #required somehow, otherwise nothing happens in PulseAudio
}
}

```The last bit is specific to my Sony Receiver, but what's important in the default for pulse AND the setting for pasuspender that routes to the hardware, as the current Church of Wine instructs. On my setup the winealsa driver has 3 or 4 targets, I'll list em in a special way.

Configuring the winealsa driver TOOK a lot of asking questions and searching/reading, but in the end I only go it work after reading the source code... Please Fix This! I'll try and help.

regedit to: ```
HKEY_CURRENT_USER\Software\Wine\drivers\winealsa.drv
```Create a new Multi string value called ALSAOutputDevices.

This is a hack/workaround for winealsa. Currently winealsa uses a vary ancient, to say the least, API for scanning the devices. Yes, they have been asked to change but are just ignoring the ALSA developers... Sound familiar? On the same note the current winealsa driver has some vary PA specific code, if it had been me I'd have forked winealsa just to support PA. Instead now we have a winealsa driver that's not suitable for any one, good going.

```
plug:pasuspender
plug:'a52:CARD=SB'
plug:spdif
pulse

```Now wine can use the libasound devices that it won't detect like it should. Another issue I have that I can't find a solution to is "How can I get wine to not list all the other PCMs?" I really really really hate scrolling past em in winecfg, there is a dialog that could stand to be at least 4x higher.

I have one more bug with winealsa that could use some work. Currently when I'm using pasuspender I have to run wine under a command, gee it's pasuspender. I'd like an option or just plain auto-detection(assuming it works flawlessly and perhaps can be overridden) to do thins in winealsa. I've stated the vary simple reason else where, it's so that wine's configuration can be in control of this. My current solution is to have two scripts to call wine, what if I call the wrong one by mistake? The other reason is because, asside from the auto detecting if pulse is being use, it's a vary simple change to make and even more the code would have to be protected by something like #ifdef _HAS_PULSE_H and thus only even compile on systems that have PA.

Now I understand that this is a forum for winepulse and I'm almost 80 lines in and not one mention of that till now. The point is that I've tested every one of these with winealsa and they all work flawlessly with Diablo III. What won't work is winepulse, there is an echo seams like every sound is repeated 3 or 4 times.

What can I do to identify this or track it down?

To switch from winealsa to winepulse or the other way around(vice versa).   Regedit the sting value of HKEY_CURRENT_USER\Software\Wine\drivers should be "alsa", "pulse", or perhaps even something else.  I think "jack" is also supported.

Now I'm going to go back and perform that manditory testing of winepulse. I didn't yet because this is long enough already.

While I'm at it, winecfg has one bug you should know about. Setting changes don't effect the Test Sound button, yeah I know I can't help laughing right now also. That button will continually regurgitate sound using only the settings wine originally started with... I might not have even caught this if my Received didn't jump up and say "Hi Dolby Digital Surround Sound." when configured to use Stereo PCM. This would have had me going for a bit with "No audio in Diablo, but works in winecfg."

---

### Post by cheako on 2012-05-07
Ohh, yeah.  I'd also like a simpler method to load winepulse|winealsa.  I think I will look into the setting library as you had for winepulse.  However if I disable winealsa.drv then I get no sound driver.

I'll keep playing with it, but either way the current situation is both unbearable and inappropriate.

---

### Post by cheako on 2012-05-07
Ok, following the instructions to either disable the loading of winepulse.drv or using WINENOPULSE=1, I get no audio drivers and thus no sound.

As my problem only exist when I can hear, it's a moot point.

I can however more aptly describe the issue.  Each sound byte is machine gunned out for about 0.5 seconds, perhaps 5 times...  It's so annoying that I can't really vouch for the accuracy of these figures.  I believe it's much like the writer is writing into a larger ring buffer then the reader is reading from.  Thus the audio is both repeated and clipped.

---

### Post by cheako on 2012-05-07
After some more testing I've discovered that Diablo II(this is not the same as Diablo III) does not work well using the winealsa driver, but works much better using the winepulse driver.

The only output that has an issue is the a52, Stereo PCM works just fine no matter what settings I use.  Pulse seams to always add static(even when using PCM), especially to the opening horn section(like in a band).  There is more static using the a52 driver and using the winealsa driver there is a few notes then static then nothing.

So now I've got applications on both sides and the need to have an easy/efficient method for switching grows.  I'll likely write a script that edits the user.reg file.

---

### Post by cheako on 2012-05-08
MOHAirborneDemo.exe (Medal of Honor) has scratchy and even Skippy sound in some places with the winepulse driver.

The winealsa driver locks up AirborneDemo when using pulse to a52.

---

### Post by cheako on 2012-05-10
Is this forum dead?
I feel it's the only safe place to talk about sound in ALSA when using Ubuntu.

---

### Post by RFS-81 on 2012-05-14
> **cheako said:**
> After some more testing I've discovered that Diablo II(this is not the same as Diablo III) does not work well using the winealsa driver, but works much better using the winepulse driver.

  Did you have pulseaudio running? I had pretty bad sound when winepulse.drv did not exist and I used Wine without "killing" pulseaudio first.

---

### Post by vladdy on 2012-05-16
Look, I don't want to encourage people to switch between winealsa and winepulse. I want to use winepulse if it's available, if there are specific issues you want to report I'm listening, but please give reports that are clear enough for me to understand:

1. What are you doing to trigger the bad behavior with winepulse
2. Does it happen with winealsa too (to isolate bugs that aren't in winepulse)
3. Any more information that might help me pin problems down, for example fixme/err's related to winepulse or audio in the console

If I ask for it please provide more information, else you will be forced to keep working around forever, instead of spending a few extra minutes fixing it with me finally.

---

### Post by CoCumis on 2012-05-29
When i use winepulse in DiabloII, then sound is about one second delayed and crackling. When i use winealsa, sound is still crackling but timing is correct.
When i use winepulse in CounterStrike, sound is also about one second delayed and crackling (only in menu in game is not crackling only delay), but when i use winealsa, sound is good.
In both cases in console is this fixme:

```
fixme:pulse:AudioRenderClient_GetBuffer 0x69e9948 Not using pulse locked data: 0 16374/17590 0/17590
```

DiabloII has this fixme three times, CounterStrike only one

My wine version is 1.5.5

P.S.: Sorry for my English

---

### Post by cheako on 2012-05-29
> **RFS-81 said:**
> Did you have pulseaudio running? I had pretty bad sound when winepulse.drv did not exist and I used Wine without "killing" pulseaudio first.

I was using PA via the ALSA pulse plug-in.

---

### Post by cheako on 2012-05-29
> **vladdy said:**
> 2. Does it happen with winealsa too (to isolate bugs that aren't in winepulse)


There are two ways(at least of the procedures I'm willing to even try) to accomplish this.

a. Use ALSA with the pulse plugin.
b. Use ALSA with any number of the other available plug-ins.  Typically this will be a hardware device, but it could also be using dmix.

Other methods include uninstalling PA and even stopping or killing PA.  I've found pasuspender to deliver as advertised and consider it to be the only method of disabling PA in order to implement option b.  I'm willing to accept the consequences of that descision and work with PA developers to correct *any bugs that pasuspender doesn't cover.

* I have yet to see any bugs with this configuration, aside from what wine introduces with it's legacy/depreciated sink detection code.

---

### Post by cheako on 2012-05-29
> **vladdy said:**
> Look, I don't want to encourage people to switch between winealsa and winepulse.

Sorry about that, perhaps in time we can look forward to achieving this.  However from my view point it's currently a necessary evil.  I believe it would be important, for debugging and in the mean time, to have a good set of instructions detailing how to do this available and supported.

---

### Post by lexa2 on 2012-05-30
Cheako (you're Mike Mestnik, am I right?), sorry for making noise, but could you please explain what are you trying to achieve by posting long messages about getting winealsa.drv to work with a PA as an output device to an unofficial support thread for winepulse.drv? Had you accidentally chosen a wrong forum/thread to post?

Problems with winealsa.drv behaving wrong with PA IMHO should be posted to WineHQ's forums mirrored with related bug report to Wine's Bugzilla. Maarten had done a wonderful work implementing winepulse.drv and we all should be thankful for that. On the other hand the fact that he had done it is not a reason to involve him into flameblown discussions about winealsa.drv "support" for PA and about Wine devs refusing to include his work in main Wine tree as it is - there's no point in that as it wouldn't result in anything positive.

Just my two cents.

---

### Post by BlankedOutBox on 2012-05-31
> **CoCumis said:**
> When i use winepulse in DiabloII, then sound is about one second delayed and crackling. When i use winealsa, sound is still crackling but timing is correct.
When i use winepulse in CounterStrike, sound is also about one second delayed and crackling (only in menu in game is not crackling only delay), but when i use winealsa, sound is good.
In both cases in console is this fixme:

```
fixme:pulse:AudioRenderClient_GetBuffer 0x69e9948 Not using pulse locked data: 0 16374/17590 0/17590
```DiabloII has this fixme three times, CounterStrike only one

My wine version is 1.5.5

P.S.: Sorry for my English
I have exact same problem. It was working perfectly in ppa version of 1.5.4, so I think this is a regression.
Also adding "tsched=0" option after "load-module module-udev-detect" in /etc/pulse/default.pa did not help.

---

### Post by vladdy on 2012-06-05
Might be related to dsound changes, pulseaudio might start to misbehave on larger latencies. I think it's probably the dsound changes breaking things, can you try to set windows version to vista or higher to find out? Diablo should use native audio calls if version is not xp.

---

### Post by CoCumis on 2012-06-07
I use windows version set to windows 7 as default. If You thought this. But I test also set it directly to D2Multires.exe and it is still delayed.(Or am I misunderstand what You want?)

---

### Post by Dlambert on 2012-06-08
Just updated this morning, the new pulse broke sound in wine for me. Its garbled at first, then quieter than normal.

---

### Post by quequotion on 2012-06-12
First of all let me express my disappointment with the decision not to support winepusle at this time and general dismay at the state of audio in GNU/Linux.

AMD64 wine needs to depend on libasound2-plugins:i386

This was necessary for me because I wanted to play an old game with MIDI music--for which pulseaudio, ergo winepulse, has no interface.

Winealsa, using the default alsa interfaces detected, output horrible, crackling, laggy PCM.

Cheako's advice to get the winealsa->pulseaudio interface working proved invaluable. 

In **HKCU\Software\Wine\drivers\winealsa.drv** I created a new multi-string value, **ALSAOutputDevices**, and added **pulse** as the first and only item in the list.

This allowed me to select **Out: pulse** in winecfg (which was always available in older version of wine), but my game still crashed with this error:```
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get)  Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_conf_pulse.so 
```

---

### Post by vladdy on 2012-06-14
Oh right, looks like wine has broken midi..

Sometimes I feel better if I DON'T look at what they come up with..

f6890ef0e227afd12ce2325497d0cae478602c7d looks evil, I don't get why they don't query that property off the default device instead, would have been less work, I'll see if I can add a workaround for pulse to it, sigh..

---

### Post by quequotion on 2012-06-18
> **vladdy said:**
> Oh right, looks like wine has broken midi..

Sometimes I feel better if I DON'T look at what they come up with..

f6890ef0e227afd12ce2325497d0cae478602c7d looks evil, I don't get why they don't query that property off the default device instead, would have been less work, I'll see if I can add a workaround for pulse to it, sigh..

Keep fighting the good fight!

---

### Post by cheako on 2012-06-20
I am Mike Mestnik.

It seams as though pulseaudio is unsupported at all when using wine, the only advice ppl get when asking on IRC is that you must completely uninstall pulseaduio.

As such, there is no other community for pulseaduio users and wine.

I know that these instructions are perhaps unwelcome here, however there is no better place for them.  This could turn into unsupported hack center of the wine audio world, in for a penny in for a pound you Audio rebels.

To switch from winealsa to winepulse.   Regedit the sting value of  HKEY_CURRENT_USER\Software\Wine\drivers\Audio should be "alsa", "pulse", or  perhaps even something else.  I think "jack" is also supported.

---

### Post by vladdy on 2012-06-24
Ok I've uploaded wine 1.5.7 with pulse17 and a new version of pulse18.

Changes since v17 from changelog:
```

  * Winepulse v18 patch
    - Remove clock_pulse interpolation. It sadly couldn't work.
    - Allow 2 * MinimumPeriod for shared buffers
    - Fix all compiler warnings when compiling with 64-bits
    - Dynamically select low latency mode if less than 2 default periods
      are requested. This requires the rtkit patch to be useful.
  * rtkit patch
    - Uses rtkit to get realtime privileges in a safe manner.
      This allows for more accurate timing and less chance of underruns.
  * dsound patches to work nicer with winepulse
    - Rework that uses event-based handling for rendering. In testing
      with jackd, down to 3.3ms latency was possible. It will still
      underrun once every few seconds, so low latency is not on by
      default. 80 ms will be default latency.
  * mmdevapi patch to reactivate midi with winepulse
    - winmm will use winealsa for midi only
  * Add patch so default valgrind on precise won't crash
    - Don't bump fd limit with valgrind enabled.

```

In human form: I use rtkit's hook for wine that never got upstream to add reliability to winepulse. dsound rendering has been reworked slightly. If you are insane and into pro audio winepulse can be used to go arbitrarily low in latency. Only for WASAPI mode though.  Hopefully this will make winepulse even more stable than before, and you no longer need to enable winealsa for midi. :)

If latency interests you, the new default latency for dsound mode is 80 ms, which is still less than before. I can help you patch dsound to go lower than 80 ms if you want, but you should really use WASAPI mode if your audio software supports it since it will work by default then. I had 3.3ms from dsound with underruns every second piping pulseaudio to jackd. One has to find the lower bound right? Because of obvious reasons I never enabled this by default. This will never be possible with winealsa as far as I can tell..

~Maarten

---

### Post by quequotion on 2012-06-26
> **vladdy said:**
> you no longer need to enable winealsa for midi. :)

YAY!

Question:

Hearing this news, I immediately upgraded, opened regedit, and changed my driver back to "pulse"

When I opened winecfg, the panel still displays "winealsa.drv", but offers choices of "Default" or "Pulseaudio" for all devices.

Clearly, this is not the original alsa driver, which still has my custom "Out: Pulse" option along with several dysfunctional alsa ports.

As far as I can tell, this driver is fully functional and midi support works without any need to reconfigure my software.

Just a misprint?

---

### Post by vladdy on 2012-06-28
Oh seems it uses the same mechanism as winmm to determine driver name, strictly speaking a bug.

---

### Post by dreddie on 2012-06-28
Hmm... seems like the latest build (wine 1.5.7-0ubuntu3~pulse18 ) in the ppa is not working. I get the following error: 

> getting server_pid from lock 19361
wine: cannot get pid from lock (lock isn't locked)
err: process:start_wineboot failed to start wineboot, err 1359
getting server_pid from lock 19361
wine: cannot get pid from lock (lock isn't locked)

---

### Post by vladdy on 2012-07-02
Yeah that was scott with a apparmor patch and he fixed it in ubuntu4.

---

### Post by quequotion on 2012-07-08
> **cheako said:**
> the only advice ppl get when asking on IRC is that you must completely uninstall pulseaduio.

Off topic:

Why is it that people distrust pulseaudio so  much?

I've lost count of how many forum threads, blog posts, and wikis I've seen with "solutions" that involve the complete removal of pulseaudio.

I've had some trouble now and then myself, but I've always been able to find a solution through pulseaudio--unless the problem was a deficiency in ALSA or a bug elsewhere in the tangled mess that is the linux audio subsystem.

---

### Post by trasatti on 2012-07-11
problems installing the net framework 2.0 in ubuntu 4.12

the following message appears when trying to install dotnet20 porfavor help me

dotnet20 install completed, but installed file / home / bruno / .wine / DosDevices / c :/ windows/Microsoft.NET/Framework/v2.0.50727/mscorlib.dll not found

---

### Post by vladdy on 2012-07-14
New version, it turns out due to lack of testing dsound was broken in 1.5.7, sorry about that. With 1.5.8~ubuntu3 dsound should work right again, and skyrim will start working too. :-)

For some reason it was requesting a 20 ms buffer, so it took some extra effort to get that right.If you are still on 1.5.6 due to regression, copying those dll's from 1.5.6 will make things work in 1.5.8: d3d10core.dll.so d3d10.dll.so d3d8.dll.so d3d9.dll.so  d3dim.dll.so d3drm.dll.so gdi32.dll.so opengl32.dll.so wined3d.dll.so  winex11.drv.so ddraw.dll.so

More feedback is welcome though, after 1.5.8~ubuntu3 is uploaded are there any programs that still have problems with sound in winepulse?

---

### Post by tkmn on 2012-07-17
No sound issues, but I believe I am suffering from this bug:

[http://bugs.winehq.org/show_bug.cgi?id=30986](http://bugs.winehq.org/show_bug.cgi?id=30986)

The last update (1.5.8-0ubuntu3~pulse18 ) killed my framerate in StarCraft 2.

:confused:
[I]
This bug was fixed in 1.5.9[/I]

---

### Post by OpenRevan on 2012-07-18
Every dsound applications lags on x86-64 PC (nothing on x86-32 one, Wine 1.5.9-0ubuntu1~pulse19), log with WINEDEBUG="warn+all":```
warn:sound SOUND_PerformMix Probable buffer underrun
warn:pulse pulse_underflow_callback Underflow
warn:sound SOUND_PerformMix Probable buffer underrun
```

---

### Post by vladdy on 2012-07-18
Should be fixed in 1.5.9~ubuntu2, sorry for the inconvenience, it was completely my fault. :)
2 calls sharing almost completely the same name behaved completely different.

---

### Post by OpenRevan on 2012-07-19
**vladdy**
Fixed, ya [IMG]https://dl.dropbox.com/u/43692746/emot2/56.png[/IMG]?```
The following packages have unmet dependencies:
 wine1.5-i386:i386 : Depends: libmpg123-0:i386 (>= 1.13.7) but 1.12.1-3.2ubuntu1 is installed.
                     Depends: nvidia-libopencl1:i386 (>= 195) which is a virtual package.
```

---

### Post by vladdy on 2012-07-19
What version of wine1.5-i386:i386 is that? I have no such depends in 1.5.9-0ubuntu2~pulse19+build1

---

### Post by OpenRevan on 2012-07-19
**vladdy**
I'm feeling like an idiot - other repo %).
Sorry about that stupid report.

---

### Post by vladdy on 2012-07-19
[IMG]http://testbot.winehq.org/~mlankhorst/rbd-laugh.png[/IMG]

---

### Post by OpenRevan on 2012-07-20
[IMG]http://s1.hostingkartinok.com/uploads/images/2012/01/f5d39fbebfa7b22907c5213dafb15ab3.png[/IMG]

---

### Post by vladdy on 2012-07-24
Are there any outstanding issues with my winepulse now or all they all fixed in 1.5.9-0ubuntu2?

---

### Post by OpenRevan on 2012-07-26
**vladdy**
[IMG]http://s1.hostingkartinok.com/uploads/images/2012/02/e24e5d7dff91de542a87a8eed93854a5.png[/IMG] Everything is fine.

---

### Post by DoctorMO on 2012-08-03
I think winealsa and winepulse produce the same problem, pulse audio shows the audio source being destroyed and created many times per second causing a very distinctive jumps.

Not sure what you guys can recommend for such a problem, I was kinda hoping winepulse would fix the issue.

---

### Post by vladdy on 2012-08-04
> **DoctorMO said:**
> I think winealsa and winepulse produce the same problem, pulse audio shows the audio source being destroyed and created many times per second causing a very distinctive jumps.

Not sure what you guys can recommend for such a problem, I was kinda hoping winepulse would fix the issue.

....?

I don't understand the context, the problem, what you mean or how to reproduce it..

---

### Post by DoctorMO on 2012-08-04
Running any Windows 98 game on Ubuntu 12.04 using either wine 1.4 or wine 1.5 (pulse). It's odd because at first you think it's a buffering problem, but looking at the sound preferences in the apps tab, the app's sound is disappearing and reappearing like crazy.

Not sure how you could test it, try the demo of one of the games: [http://games.softpedia.com/get/Games-Demo/Pharaoh.shtml](http://games.softpedia.com/get/Games-Demo/Pharaoh.shtml)

---

### Post by vladdy on 2012-08-09
I don't get sound from pharaos?

---

### Post by DoctorMO on 2012-08-09
**Update:** Interesting results, if I'm playing music (rhythembox) when I load a game, then the sound works perfectly, every time.

Maybe this is an error in pulseaudio itself.

---

### Post by vladdy on 2012-08-11
Can you attach a +winmm,+pulse,+dsound,+tid log of broken?

---

### Post by quequotion on 2012-08-20
As of wine 1.5.11-0ubuntu1, the pulseaudio patchset number has been removed from the naming scheme in the PPA.

[s]I just want to make sure before upgrading: are the pulseaudio drivers still there?[/s] Yes they are :)

Also, interest in proper multi-channel dsound +1.

---

### Post by woefulwabbit on 2012-08-21
Since switching back from cheako's d3 ppa to the wine ppa, I've found that my sound has been stuttering and looping in Diablo 3. The issue went away when I stopped using "taskset -c 0" to run Diablo 3 (which is needed for some of us to get rid of stuttering frames).

Can anyone else reproduce the sound issues with taskset -c 0?

For now my solution is to use "taskset -c 0,1" which gets rid of both stuttering frames and stuttering sound

---

### Post by vladdy on 2012-08-22
> **woefulwabbit said:**
> For now my solution is to use "taskset -c 0,1" which gets rid of both stuttering frames and stuttering sound

Ok taskset -c 0 probably shouldn't break sound. Can you try running diablo 3 with windows version set to vista or higher? It should use the native audio path instead of going through dsound, if it uses the same audio engine as warcraft.

---

### Post by HunterZ on 2012-09-04
> **YokoZar said:**
> Currently these patches are *included* in the Wine PPA that many of you are using (for wine1.5 package).  I may change this in the future to a different PPA, however, to keep it "official" (ie upstream).

Anyway, feedback appreciated.
Scott,

Any chance you could link the specific PPA, just so I can make sure that I'm using the right one? Thanks.

---

### Post by vladdy on 2012-09-05
If you want to report specific bugs just follow what I said above, the patches are meant to make things more useful, not less. If they do make things less useful please help me help you help us all.

---

### Post by jrssystemsnet on 2012-10-20
> **cheako said:**
> To switch from winealsa to winepulse or the other way around(vice versa).   Regedit the sting value of HKEY_CURRENT_USER\Software\Wine\drivers should be "alsa", "pulse", or perhaps even something else.  I think "jack" is also supported.

Thank you SO MUCH for this!  This was all I needed to get beautiful, clear sound on my Precise (12.04.1) x86_64 workstation under Wine.  I've been suffering along for freaking EVER with horrible, choppy staticky audio, and of course even installing wine-1.5 from the PPA didn't fix it... because winecfg and winetricks didn't know anything about pulse, and wine-1.5 still had alsa selected, so until I saw your post about making the manual regedit, I'd never actually USED the pulse driver.

TL;DR this fixed EVERYTHING for me.  Thank you thank you thank you. :)

---

### Post by vladdy on 2012-10-26
Well please consider removing that key altogether then, winepulse will fail to load and fallback to alsa if pulseaudio is not available as audio system, but only if you don't have that registry key.

---

### Post by DGhost001 on 2012-10-28
Hi there,

since the update to wine 1.5.16 I can't start programs that are using dsound any more.
It is completely independent from the program as long as it is using dsound and they all crashing with the same error:

```
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599
fixme:dsound:DSOUND_WaveFormat Limiting channels to 2 due to lack of multichannel support
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
Assertion 'pa_atomic_load(&(b)->_ref) > 0' failed at pulsecore/memblock.c:590, function pa_memblock_unref(). Aborting.
```If I start them with WINENOPULSE=1 they work as expected and they also worked with wine 1.5.15. So it seams to me that there is something broken with the wine pulse audio support in the latest wine from the ppa.

Hopefully this can be fixed.

---

### Post by vladdy on 2012-10-29
I'm surprised you're hitting that bug. Can you tell me what release you're on and what distribution?

This is a really old pulseaudio bug, and can be fixed by applying [http://cgit.freedesktop.org/pulseaudio/pulseaudio/commit/?id=e91e78bb54456eda7f815afdb25857fe0887de22](http://cgit.freedesktop.org/pulseaudio/pulseaudio/commit/?id=e91e78bb54456eda7f815afdb25857fe0887de22) to your pulseaudio sources, which will fix the bug. Make sure that if you're on a 32 + 64-bits system to get both libraries patched, as it's a client a lib issue..

I've been wanting to sru this to precise, but I wasn't able to reproduce the bug any more, but I know that commit fixes it since I hit the issue before myself. So if you're on precise let me know and I'll talk to the pulseaudio maintainer in ubuntu this week about sru'ing it after all. :-)

~Maarten

---

### Post by DGhost001 on 2012-10-30
> I'm surprised you're hitting that bug. Can you tell me what release you're on and what distribution?
I'm currently running a fully patched Kubuntu 12.04 64bit. 
The package manager reports
```

   pulseaudio           1:1.1-0ubuntu15.1
   libpulse0            1:1.1-0ubuntu15.1
   libpulse0:i386       1:1.1-0ubuntu15.1
   wine1.5              1.5.16-0ubuntu1  
   wine1.5-amd64        1.5.16-0ubuntu1
   wine1.5-i386:i386    1.5.16-0ubuntu1

```as being installed and being the latest available version of those packages.

> 
This is a really old pulseaudio bug, and can be fixed by applying [http://cgit.freedesktop.org/pulseaudio/pulseaudio/commit/?id=e91e78bb54456eda7f815afdb25857fe0887de22](http://cgit.freedesktop.org/pulseaudio/pulseaudio/commit/?id=e91e78bb54456eda7f815afdb25857fe0887de22) to your pulseaudio sources, which will fix the bug. Make sure that if you're on a 32 + 64-bits system to get both libraries patched, as it's a client a lib issue..

I've been wanting to sru this to precise, but I wasn't able to reproduce the bug any more, but I know that commit fixes it since I hit the issue before myself. So if you're on precise let me know and I'll talk to the pulseaudio maintainer in ubuntu this week about sru'ing it after all. :-)
Before I'm going into the trouble and start cross-compiling the 32bit pulse audio library on my 64bit machine, I would like to wait for the response from the pulse audio package maintainer. So it would be kind of you if you could contact him and let me know his response.

 Falk

---

### Post by father_ted on 2012-10-30
The old version of the pulse server isnt great with wine. The 2.0 version with the audio-dev ppa works a lot better on 12.04 - 12.10 has the newer one and works nicely.

---

### Post by vladdy on 2012-10-30
Looks like the precise pulseaudio already had that commit backported after all, so dont bother trying it yourself.

Either the backport didn' t fix it or you' re hitting another pulse issue specific to precise. Either way there's not much I can do right now, it looks like there is a workaround by using the mentioned ppa, so you can try that. Hopefully I'll have some time next week to look at it in more detail. :-)

---

### Post by DGhost001 on 2012-10-31
I just wanted to let you know, I just installed pulse audio from the audio dev ppa, as suggested by father_ted.

I have now installed:
```

libpulse0         1:2.0-0ubuntu1~precise2
libpulse0:i386    1:2.0-0ubuntu1~precise2
pulseaudio        1:2.0-0ubuntu1~precise2

```which seams to be the latest available versions for precise and it didn't solve the problem. I still get

```

Assertion 'pa_atomic_load(&(b)->_ref) > 0' failed at pulsecore/memblock.c:590, function pa_memblock_unref(). Aborting.

```

So the workaround didn't work for me.

 Falk

---

### Post by DGhost001 on 2012-11-01
Ok another short update.

I was able to pinpoint a pulseaudio option that directly triggers the bug.

In my /etc/pulse/default.pa config I have set the option

```

load-module module-udev-detect tsched=0

```

to workaround another bug which results in distorted sound on my system.

I changed this option to the default configuration that comes with ubuntu (tsched=1) "est volia"  the wine bug is gone. (But the distorted sound is back)
After reseting this option back to tsched=0 again the wine bug was back.

So vladdy if you are going to investigate the bug, don't forget to temporarily turn off the timer based and re-enable the old interrupt based scheduling in pulseaudio.

 Falk

---

### Post by vladdy on 2012-11-09
Still can't reproduce it after downgrading to old pulseaudio. Is there anything special about your config? What programs are you trying?

---

### Post by jrssystemsnet on 2012-11-09
FWIW, when I have problems with audio in Wine, closing the program in question and doing **pulseaudio -k** then re-running the program gets them sorted out.

This also fixes a really annoying bug in Chrome/Chromium where YouTube videos play on full-on fast-forward for no apparent reason.  So it seems like there's a bug upstream in Pulse IMO.

---

### Post by DGhost001 on 2012-11-09
Hi vladdy,
I don't think that there is something special within my config besides the already mentioned tshed=0 option. 
I've just appended my pulse audio config to this post, so you can compare it to yours and see if I missed something special. 
Within the tar you will also find a trace with +dsound,+pulse which may help you to find the problem.

Concerning the Programs which are failing:

For example every Game I try to run fails with the same error. They all worked without any problems in wine 1.5.15 and pulse audio and they still work fine if I use wine 1.5.16 without pulse audio.

Need for Speed Most Wanted (the original)
Battlefield 2
World in conflict
Prince of Persia WW

just to name a few.

 Falk

P.S.
 I tried the pulseaudio -k trick and it does not improve the situation.

---

### Post by vladdy on 2012-11-10
Ok so it's crashing nowhere in particular during normal operation, would it be possible to get a complete backtrace from the assertion failure?

---

### Post by DGhost001 on 2012-11-10
To get a useful backtrace for you, I compiled wine myself. 
So here is the backtrace:
```

Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:f77d9425 ESP:1aefe66c EBP:000019cb EFLAGS:00000202(   - --  I   - - - )
 EAX:00000000 EBX:0000195e ECX:000019cb EDX:00000006
 ESI:737d1000 EDI:f7623ff4
Stack dump:
0x1aefe66c:  7bd01aa4 f74ac1df f7623ff4 1aefe7a0
0x1aefe67c:  f74af825 00000006 1aefe720 00000000
0x1aefe68c:  00000000 00000000 7bd02ea8 f7624440
0x1aefe69c:  00000028 00000000 00000000 00000000
0x1aefe6ac:  7c1d3d64 7bd004b8 000000fe 7c16cc90
0x1aefe6bc:  7c1ede00 00000001 00000028 1aefe708
Backtrace:
=>0 0xf77d9425 __kernel_vsyscall+0x5() in [vdso].so (0x000019cb)
  1 0xf74ac1df gsignal+0x4e() in libc.so.6 (0x7bd01aa4)
  2 0xf74af825 abort+0x174() in libc.so.6 (0x7bd01aa4)
  3 0x7c17513c pa_memblock_unref+0x32b() in libpulsecommon-2.0.so (0x7bd01aa4)
  4 0x7c176a50 pa_memexport_process_release+0xef() in libpulsecommon-2.0.so (0x7bd01aa4)
  5 0x7c181fea in libpulsecommon-2.0.so (+0x34fe9) (0x7bd005d0)
  6 0x7c16cd58 in libpulsecommon-2.0.so (+0x1fd57) (0x00000000)
  7 0x7c1d5495 pa_mainloop_dispatch+0x104() in libpulse.so.0 (0x00000000)
  8 0x7c1d5973 pa_mainloop_iterate+0x52() in libpulse.so.0 (0x1aefea18)
  9 0x7c1d5a44 pa_mainloop_run+0x33() in libpulse.so.0 (0x1aefea18)
  10 0x7c64f249 pulse_mainloop_thread+0x68(tmp=0x0(nil)) [/wine-1.5.16/dlls/winepulse.drv/mmdevdrv.c:274] in winepulse (0x1aefea18)
  11 0x7bc75a00 call_thread_func_wrapper+0xb() in ntdll (0x1aefea28)
  12 0x7bc7882d call_thread_func+0x7c(entry=0x7c64f1e0, arg=0x0(nil), frame=0x1aefeb18) [/wine-1.5.16/dlls/ntdll/signal_i386.c:2522] in ntdll (0x1aefeaf8)
  13 0x7bc759de call_thread_entry_point+0x11() in ntdll (0x1aefeb18)
  14 0x7bc7e8d9 start_thread+0xe8(info=0x7ff5cfb8) [/wine-1.5.16/dlls/ntdll/thread.c:408] in ntdll (0x1aeff368)
  15 0xf762fd4c start_thread+0xcb() in libpthread.so.0 (0x1aeff468)
0xf77d9425 __kernel_vsyscall+0x5 in [vdso].so: movl     $0x2b,%ecx


```While experimenting with the bug I encountered several crashes at totally different code sections within wine. 
So I started reading your code and added some additional debug output to it. And  I found something very interesting which would be a very good explanation for the crash.

To the AudioClient_Initialize function I added an output to tell me how large the temporary buffer (which get handed out if pulse has not enough free frames available) is in the moment of its allocation.

And I got the following:
```

fixme:pulse:AudioClient_Initialize TMP Buffer 0x1327b350 alloced. Size 73728

```In dsound/mixer.c:663 there is a memset which clears the buffers that are returned by the IAudioRenderClient_GetBuffer() function.
Exactly there I added also an additional debug output the see if the size of the memset matches the size of the allocation for the buffer.

```

fixme:pulse:AudioRenderClient_GetBuffer 0x1327b150 Not using pulse locked data: 0 8187/9216 0/9216
fixme:dsound:DSOUND_PerformMix Buffer 0x1327b350 cleared. Frames 9216 221184

```The last number in the last line is the number of bytes that get actually cleared by the memset. If you compare that to the alloced size of the tmp buffer you see that there are a alot of bytes written behind the tmp_buffer.
This phenomena is not limited to the tmp_buffer. 
If the tmp_buffer gets not handed out on the first request then wine is crashing within the pulse library. If the tmp_buffer is handed out than the crash most likely occurs within dsound due to trashed function pointers.

An typical backtrace than looks like this
```

Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e186f3d ESP:0231ebbc EBP:0231ec94 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:1328d398 EBX:7e1afff4 ECX:13279518 EDX:00000000
 ESI:13279518 EDI:00000000
Stack dump:
0x0231ebbc:  1328d398 0231ec78 0231ed04 7bc484ae
0x0231ebcc:  7bc37091 0231ec48 0231ec94 7bc37091
0x0231ebdc:  7bc3715f 0006d1b8 0231ec34 7bc3715f
0x0231ebec:  7bc37091 132795c4 1327b0d0 0231ed04
0x0231ebfc:  7bc3715f 13121000 7e19975c 0231ed40
0x0231ec0c:  7bcb7ff4 132795c4 7bcb7ff4 0231ec38
Backtrace:
=>0 0x7e186f3d DirectSoundDevice_CreateSoundBuffer+0x57d(device=0x13279518, dsbd=0x231ed04, ppdsb=0x139f0678, lpunk=(nil), from8=0) [/wine-1.5.16/dlls/dsound/dsound.c:927] in dsound (0x0231ec94)
  1 0x7e1873f6 IDirectSound8Impl_CreateSoundBuffer+0x95(iface=0x132794f4, dsbd=0x231ed04, ppdsb=0x139f0678, lpunk=(nil)) [/wine-1.5.16/dlls/dsound/dsound.c:243] in dsound (0x0231ece4)
  2 0x00a20c3e in dead space (+0x620c3d) (0x010c1894)
0x7e186f3d DirectSoundDevice_CreateSoundBuffer+0x57d [/wine-1.5.16/dlls/dsound/dsound.c:927] in dsound: call    *0x4(%edx)

```So it seems to me there is a major disagreement between dsound and the winepulse driver how large the playback buffers are. 

Hopefully this post will help you to find the cause of the problem.

 Falk

---

### Post by DGhost001 on 2012-11-11
Yeehaaa I finally was able to fix the problem.

The Problem is that dsound requests a padded Wave format, which is not supported by the winepulse driver. But the driver accepts it without any problem which results in trashing the heap.

To fix it just add the following lines to the mmdevdrv.c in the function AudioClient_IsFormatSupported() directly before the "if (hr == S_OK || !out)"

```

    //No padding in the samples allowed!!
    if((fmt->nChannels * fmt->wBitsPerSample)/8 != fmt->nBlockAlign)
    {
      FIXME("Unsupported padded Sample format requested");
      hr = S_FALSE;
    }

```Furthermore I would recommend to improve the checks for the supplied wave format in the AudioClient_Initialize function, to catch all formats that are not supported by pulseaudio.

 Falk

---

### Post by Nilladar on 2012-11-12
Where can I find this mmdevdrv.c file to add these lines?

---

### Post by vladdy on 2012-11-12
Oh.. derp

Have a patch:
```
diff --git a/dlls/dsound/primary.c b/dlls/dsound/primary.c
index 981fc02..a1056f0 100644
--- a/dlls/dsound/primary.c
+++ b/dlls/dsound/primary.c
@@ -157,7 +157,11 @@ static WAVEFORMATEX *DSOUND_WaveFormat(DirectSoundDevice *device, IAudioClient *
             static int once;
             if (!once++)
                 FIXME("Limiting channels to 2 due to lack of multichannel support\n");
-            mixwfe->Format.nChannels = 2;
+
+            w = &mixwfe->Format;
+            w->nChannels = 2;
+            w->nBlockAlign = w->nChannels * w->wBitsPerSample / 8;
+            w->nAvgBytesPerSec = w->nSamplesPerSec * w->nBlockAlign;
         }
 
         if (!IsEqualGUID(&mixwfe->SubFormat, &KSDATAFORMAT_SUBTYPE_IEEE_FLOAT)) {


```

---

### Post by vladdy on 2012-11-12
Can you test the next patch too without the dsound patch?

Both patches should fix the issue, but I want to see if both patches fix the same issue first.

```
commit 756e43bfeb8b4aee34a1427d38abca38dfae5d62
Author: Maarten Lankhorst <maarten.lankhorst@canonical.com>
Date:   Mon Nov 12 17:15:49 2012 +0100

    winepulse: fix the checks in IsFormatSupported
    
    Thanks to DGhost001 for reporting and isolating the issue.

diff --git a/dlls/winepulse.drv/mmdevdrv.c b/dlls/winepulse.drv/mmdevdrv.c
index 643d55e..86dd10a 100644
--- a/dlls/winepulse.drv/mmdevdrv.c
+++ b/dlls/winepulse.drv/mmdevdrv.c
@@ -1443,6 +1443,10 @@ static HRESULT WINAPI AudioClient_IsFormatSupported(IAudioClient *iface,
         }
     }
 
+    if (fmt->nBlockAlign != fmt->nChannels * fmt->wBitsPerSample / 8 ||
+        fmt->nAvgBytesPerSec != fmt->nBlockAlign * fmt->nSamplesPerSec)
+        hr = S_FALSE;
+
     if (hr == S_OK || !out) {
         CoTaskMemFree(closest);
         if (out)

```

---

### Post by DGhost001 on 2012-11-12
I can confirm both patches are fixing the problem independent from each other. 

But the first patch also fixes the static noise I got, while using the a52 pulse audio sink with my and your second patch. 
For Analog 5.1 output both patches make no difference, and both work.

@Nilladar
You find the mentioned file in the ubuntu wine source under dlls/winepulse.drv/mmdevdrv.c. But before you start compiling wine yourself, just wait I hope there will be an update soon as it is now know how to fix the problem.

 Falk

---

### Post by vladdy on 2012-11-12
Oh I was in fact hit by this, but valgrind wasn't enabled on the wine ppa so I didn't get warned about it. Probably why steam and steam games didn't work for me on the -rt kernel.

Some more digging, it seems I broke things most likely a long time ago when I originally reworked IsFormatSupported when I still had hope it could be included into wine. Sadly none of the tests in mmdevapi exposes the bug, and other drivers look affected too.

---

### Post by Nilladar on 2012-11-12
I guess I'll wait it out before I go recompile wine. Either way, nice work on the solve.

---

### Post by vladdy on 2012-11-12
wine1.5 - 1.5.17-0ubuntu4 uploaded, should be fixed there. I pushed it to multimedia.git too, hopefully someone watches that so that other distros can pick it up. :)

---

### Post by Aydos on 2012-11-14
I have never had a problem getting my Nvidia drivers to work or getting Wine set up to play nice with any of my games.

However, My mumble or mangler clients always seem to act up and this appears to be something I need to try.

What steps do I need to take to try and run this pulseaudio version of Wine to run on my system and see if it helps?

---

### Post by vladdy on 2012-11-15
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get install wine1.5

Should work for quantal and precise. Recompile might broken on quantal, I compile for precise only and copy the binaries to quantal.

---

### Post by LillyDragon on 2012-11-20
Nope, nothing. D: I tried it and the terminal just gave me an error, since apparently there wasn't an installation candidate.

---

### Post by xclusive585 on 2012-12-18
Curious if this PPA build with winepulse supports 5.1 or 7.1 surround? I haven't seen any indication that it does so I'm curious.

---

### Post by A Nonny Moose on 2012-12-29
Hmmm.  I just updated from 1.4.1 to 1.5.20 to test the newest release and my app. crashed.

Here is my console log:

fixme:win:EnumDisplayDevicesW ((null),0,0x32ef7c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32eecc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f50c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f4ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f4ec,0x00000000), stub!
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit [http://ubuntuforums.org/showthread.php?t=1960599](http://ubuntuforums.org/showthread.php?t=1960599)


Which is how I got to here.  Interestingly enough, the app quit on that final line denying the Winepulse routines.

The app is SimCity 4 Deluxe digital download (v. 1,1,641).

I tried to back out to 1.4.1 but it is broken in the distribution.

Suggestions?

Further to this the dump of my app shows the crash occured in the sound module:
Exception module:  C:\windows\system32\dsound.dll.

When patching general use software it would be nice to have tested it more rigorously.  Since I can't back out due to nonsense at the distro, I am no longer able to kill time using this app.

---

### Post by wiebeest on 2012-12-29
> **A Nonny Moose said:**
> Hmmm.  I just updated from 1.4.1 to 1.5.20 to test the newest release and my app. crashed.[/url]


Which is how I got to here.  Interestingly enough, the app quit on that final line denying the Winepulse routines.

The app is SimCity 4 Deluxe digital download (v. 1,1,641).

I tried to back out to 1.4.1 but it is broken in the distribution.

Suggestions?

When patching general use software it would be nice to have tested it more rigorously.  Since I can't back out due to nonsense at the distro, I am no longer able to kill time using this app.

It seems you are not the only one with the latest update of wine crashing. I've found them all across the boards. The version 1.5.20 definitely is flawed. Check my post here below.
 
I get these same errors across a melange of different games: [http://ubuntuforums.org/showthread.php?p=12428159#post12428159]("http://ubuntuforums.org/showthread.php?p=12428159#post12428159")

---

### Post by MrRtd on 2012-12-29
> **wiebeest said:**
> It seems you are not the only one with the latest update of wine crashing. I've found them all across the boards. The version 1.5.20 definitely is flawed. Check my post here below.
 
I get these same errors across a melange of different games: [http://ubuntuforums.org/showthread.php?p=12428159#post12428159]("http://ubuntuforums.org/showthread.php?p=12428159#post12428159")
Yes this is affecting me too. Very annoying.

---

### Post by A Nonny Moose on 2012-12-31
A new "version" of 1.5.20 came in from the distro today.  It appears to have been fixed now.;)

---

### Post by tankypon on 2013-01-02
I just test it today. And of course, the bug have been fixed :)

---

### Post by A Nonny Moose on 2013-01-13
Got a distro update to wine-1.5.21.

All is well with the app that I run.  The improvement in sound quality is very noticeable.

---

### Post by meriley on 2013-02-28
I have a strange issue where my output audio(what i hear) is fine but my input audio (Microphone) [COLOR=#000000][FONT=Verdana]sound like a chipmunk and its choppy.
[/FONT][/COLOR]
Mic works fine outside of wine.

Running 1.5.24

Also as you can see im having issues with steam updating. But thats a seprate issue.

```
[COLOR=#007700][FONT=Courier New]fixme:heap:HeapSetInformation (nil) 1 (nil) 0[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f0054c0, 0x3f036b40, 0x3f036b38[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f0054c0, 0x3f036b78, 0x3f036b70[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f0054c0, 0x3f036b08, 0x3f036b00[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f0054c0, 0x3f036bb0, 0x3f036ba8[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f0054c0, 0x3f036be8, 0x3f036be0[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:heap:HeapSetInformation (nil) 1 (nil) 0[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:43] uninstalled manifest found in C:\Program Files (x86)\Steam\package\steam_client_win32.[/FONT][/COLOR]

[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:43] Found pending update[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:43] Applying update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:43] uninstalled manifest found in C:\Program Files (x86)\Steam\package\steam_client_win32.[/FONT][/COLOR]

[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:43] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:44] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:44] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:44] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:44] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:44] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:44] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:44] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:45] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:46] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Failed to clear up temporary update files used for rollback, continuing anyway[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Cleaning up...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:47] Update complete, launching...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:heap:HeapSetInformation (nil) 1 (nil) 0[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f0054c0, 0x3f036b40, 0x3f036b38[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f0054c0, 0x3f036b78, 0x3f036b70[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f0054c0, 0x3f036b08, 0x3f036b00[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f0054c0, 0x3f036bb0, 0x3f036ba8[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f0054c0, 0x3f036be8, 0x3f036be0[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]p11-kit: couldn't load module: /usr/lib32/pkcs11/gnome-keyring-pkcs11.so: /usr/lib32/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:iphlpapi:NotifyAddrChange (Handle 0x5b9d69c, overlapped 0x59a9970): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:winsock:WSALookupServiceBeginW (0x5b9d79c 0x00000ff0 0x5b9d7e4) Stub![/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][0228/070553:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:dbghelp:elf_search_auxv can't find symbol in module[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventUnregister deadbeef: stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventUnregister deadbeef: stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventUnregister deadbeef: stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventUnregister deadbeef: stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventUnregister deadbeef: stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]err:ole:CoGetClassObject class {dff32fea-3331-48da-a272-ccfc238695be} not registered[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]err:ole:CoGetClassObject class {dff32fea-3331-48da-a272-ccfc238695be} not registered[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]err:ole:create_server class {dff32fea-3331-48da-a272-ccfc238695be} not registered[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]err:ole:CoGetClassObject no class object {dff32fea-3331-48da-a272-ccfc238695be} could be created for context 0x17[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:48] Verifying installation...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:48] BVerifyInstalledFiles: resource/overlay_italian.txt should be -1[/FONT][/COLOR]


[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:48] Downloading update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:48] Checking for available updates...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:49] Download complete.[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:49] uninstalled manifest found in C:\Program Files (x86)\Steam\package\steam_client_win32.[/FONT][/COLOR]

[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:49] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:49] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:49] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:49] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:49] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:49] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:49] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:50] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:50] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:51] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Extracting package...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Installing update...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] BCommitUpdatedFiles: failed to rename ./vstdlib_s.dll -> ./vstdlib_s.dll.old[/FONT][/COLOR]

[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] Failed to apply update, reverting...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:52] uninstalled manifest found in C:\Program Files (x86)\Steam\package\steam_client_win32.[/FONT][/COLOR]

[COLOR=#007700][FONT=Courier New][2013-02-28 07:05:56] uninstalled manifest found in C:\Program Files (x86fixme:ntdll:NtLockFile I/O completion on lock not implemented yet[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:win:RegisterDeviceNotificationA (hwnd=0x20068, filter=0x33e3dc,flags=0x00000004) returns a fake device notification handle![/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:win:RegisterDeviceNotificationW (hwnd=0x10110, filter=0x102ce98c,flags=0x00000000) returns a fake device notification handle![/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:win:EnumDisplayDevicesW ((null),0,0x33df68,0x00000000), stub![/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:SHAppBarMessage unknown msg: 4[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:SHAppBarMessage unknown msg: 4[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:SHAppBarMessage unknown msg: 4[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:winsock:WSALookupServiceBeginW (0x77fe1dc 0x00000ff0 0x77fe224) Stub![/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][0228/070603:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]err:ole:RevokeDragDrop invalid hwnd 0x1011c[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:win:RegisterDeviceNotificationA (hwnd=0x20112, filter=0x33e970,flags=0x00000004) returns a fake device notification handle![/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:win:UnregisterDeviceNotification (handle=0xcafeaffe), STUB![/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:win:UnregisterDeviceNotification (handle=0xcafecafe), STUB![/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:win:UnregisterDeviceNotification (handle=0xcafecafe), STUB![/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:iphlpapi:CancelIPChangeNotify (overlapped 0x59a9970): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]warning: The VAD has been replaced by a hack pending a complete rewrite[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]Shutting down. . .[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New])\Steam\package\steam_client_win32.[/FONT][/COLOR]

[COLOR=#007700][FONT=Courier New][2013-02-28 07:06:00] Background update loop checking for update. . .[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:06:00] Checking for available updates...[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New][2013-02-28 07:06:02] uninstalled manifest found in C:\Program Files (x86)\Steam\package\steam_client_win32.[/FONT][/COLOR]

[COLOR=#007700][FONT=Courier New][2013-02-28 07:06:03] Download complete.[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventUnregister deadbeef: stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventUnregister deadbeef: stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventUnregister deadbeef: stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventUnregister deadbeef: stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:advapi:EventUnregister deadbeef: stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]Assert( Assertion Failed: (::DeleteObject( hOldBitmap )) ):surface_gdiwin32.cpp:1839[/FONT][/COLOR]

[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub[/FONT][/COLOR]
[COLOR=#007700][FONT=Courier New]fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub[/FONT][/COLOR]
```

when I use my mic I get "[COLOR=#007700][FONT=Courier New]warning: The VAD has been replaced by a hack pending a complete rewrite"[/FONT][/COLOR]

---

### Post by skrech on 2013-04-03
Hey, I've just installed wine1.5 from the PPA and noticed that winecfg is showing winealsa.drv as the audio driver? How can I set it to use winepulse? 
I want to try winepulse because foobar2000 in wine is making occasional audio dropouts/pops/clicks when, for example, I open new tab in chrome, or minimize/maximize some window. Is it even possible to remedy these dropouts, because I'm new to wine and don't know how it was before and the documentation and all the information is MESS scattered all over the Internet.

---

### Post by Projector on 2013-04-16
I'd like to +1 the popping and clicking sound issue.  I'm trying to play LOTRO right now and I have to have the master volume silenced due to the racket it's making.  I'm running wine 1.5.28 on linux mint 14 64 bit.

---

### Post by irishetalon007 on 2013-04-26
> **Projector said:**
> I'd like to +1 the popping and clicking sound issue.  I'm trying to play LOTRO right now and I have to have the master volume silenced due to the racket it's making.  I'm running wine 1.5.28 on linux mint 14 64 bit.
Whenever I run into this, doing a ```
sudo killall pulseaudio
``` usually fixes it for me. just run that code in terminal before executing your game in wine.

---

### Post by vladdy on 2013-05-01
It seems there was a bug in pulseaudio that you're probably hitting. Upgrading to pulseaudio 3.0 should fix this.

[http://cgit.freedesktop.org/pulseaudio/pulseaudio/commit/?id=29f064aa3d3a83e275361aad3f9e7efdc84b8ad0](http://cgit.freedesktop.org/pulseaudio/pulseaudio/commit/?id=29f064aa3d3a83e275361aad3f9e7efdc84b8ad0)

---

### Post by vladdy on 2013-05-01
About the microphone support being broken, I did an initial port of dsound to the new mmdevapi interface but it was rejected and someone else's implementation got merged, if steam was using directsound for microphone recording you would probably be interested in my version of capture, but I'd have to dig that one up first. It was rejected on the grounds of being a rewrite, sigh..

---

### Post by K1773R on 2013-05-04
where can i get the patches? you arent supplying em which is really bad... not everyone is using the ppa and since i would like this in my wine buils too, i need the patches.
pls supply the patches (for each version u push) just like this guy did earlier: [http://art.ified.ca/?page_id=40](http://art.ified.ca/?page_id=40)

---

### Post by vladdy on 2013-05-08
I don't need to supply patches, [http://repo.or.cz/w/wine/multimedia.git/shortlog](http://repo.or.cz/w/wine/multimedia.git/shortlog) has the git tree. I rebase it every time there is a wine release.

You can use git format-patch to make patch files out of it, or use git diff to make a single diff.

But if you grab the wine source from launchpad or with apt-get source, the patches used against wine are in wine-1.5*/debian/patches.

---

### Post by K1773R on 2013-05-16
thanks, git is fine!
consider adding the link of the git to first post ;)

greetings

---

### Post by vladdy on 2013-05-22
Done, I added a warning about sound quality with pulseaudio < 3.0 too, with a link to the fix.

---

### Post by asd321 on 2013-06-19
Hi, I'm using dsound.dll from windows 7 and winepulse (only way to get 5.1 sound in games?). Sometimes it output noise, something like buffer loop. Best way to reproduce it is pause music in foobar2000. It doesn't happend in alsa driver.

---

### Post by Tommystephen01 on 2013-07-19
Hi all,
This is Tommy Stephen, i am the new user of this forum support me.
oh! this is a very informative
post! i actually enjoyed reading this..

---

### Post by acodea on 2013-10-31
what is the ppa as added to synaptic. Answering this will help for me to learn, for future reference.

---

### Post by culted86 on 2013-11-30
how can i extract all the patches with "git format-patch"? the best i could do is "git format-patch -1" but that only gives me the first commit?

---

### Post by Hans_Stephensen on 2014-02-17
Hi brilliant people.

I'm having sound issues in Starcraft 2 under Ubuntu 13.10 using wine 1.7.12 and pulseaudio 4.0.

I have so far not been able to find a fix or workaround. As soon as I have logged on to battle.net, every sound played, be it interface sound, game effects or ingame voices, will be played on what sound like on top of each other and even itself. So the loggin sound "bling" becomes "bliblilinglingngngnggg". It doesn't seem to chop og distort the sound just repeat it several times. There's no fuzzing og buzzing either. It be causing severe lag during battles as well, but I'm not sure.

Disabling "winepulse.drv" in winecfg stops the sound reapeating problem, but yields horrible sound and lag... not suprisingly.
One thread on a problem I hoped was the same, suggested changing resampling method to src-linear. That did nothing, so it's back to default.

I really hope this thread can shed some light on the problem. I'm craving for a fix or workaround. :)

---

### Post by mlankhorst on 2014-03-04
can you set windows version to win vista or newer? That should fix sound for you.  Pulseaudio 5.0 seems to have introduced a regression when used with usb headphones, reverting 826c8f69d34ef49e86fe0ab6c93c1ffba8916131 fixes it. I'm talking to the pa devs about possible fixes.

---

### Post by mlankhorst on 2014-03-04
if the upstream for the original wine git tree is origin, and you're working on a branch with the patches it's simply  git format-patch -o /tmp/out origin/master

---

### Post by TheRealBecks on 2014-06-16
Pizza Connection 2 isn't working at some point, see [http://bugs.winehq.org/show_bug.cgi?id=36744](http://bugs.winehq.org/show_bug.cgi?id=36744)

So, yeah, this "bug" is still out there and "WINENOPULSE=1 wine Pizza2.exe" is not working :(

---

### Post by HunterZ on 2015-11-02
It's finally happening: winepulse is in the process of being merged into the official Wine source tree! Thanks for all the hard work everyone.

Why it happened: As far as I can tell, Wine forked into a wine-staging project that was willing to include more edgy patches, and this eventually resulted in the Wine team deciding to change how they were running things. As a result, Wine and wine-staging teams are merging back together, with wine-staging acting as a proving ground to give patches a place to mature until they're ready to go into official Wine. Pulseaudio was in wine-staging, and was a major target that people identified for bringing over to Wine under the new system.

---

### Post by yoshii on 2015-11-23
> **HunterZ said:**
> It's finally happening: winepulse is in the process of being merged into the official Wine source tree! Thanks for all the hard work everyone.

Why it happened: As far as I can tell, Wine forked into a wine-staging project that was willing to include more edgy patches, and this eventually resulted in the Wine team deciding to change how they were running things. As a result, Wine and wine-staging teams are merging back together, with wine-staging acting as a proving ground to give patches a place to mature until they're ready to go into official Wine. Pulseaudio was in wine-staging, and was a major target that people identified for bringing over to Wine under the new system.

That's really cool!  Congratulations.  And thanks.

---

### Post by yoshii on 2015-12-06
@expUfone, I don't know what you are advertising for.  But anyways, I use Wine alot for digital audio workstation programs as well as image editors and some Windows utilities and it works well enough to legitimize my switch away from Windows OS.  It's not perfect, but it's excellent in my opinion.  Development of it is somewhat slow, but some things will probably stabilize more over time.  Don't give up on it yet.

---

