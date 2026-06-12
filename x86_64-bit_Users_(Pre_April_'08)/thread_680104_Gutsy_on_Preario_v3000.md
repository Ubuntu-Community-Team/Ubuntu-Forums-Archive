---
title: "Gutsy on Preario v3000"
date: 2008-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by reve_etrange on 2008-01-27
I just convinced my housemate to switch to Linux.  I thought Ubuntu would be the best distro for a new user, so I installed 64 bit Gutsy on his laptop, a Compaq Presario v3000.
I got wlan working with ndiswrapper (though Network Manager wont configure properly, I have to run iwconfig, etc. by hand), and the video card working with Restricted Drivers manager.  The only thing that still doesn't work is sound...the odd thing is that the sound control panel, and various playback software (like VLC) detect and list the sound device (as CONEXANT High Def. Audio).

$lspci | grep Audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'd appreciate any advice or knowledge about this hardware.

Thanks in advance.

---

### Post by homerhomer on 2008-01-28
Check this site out 
it's a good list of other users with laptops
[http://www.linux-on-laptops.com/compaq.html](http://www.linux-on-laptops.com/compaq.html)

---

