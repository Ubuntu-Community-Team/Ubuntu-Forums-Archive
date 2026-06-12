---
title: "DarkIce, Ices0 or anything to stream mp3 to icecast from soundcard"
date: 2006-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Beamerboy on 2006-07-16
Having a nightmare with this lot tonight.

First of all I figured "There is bound to be an xmms plugin to stream my mp3s to my icecast server." So I popped open synaptic and sure enough there was xmms-liveice.  Installed in a snap, so I had a play with the configuration and set it up how I wanted it.  Enabled the plugin and xmms crashed.  Managed to stop it crashing only to get some very funky noise through (it seems xmms-liveice is not very ALSA friendly).

So I tried the LiveIce client, needless to say not very friendly with ALSA either:
```

Initialising Soundcard

 21561:Error: Failed to open sound device

```

So I tried Ices2, oops only ogg support there which will only support 1 channel (mono) instead of 2 channel (stereo) for some odd reason.  No matter what I do it will only stream the left channel.

Heard about some Ices0 that will stream MP3 but lo-and-behold not available in the repos for 64bit Dapper.

So I dug around a bit more and found ezstream.  It actually compiled and works if you give it a playlist, try and use stdin as advised and you are greeted with nothing.  No crashes, but nothing gets sent through the network, it just seems to hang.

So DarkIce and Darksnow seemed like a good idea, but since the version in the repos is ogg only (so only mono via the left channel) I tried to build darkice myself using the --with-lame-prefix=/usr/lib --with-alsa
```

checking for lame library at /usr/lib ... found at /usr/lib
checking for alsa libraries at /usr ... found at /usr

```
Well that looks spiffing, lets make;
```

LameLibEncoder.cpp: In member function ‘virtual bool LameLibEncoder::open()’:
LameLibEncoder.cpp:82: error: cast from ‘lame_global_flags*’ to ‘int’ loses precision
LameLibEncoder.cpp:85: error: cast from ‘lame_global_flags*’ to ‘int’ loses precision
make[2]: *** [LameLibEncoder.o] Error 1
make[2]: Leaving directory `/home/paladine/darkice-0.17.1/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/paladine/darkice-0.17.1/src'
make: *** [all-recursive] Error 1
paladine@main:~/darkice-0.17.1$

```
Oh dear now thats not so good and after such a promising start too?

So I tried VLC again to no avail and finally MusE which simply refuses to even start because it can't find a sequencer.

Sooooo

I guess my question is, has anyone managed to get mp3 streaming to icecast straight from the soundcard as opposed to using a playlist, to work on Dapper 64bit with alsa?  If so, what did you use and how did you configure it please?

I think darkice is the way to go if I can get past these build errors.

All help appreciated.

Beamerboy

---

### Post by rocktorrentz on 2006-10-29
I've had this exact problem by with Kubuntu Edgy AMD64. If anyone has a solution it would be great; i've had to stop running my little hobby shoutcast station because of switching to linux.

---

### Post by RAOF on 2006-10-29
> **Beamerboy said:**
> ...
So I tried the LiveIce client, needless to say not very friendly with ALSA either:
```

Initialising Soundcard

 21561:Error: Failed to open sound device

```
...

You **may** have some luck installing and using **alsa-oss**.  ALSA includes some OSS emulation, and running (from a terminal) **aoss *command*** *should* make *command* use ALSA nicely.

As for DarkIce, it seems to be (stupidly) assuming that a pointer is the same size as an int.  Aaargh, stupid non-portable code!  You may well be able to make it compile by changing the **int**s to **intptr_t**s, the correct type if you ever want to treat a pointer as an integer.  Is darkice still maintained?  If so, you could ask them to fix their broken code!

**EDIT:**
I've fixed the Failure-To-Build-From-Source.  Could someone test the packages found in the "misc" section of my repository?  It's built with vorbis, lame, and faac support.  [http://raof.dyndns.org/falcon/dists/edgy/misc/](http://raof.dyndns.org/falcon/dists/edgy/misc/)

Once someone's verified that it works, we can open a bug on Launchpad, or with the developers, or somewhere.

---

### Post by rocktorrentz on 2006-10-30
I've installed your darkice and the normal repository darksnow along with liblame0 liblame-dev and lame. But darksnow says darkice isn't streaming and the output at the client i.e. a windows box running winamp is almost too quiet to hear. I have installed aumix as suggested in a tutorial I read and turned everything up to 100 except the mic and this changes nothing. 

However I have managed to make the XMMS plugin work properly so I shall be using that until a working solution for amarok is here.

Thanks for you effort
rocktorrentz

---

### Post by enzomatrix on 2006-10-30
Darkice only works by using OSS for me.
As ALSA gives OSS emulation I've only changed the config file to use the OSS device.

---

### Post by rocktorrentz on 2006-10-31
So I don't have to install any extra OSS emulation tools? What exactly did you change to make it work properly for you?

thanks in advance 
rocktorrentz

---

### Post by enzomatrix on 2006-10-31
I just put /dev/dsp as input device.
This is the input part of my darkice.cfg file.
```
# this section describes the audio input that will be streamed
[input]
device          = /dev/dsp  # OSS DSP soundcard device for the audio input
sampleRate      = 11025     # sample rate in Hz. try 11025, 22050 or 44100
bitsPerSample   = 16        # bits per sample. try 16
channel         = 1         # channels. 1 = mono, 2 = stereo
```

---

### Post by rocktorrentz on 2006-11-01
Those settings are the same as mine except I am using a 44100 sample rate. Are you using an ogg output?

---

