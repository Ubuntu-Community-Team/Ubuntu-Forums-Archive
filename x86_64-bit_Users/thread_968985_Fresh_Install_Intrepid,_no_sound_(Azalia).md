---
title: "Fresh Install Intrepid, no sound (Azalia)"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by ubernatural on 2008-11-03
Hi, I just installed Intrepid 64-bit, and I'm getting no sound :(  I've spent a couple hours hunting around with no luck...  I did try a few different things (like getting the latest alsa and building it), but that messed up my system a bit so I just reinstalled fresh so it'll be easier to get assistance...

output of aplay -l:
aplay: device_list:215: no soundcards found...

output (part) of lspci -v:
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 8249
	Flags: slow devsel, IRQ 16
	Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

There was no output from sudo modprobe snd-hda-intel.

All of these steps are taken from the Sound Troubleshooting guide.  I really have no idea what's going on, or what exactly these things are telling me.  All I know is that I've got no sound... :(  Can anyone help?

Thanks a bunch.

---

### Post by Yellow Pasque on 2008-11-03
How did you build the latest ALSA? Did you use this script? [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

Also, you can try OSS4, which I know has been reported successful for at least a few onboard ATI Azalia users. I can also personally vouch for it on my Biostar 780G board, though I haven't tried it with digital out or surround (I have a discrete sound card).

---

### Post by xigen on 2008-11-03
Well, I had plenty of troubles getting audio to work myself.

Here is what worked for me... AMD64, Delta 66 (m-audio) card:

1) install alsa-utilities, there is a GTK asoundconf utility ( system -> preferences --> choose sound card) which lets you choose sound cards.
* This let me choose the delta66 as opposed to the sound output from my motherboard. 

2) if that does not work, go in with a terminal and change the order of sound card probing/config
* see ubuntuforums.org/showthread.php?t=766683  .. the "Configuring default soundcards / stopping multiple soundcards from switching" section (it is a way down the page)

3) disable Pulseaudio.

... killall pulseaudio
* my (system -> preferences -> sound) worked when I killed pulseaudio.

... sudo apt-get remove pulseaudio

... then... in terminal,
type "sudo Nautilus".

Then browse in Nautilus and move the file "/etc/X11/Xsession.d/70pulseaudio" to trash.  ... I had trouble logging in when my system had this file.

hope that helps -- Rock on!

---

### Post by ubernatural on 2008-11-04
Temüjin - I hadn't tried that script earlier.  I tried it out but there was no change.

xigen - thanks for the suggestions.  I only have one sound card (onboard) in the box.  I tried disabling / removing pulseaudio in case that did something, but sadly it didn't change things either :(

I went through the OSS4 HowTo just now, also with no change.  It keeps looking like the hardware is *recognized*, just not *installed*.  I'll post my OSS4 troubleshooting info here in case it's something easy that I've overlooked.  Let me know if I should re-post this information on the OpenSound forums instead.

```
john@aaron:~$ uname -a
Linux aaron 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64 GNU/Linux
john@aaron:~$ ossmix
Selected mixer 0/High Definition Audio 0x00000001
Known controls are:


john@aaron:~$ ossinfo -v3
Version info: OSS 4.1 (b rc2/200811041156) (0x00040090) GPL
Platform: Linux/x86_64 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 (aaron)

Number of audio devices:	0
Number of audio engines:	0
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 ATI HD Audio interrupts=4217 (4217)
    HD Audio controller ATI HD Audio
    Vendor ID    0x10024383
    Subvendor ID 0x10438249
     Codec  0: Unknown (0x00000001/0x00002f80)
 2: oss_usb0 USB audio core services


Mixer devices
 0: High Definition Audio 0x0000000 (Mixer 0 of device object 1)
    Device file /dev/oss/oss_hdaudio0/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps: 
    Device handle: PCI82491043-0000:00:14.2-mx01
    Device priority: 10


Audio devices

```

Thanks for all the assistance.

---

### Post by ubernatural on 2008-11-04
Incidentally, I just checked and confirmed that my user is a member of the audio group (from other posts about people with no soundcards found).

---

### Post by ubernatural on 2008-11-05
I just decided to add this to launchpad as a bug since it's an issue with a fresh install as well as the live CD.

[https://bugs.launchpad.net/ubuntu/+bug/294189](https://bugs.launchpad.net/ubuntu/+bug/294189)

---

### Post by toddedw on 2008-11-05
Just for the record my SBx00 Azalia was working fine before I upgraded to 8.10. Fooey on me for upgrading.

---

### Post by marttali on 2008-11-06
Any updates? I have the same exact trouble- sb600 azalia with 8.10 64bit Kubuntu.
No sound with live cd, no sound with fresh install. I have dealt with it for weeks now :). chesk my other threads..
The only solution has been OSS4, nothing else has worked.
But now with OSS i don't have sound in flash anymore and this is a critical issue when your 2 year old demands youtube dump truck and fire truck videos believe me :)

---

### Post by Yellow Pasque on 2008-11-06
> But now with OSS i don't have sound in flash anymore
Download this: [http://ubuntuforums.org/attachment.php?attachmentid=69426&d=1210377383](http://ubuntuforums.org/attachment.php?attachmentid=69426&d=1210377383)
Gunzip and place in /usr/lib32

---

### Post by marttali on 2008-11-07
Thank you Mr Temüjin, that did the trick !

---

### Post by ubernatural on 2008-11-07
marttali - did you have any difficulties switching to OSS?  Does your card match "ATI Technologies Inc SBx00 Azalia (Intel HDA)" exactly (from lspci -v)?  I know what you mean about the dump trucks and fire trucks.  Diggers and cranes at my house...just not the same w/o sound :(

toddedw - are you still on ALSA or did you try OSS?

osstest says:
```
Sound subsystem and version: OSS 4.1 (b rc2/200811041156) (0x00040090)
Platform: Linux/x86_64 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008


NOTICE! You don't have any audio devices available.
        It looks like your audio hardware was not recognized
        by OSS. Please contact 4Front technologies for help
        (http://www.opensound.com/support.cgi). Don't forget to
        include your soundon.log file to the support request.
```

I did send my soundon.log file to 4Front, so I'll post back if I either get things resolved that way or via the launchpad report.

---

### Post by marttali on 2008-11-07
no difficulties, the device is:
 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
just downloaded the 4.0.. deb from the opensound site and installed it.
maybe run sudo dpkg-reconfigure linux-sound-base after installation to make sure it uses OSS. I noticed you are trying out beta ? Maybe that's the reason it doesn't work.
oh and run aplay-l after installation, this should tell you if it's successful (no soundcard yadda-yadda=something's wrong).
if there's no sound after installation also run ossxmix from bash to see if sound really is enabled.

---

### Post by ubernatural on 2008-11-11
On a tip from an email response from 4Front, I updated my BIOS and now have sound.  Now everything works - OSS, ALSA, etc - just as it always had on all my other computers.  Don't know what the problem was before, but obviously some BIOS changes were made for my motherboard between 07/2007 and 08/2008.

Thanks to all for the assistance (and yay to 4Front for immediately seeing that the BIOS wasn't reporting the audio device properly and pointing me in the right direction!)

---

### Post by danzvash on 2008-11-19
I recommend AGAINST using 4Front/OSS - stick with the community and use ALSA. It's more open, and in the long run you'll have less issues.

I also recommend against dropping random libs in various points on your filesystem, or installing direct from source without building .deb (or at least using something like "stow") - stick with apt-get or other front-end - package management is the way ;-)

I found my card
```
 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]

```

didn't work until I added the line:
```
options snd-hda-intel index=0 model=toshiba position_fix=1
```
to /etc/modprobe.d/alsa-base and restarted alsa.

Your problem may be something similar. Have a look at all your levels in alsamixer or other mixer app for any muted/disabled channels ....

---

### Post by ubernatural on 2008-11-22
Thanks for the advice.  I actually had been working with a fresh install anyhow, so after updating the BIOS I just redid the install completely.  The BIOS update fixed even ALSA, so I had no need to switch back to OSS and am using ALSA now.  I do appreciate the help from 4Front though that directed me to the BIOS update...

---

