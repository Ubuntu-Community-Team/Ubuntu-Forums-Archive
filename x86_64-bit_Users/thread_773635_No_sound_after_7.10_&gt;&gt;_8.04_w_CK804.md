---
title: "No sound after 7.10 &gt;&gt; 8.04 w/ CK804"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by mkngl84 on 2008-04-29
Hello,

The relevant lspci prints:

"00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
01:08.0 Multimedia audio controller: Creative Labs SB X-Fi" [COLOR="Red"](single tear ... *sigh*)[/COLOR]

I have been using the onboard CK804 audio and it has worked fine as long as linux has run on this motherboard. I believe the correct modules are inserted for it and dmesg does not mention it. See the attached dmesg log. The volume control works without errors, however there is silence no mater what. The speakers are connected correctly and work fine elsewhere. Alsamixer recognizes the device, also.

I tried:
"cat /some/file > /dev/dsp"
...and got:
"bash: /dev/dsp: Device or resource busy"

Vlc gives the following messages:
"
main debug: control type=1
main warning: computed PTS is out of range (7894346), clearing out
main warning: output PTS is out of range (7913047), clearing out
main debug: audio output is starving (290937), playing silence
main debug: control type=1
alsa debug: recovered from buffer underrun
main debug: control type=1
main warning: computed PTS is out of range (420470878), clearing out
main warning: output PTS is out of range (420476227), clearing out
main debug: audio output is starving (296219), playing silence
main debug: control type=1
alsa debug: recovered from buffer underrun
"

This one, for me, is a head scratcher. This is on 8.04 Hardy Heron LTS (stable). Any ideas, folks? What other tests can I do?

Thanks much,
m

PS: the previous kernel (2.6.22-14) worked fine with CK804 while the current (2.6.24-16) is adept at silence with the CK804.

---

### Post by mkngl84 on 2008-04-30
I found my 7.10 Gutsy Gibbon 64-bit Desktop disc and tested it out. Turns out the sound is dead there too.

Well, I've learned my lesson to keep the SPEAKERS on BATTERY backup as well or they will discharge into your sound card if there is a spike or outage.

Now I get to wait for decent X-Fi drivers before I can have sound again. Yeah!

---

