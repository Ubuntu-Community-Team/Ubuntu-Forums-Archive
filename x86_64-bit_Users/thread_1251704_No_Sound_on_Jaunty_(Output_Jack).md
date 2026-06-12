---
title: "No Sound on Jaunty (Output Jack)"
date: 2009-08-28
forum: x86 64-bit Users
---

### Post by BTSykes on 2009-08-28
I just recently started using Ubuntu earlier this week and have so far been able to resolve all issues through reading archives of this forum. One problem that has persisted throughout all treatments is that of sound. All of the easy ([and even the less than easy]("http://ubuntuforums.org/showthread.php?t=205449")) processes have been exhausted. The speaker are plugged in, nothing is muted, the correct drivers are installed. From little I know of computer science, the issue seems to lie  somewhere between the sound card and the output jack. 


I am actually having this issue on two separate systems:


First- A custom desktop computer running on an ***Asus M3A76-CM*** Motherboard.

"lspci | grep Audio" yeilds:
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

"aplay -l" yields:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



Second- A ***Gateway T 1620***
which is also using ATI Drivers. (I dont have the system in front of me, ill get the details later). 

On the Gateway sound is functional on the built in speakers, but not when speakers are plugged into the output jack.

Please Help!

---

