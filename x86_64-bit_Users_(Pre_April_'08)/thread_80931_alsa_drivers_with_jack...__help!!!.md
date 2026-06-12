---
title: "alsa drivers with jack...  help!!!"
date: 2005-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubonetu on 2005-10-23
I know I did this on my hoary installation, I had alsa running so I could use it with jack (I'm going for less lag in ardour and for kicks, creox and jack-rack w/ distortion).  Here's what I get from jack:
```

07:21:02.675 Startup script...
07:21:02.676 artsshell -q terminate
07:21:03.155 Startup script terminated with exit status=256.
07:21:03.157 JACK is starting...
07:21:03.158 /usr/bin/jackd -v -dalsa -dhw:0 -r44100 -p1024 -n2
07:21:03.179 JACK was started with PID=6628 (0x19e4).
getting driver descriptor from /usr/lib/libjack0.80.0-0/jack_alsa.so
getting driver descriptor from /usr/lib/libjack0.80.0-0/jack_dummy.so
getting driver descriptor from /usr/lib/libjack0.80.0-0/jack_oss.so
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
registered builtin port type 32 bit float mono audio
loading driver ..
new client: alsa_pcm, id = 1 type 1 @ 0x100208e0 fd = -1
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
ALSA: cannot set number of periods to 2 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
07:21:03.633 JACK was stopped successfully.
07:21:05.354 Could not connect to JACK server as client.
```

I've installed the drivers succesfully (though I didn't know what to put in my "kernel module conifig" [where ever that is]) but still don't have a working alsa pipeline:  results from "Multimedia Systems Selector":

```
Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'
```

Anyway, any help would be great.
Thanks,
Ubonetu

---

### Post by franzfranz on 2005-10-25
i have the same problem! Any Solutions?

---

### Post by ubonetu on 2005-10-25
Not yet.  I recompiled everything and added the sound modules from the INSTALL file.  Jack still won't run with alsa.  Here's what I'm getting from muse:

```
bones@peter:~$ sudo muse &
[3] 5433
bones@peter:~$ no locale <muse_en_US.UTF-8>/</usr/share/muse/locale>
starting with default template
  name2route: <alsa_pcm:playback_1> not found
  name2route: <alsa_pcm:playback_2> not found
cca_open_socket: could not connect to host 'localhost', service '14541'
cca_init: could not connect to server 'localhost' - disabling ladcca

```

I'm seriously thinking of paying for support but I don't have one hundred dollars to spend.  

Thanks for listening,
ubonetu

---

### Post by Ububurns on 2006-01-19
I'm having a similar problem, and would love for anyone to help out.

My sound card worked with jack, without having to configure anything when in my PC.

Now, on a brand new install in a Mac, with that same card, I'm receiving: 

[I]Sorry. The audio interface "hw:1" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa[/I]

Is there something missing?  Do I have to manually configure the sound card?  I'm not terribly sure where to start...

---

### Post by SectionThree on 2006-01-19
Here's a quick but temporary fix :

Open the Volume Control app (I think it's either in System Tools or Sound and Video-- I can't look right now because I'm running OS X right now) and you'll see a bunch of volume sliders, and underneath each of them there's a little speaker icon. If there's a big red X over it, that means it's muted. Click on it to un-mute it and the sound should come on.  You'll have to do this each time you insert or remove anything from the jack though...

---

### Post by SectionThree on 2006-01-19
Oh yeah, I'm running Breezy and have never seen Hoary, so please use this bit of information to take my advice with a grain of salt, and GOOD LUCK!:cool:

---

### Post by Ububurns on 2006-01-21
Thankyou for the suggestion - I tried it, but had no luck, unfortunately.

The problem people have described doesn't seem do with muted inputs or outputs.  If it did, then the Jack daemon would be able to run, but there would be no audio capture coming through.  This happens to be the case on PCs (and has been fairly easy to get going properly).

The problem seems to be more in relation to getting the jack daemon to run **at all** on a Mac, in Ubuntu.  After trying for quite a while, and from reading what is in this thread, it seems that jackd is plain outright refusing to accept and use any ALSA device.  Thus the "cannot load module alsa".

Please, if anyone is having any success with getting Jack to work, in Breezy on a PPC, let us know!

---

### Post by 23meg on 2006-01-21
What sound device are you using? It looks like a device-specific problem to me; putting the correct configuration settings for your device in your ~/.asoundrc file might fix this. Many ready asoundrc files are available somewhere in the official ALSA website, along with relevant discussion.

---

### Post by Ububurns on 2006-01-24
Thanks, 23meg.  I thought it might be alsa configuration too.  I'm using a Sound Blaster Live! card.

I have noticed that I have no .asoundrc file in my home directory, or anywhere.  In fact, there seems to be no asound.conf file either!  Yet I am able to use my sound card with most gnome applications, and alsa (although without jack).  And apparently, ALSA doesn't require either of those two files to be able to function properly.

I'm beginning to think the version of Jack that came with Breezy, for PPC, doesn't work at all (and it's not the most recent release anyway).  There is a version 0.100.4 for PPC in Debian Unstable but unfortunately packages.debian.org is down - and has been for a while.  I would like to be able to try it out, just too see.

Is ANYONE having any success with getting Jack to run, on PPC architecture?

---

### Post by stmiller on 2006-03-27
I'm replying to an old post, but I can't get jackd to run. Getting the same errors.

```
15:54:10.622 Startup script...
15:54:10.625 artsshell -q terminate
15:54:10.909 Startup script terminated with exit status=256.
15:54:10.912 JACK is starting...
15:54:10.915 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -S -i2 -o2
15:54:10.923 JACK was started with PID=12365 (0x304d).
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|2|2|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
ALSA: cannot set number of periods to 2 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
15:54:10.951 JACK was stopped successfully.
15:54:12.963 Could not connect to JACK server as client.
```

Powermac G5 Dual 2Ghz. Jack just doesn't want to start. I've tried it in capture mode only, and playback mode only, etc. Nothing. Anyone?

```
stmiller@stmiller:~$ uname -a
Linux stmiller 2.6.12-10-powerpc64-smp #1 SMP Sat Mar 11 17:03:13 UTC 2006 ppc64 GNU/Linux

```

---

### Post by stmiller on 2006-03-27
Okay I compiled Jack 0.100.0 to see if that would fix it. It loads the kernel module, but still gets errors of client connection. I think it's fair to say the jack package in Breezy PPC is bad, as at least this one from source loads the alsa driver. I'm going to try different settings in qjackctl and see if I can get it to work.

```
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|soft-mode|16bit
control device hw:0
configuring for 44100Hz, period = 128 frames, buffer = 2 periods
nperiods = 3 for capture
nperiods = 3 for playback
26879 waiting for signals
17:55:03.433 Could not connect to JACK server as client.
registered builtin port type 32 bit float mono audio
new client: alsa_pcm, id = 1 type 1 @ 0x10022a68 fd = -1
new buffer size 128
registered port alsa_pcm:capture_1, offset = 512
registered port alsa_pcm:capture_2, offset = 1024
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:playback_2, offset = 0
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
late driver wakeup: nframes to process = 512.
late driver wakeup: nframes to process = 384.
late driver wakeup: nframes to process = 512.
late driver wakeup: nframes to process = 256.
late driver wakeup: nframes to process = 896.
late driver wakeup: nframes to process = 640.
late driver wakeup: nframes to process = 384.
load = 0.0172 max usecs: 1.000, spare = 2901.000
17:55:04.641 Could not connect to JACK server as client.
late driver wakeup: nframes to process = 768.
late driver wakeup: nframes to process = 256.
late driver wakeup: nframes to process = 384.
late driver wakeup: nframes to process = 256.
late driver wakeup: nframes to process = 384.
load = 0.0258 max usecs: 1.000, spare = 2901.000
late driver wakeup: nframes to process = 384.
late driver wakeup: nframes to process = 640.
late driver wakeup: nframes to process = 256.
late driver wakeup: nframes to process = 256.
late driver wakeup: nframes to process = 256.
late driver wakeup: nframes to process = 256.
late driver wakeup: nframes to process = 256.
late driver wakeup: nframes to process = 384.
17:55:06.044 JACK is stopping...
jack main caught signal 15
starting server engine shutdown
stopping driver
unloading driver
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 1.000, engine deleted
no message buffer overruns
cleaning up shared memory
cleaning up files
unregistering server `default'
17:55:06.086 JACK was stopped successfully.
```

---

### Post by stmiller on 2006-03-27
To compile jack from source with alsa do this:

```
$ ./configure --enable-alsa
```

And make sure all the libalsa type packages are installed. Esp. libclalsadrvc2c

---

### Post by stmiller on 2006-03-27
Okay tried the version of jack in CVS, and still no go. Same errors as the current release I just tried. Grrr....
```
jackd 0.101.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
registered builtin port type 32 bit float mono audio
new client: alsa_pcm, id = 1 type 1 @ 0x10022a68 fd = -1
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|64|2|44100|0|0|nomon|swmeter|soft-mode|16bit
control device hw:0
configuring for 44100Hz, period = 64 frames, buffer = 2 periods
nperiods = 3 for capture
nperiods = 3 for playback
new buffer size 64
registered port alsa_pcm:capture_1, offset = 256
registered port alsa_pcm:capture_2, offset = 512
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:playback_2, offset = 0
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
6968 waiting for signals
18:10:15.236 Could not connect to JACK server as client.
late driver wakeup: nframes to process = 256.
late driver wakeup: nframes to process = 128.
late driver wakeup: nframes to process = 896.
late driver wakeup: nframes to process = 384.
late driver wakeup: nframes to process = 384.
late driver wakeup: nframes to process = 128.
late driver wakeup: nframes to process = 128.
late driver wakeup: nframes to process = 384.
late driver wakeup: nframes to process = 128.
late driver wakeup: nframes to process = 448.
late driver wakeup: nframes to process = 256.
late driver wakeup: nframes to process = 128.
[SNIP]
late driver wakeup: nframes to process = 128.
late driver wakeup: nframes to process = 448.
load = 0.0603 max usecs: 1.000, spare = 1450.000
18:10:18.381 JACK is stopping...
jack main caught signal 15
starting server engine shutdown
stopping driver
late driver wakeup: nframes to process = 192.
unloading driver
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 1.000, engine deleted
no message buffer overruns
cleaning up shared memory
cleaning up files
unregistering server `default'
18:10:18.496 JACK was stopped successfully.
```

---

### Post by Ububurns on 2006-03-28
Glad to see it's not just me!  Yet, at the same time... it isn't great either.

I haven't heard of even one report of anyone successfully running Jack on a Mac.  Sad, because I bought the Mac to use Jack...

It seems a bug needs to be filed..?

---

### Post by linear on 2006-03-28
[quote=Ububurns]It seems a bug needs to be filed..?[/quote]
 
Yes, but is the bug in jack or in alsa?

---

### Post by stmiller on 2006-03-28
I contacted the package maintainer, who said installing a CVS or other version of jack would be problematic, as the ubuntu version is pre-set to point to certain files, etc. in the ubuntu install.

 Other than that, he had no help. This is very bad, as lots of computer music folks using OS X are looking for a PPC Linux distro to dual boot. But with no jack there's not much you can do, but look to a different distro. :(

I do know that trying the current stable and CVS versions of jack that the alsa module DID load. Though there were still "Could not connect to JACK server as client" errors.

---

### Post by stmiller on 2006-03-28
Hi Ububurns:

Are you running on a G4 or G5?

---

### Post by Ububurns on 2006-03-30
I'm using a G4.

The sound card is from a machine that allowed jack to work flawlessly (a PC).  The sound card itself is working fine in the Mac - but jack doesn't really care... :(  

I am of the opinion that it may be a problem with ALSA - but that's just a hunch.

---

### Post by stmiller on 2006-03-30
Okay hmm.. Well it's not CPU specific then. I'm on a G5. I'm going to have to install Fedora PPC, unfortunately. 
 I tried the dapper version of ubuntu (knowing that Rosegarden won't work in dapper now; lack of depends) to see if jack would load, and no. Same errors, does not work. I may come back to ubuntu later if it is fixed.

---

### Post by Ububurns on 2006-04-07
I've been using a sound card from a PC in my Mac.

Is that potentially the reason Jack won't run?

It's confusing me, as Audacity is recording flawlessly, and playback of media is just as perfect.  Thus I am led to believe that running pc hardware on a Mac is feasible.

However the failure of jack seems to indicate otherwise.

---

### Post by christhemonkey on 2006-04-07
To work out if the problem is ALSA or jack, try
```
aplay amediafile.wav
```
obviously replacing amediafile.wav with some form of music file.
If it fails then you have a broken alsa installation.
Report any errors back here.

---

### Post by stmiller on 2006-04-07
What exact soundcard do you have? If it's supported by alsa, it should work.  Here's the alsa database:

[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

And my sound is the onboard powermac sound (powermac dual G5 PCIX model). Jackd will not allow the alsa module to load, and thus no audio programs can run that depend on jack.


This is a serious problem; no major audio apps will work without jack. Can anyone help? Or is there anyone out there who can successfully run jack on ubuntu ppc?

---

### Post by Ububurns on 2006-04-08
That was a quick way to be certain that alsa is working - and yes, I can verify that alsa is working fine.

Yes, the card is supported.  It's just a SB Live! PCI card.

When in a PC, jackd is very willing to use this exact sound card.

However, on a Mac, as with every case I've heard, there is no success.

---

### Post by stmiller on 2006-04-08
I have a soundblaster MP3+ USB / external soundcard which works with Jack/Alsa (in the past). I plugged it in, and it works fine as a sound card, but jackd still cannot load the alsa module. Same errors. So it's not the powermac internal sound, that's for sure. And looks like it's not your sound card either.

Jack didn't work in dapper either. :(

---

### Post by Ububurns on 2006-04-09
Right.  So we can be sure (it seems) that it is NOT a sound card compatibility issue.

Playing a sound with aplay seems to indicate it is NOT an ALSA issue.

Then, from what I can gather, this means that it is a problem with JACK.

If so, then, what are the next steps we can take? Surely in these next five or so weeks before the final version is released, we can get the jack problem fixed for Dapper!

---

### Post by stmiller on 2006-04-09
Try contacting the package maintainer. He told me it works fine for him, but that's not much help for the rest of us:

Robert Jordens <jordens@debian.org>

---

### Post by stmiller on 2006-04-10
[http://72.14.203.104/search?q=cache:8eOIQQjakwcJ:lists.debian.org/debian-multimedia/2005/05/msg00005.html+jackd+ppc&hl=en&gl=us&ct=clnk&cd=12](http://72.14.203.104/search?q=cache:8eOIQQjakwcJ:lists.debian.org/debian-multimedia/2005/05/msg00005.html+jackd+ppc&hl=en&gl=us&ct=clnk&cd=12)

I'm digging for answers. This page is helpful I'm determined to get jack going. You literally cannot run any major audio apps without it. I'm trying lots of stuff to figure out a fix. I'm trying things with my usb soundblaster card also to narrow down the problem.

---

