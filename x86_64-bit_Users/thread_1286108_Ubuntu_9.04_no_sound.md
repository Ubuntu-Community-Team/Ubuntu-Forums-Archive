---
title: "Ubuntu 9.04 no sound"
date: 2009-10-08
forum: x86 64-bit Users
---

### Post by Grahn on 2009-10-08
Hello, have been trying to get my sound to work in Ubuntu 9.04, sofar no sucess, have reinstalled and followed this guide : [http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html) with no sucess. 

Getting clueless anybody have any idea about how to fix it? :(

---

### Post by Kegusa on 2009-10-08
What machine are you trying to get sound on? Just finished fixing my own soundproblems with 9.04 on a brand new netbook (HP mini 110c)

Most of the soundproblems around are related to ALSA not branding your hardware correctly, and in some cases because the ALSA version in the repositories isnt updated to a version that supports your brand.

---

### Post by Kegusa on 2009-10-08
Forgot to mention this excellent guide to troubleshoot sound issues, take a look and if all else fails you can update to the newest version of ALSA.

Comprehensive Sound Problem Solution Guide: [http://ubuntuforums.org/showthread.php?t=205449&highlight=Suddenly+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=Suddenly+sound)

Upgrading ALSA: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

### Post by Grahn on 2009-10-08
Sorry for being kind of brief, was reinstalling atm as id been messing around quite a bit haha. Anyway, alsamixer says

Card: NVidia CK804                                                                                     &#9474;
Chip: Realtek ALC658D 

So its finding my soundcard, but wont work, maybe upgrading alsa will do it... Be back in a while when ive managed to figure out how to upgrade haha. Been follow the "Comprehensive Sound Problem"- guide, nothing there indicates it shouldnt work...

---

### Post by Kegusa on 2009-10-08
Also a very good place to search for clues what is wrong is to take a look at launchpad ([https://bugs.launchpad.net/ubuntu/+source/linux](https://bugs.launchpad.net/ubuntu/+source/linux))

Just find out what modules you are using, make of the card and look from there, best of luck with your upgrades :D

---

### Post by Grahn on 2009-10-08
Still nothing after updated SALSA drivers... Looking around for other answers but really running out of ideas.

---

### Post by Kegusa on 2009-10-09
Perhaps a bit more info is needed, via the terminal post the outputs of "aplay -l" here. Then type in "lspci" and see what kind of soundcard you have.. something like this.

[PHP]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
[/PHP]

Then to get more info about this card type in "lspci -s 00:1b.0 -v" but with your bus info (the xx:xx.x part)
The last command also gives you the info about what module is used for your card.

---

### Post by Grahn on 2009-10-10
**aplay -l :**
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**lspci:**
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
[B]
lspci -s 00:04.0 -v[/B]
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
    Subsystem: ABIT Computer Corp. Device 1c0e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at cc00 [size=256]
    I/O ports at c800 [size=256]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0


Hope i got it right now :)

---

### Post by salloo on 2009-10-11
This worked for me [http://ubuntuforums.org/showthread.php?t=1281226](http://ubuntuforums.org/showthread.php?t=1281226).  Try it.

---

### Post by Grahn on 2009-10-11
Still nothing at all :( allthough for some reason i dont get the HDA intel options in Sound preferances ([http://ubuntuforums.org/attachment.php?attachmentid=130561&d=1254553368](http://ubuntuforums.org/attachment.php?attachmentid=130561&d=1254553368)) Evrything seems installed and configured rightly though.:(

---

### Post by Kegusa on 2009-10-11
Hmm.. since everything else hasnt worked out you migth try this, but it's a bit of a longshot. 

Taken from ALSA documentation

[PHP]1988 AC97 Quirk Option

1989 =================
1990 
1991 The ac97_quirk option is used to enable/override the workaround for
1992 specific devices on drivers for on-board AC'97 controllers like
1993 snd-intel8x0.  Some hardware have swapped output pins between Master
1994 and Headphone, or Surround (thanks to confusion of AC'97
1995 specifications from version to version :-)
1996 
1997 The driver provides the auto-detection of known problematic devices,
1998 but some might be unknown or wrongly detected.  In such a case, pass
1999 the proper value with this option.
2000 
2001 The following strings are accepted:
2002     - default   Don't override the default setting
2003     - none      Disable the quirk
2004     - hp_only   Bind Master and Headphone controls as a single contro
2005     - swap_hp   Swap headphone and master controls
2006     - swap_surround  Swap master and surround controls
2007     - ad_sharing  For AD1985, turn on OMS bit and use headphone
2008     - alc_jack  For ALC65x, turn on the jack sense mode
2009     - inv_eapd  Inverted EAPD implementation
2010     - mute_led  Bind EAPD bit for turning on/off mute LED
2011 
2012 For backward compatibility, the corresponding integer value -1, 0,
2013 ... are  accepted, too.
2014 
2015 For example, if "Master" volume control has no effect on your device
2016 but only "Headphone" does, pass ac97_quirk=hp_only module option.[/PHP]

Migth want to try out some of those incase they work out for you.
Also with the updated (newest) ALSA version you can also try out "alsaconf" from the CLI to see if can do anything differently..

---

