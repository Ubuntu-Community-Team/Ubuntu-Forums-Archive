---
title: "Dell Studio, Jaunty 9.04 x64, and Intel HDA"
date: 2009-05-13
forum: x86 64-bit Users
---

### Post by kreuelt on 2009-05-13
Last night, I installed Intrepid 8.10 x64 on my new Dell Studio, because Intrepid was the only disk I had lying around. At that point, the sound worked fine, and I got some basic applications installed. I then upgraded from 8.10 to 9.04 overnight, and when I woke up in the morning, the sound wasn't working. I've checked the sound help threads, and nothing seems to have helped. My sound card is an Intel HDA card, and the output of aplay -l is as follows:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Does anyone have any suggestions? Thanks in advance for all your help!

---

### Post by ken78724 on 2009-05-14
kreuelt, 
1) have you checked for the Sound tweaker? I've been able to increase sound on YouTube and Webinars using Jaunty 9.04. 
2) for self help do a System>Administration > Update Manager. Is probably okay to install all available but look in particular for an update dealing with sound. 

Then unrelated, if no solution with 1 or 2, I urge that you report error messages or issues so that an experienced guest may advise you. If you're in a hurry, try to report a problem source with something like this 
3) procure a problem source list with perhaps: 'gedit /etc/apt/sources.list' and Enter your password when prompted.
but, I do not see that you mentioned receiving a notice saying something like 'E: _cache->open() failed, please report.' 

Lastly, I hope you will share wisdom on the Dell Studio. I set out to install Ubuntu Studio 8.10 intrepix but ran into complex issues; finally achieved 8.10 install with java allowing me to attend webinars. out of curiosity I installed jaunty 9.4 and cannot get an old HP laser 4000 or Dell 922 AIO to print; plus, I lost java needed for webinar appreciation. 
Later ;)

---

### Post by ken78724 on 2009-05-14
when you are able,update your profile to Ubuntu jaunty 9.04

---

### Post by kreuelt on 2009-05-14
Thanks for the suggestions, unfortunately I can't get any of them to work. Could you possibly clarify what you mean by > 
Then unrelated, if no solution with 1 or 2, I urge that you report error messages or issues so that an experienced guest may advise you. If you're in a hurry, try to report a problem source with something like this
3) procure a problem source list with perhaps: 'gedit /etc/apt/sources.list' and Enter your password when prompted.
but, I do not see that you mentioned receiving a notice saying something like 'E: _cache->open() failed, please report.'

How would I go about doing this?

Also, I'm sorry to hear about your problems with the Dell Studio. For me, everything worked just fine, with both the 32 and 64 bit versions, in both 8.10 and 9.04, right off the bat (granted, I don't use Java that often) excepting, of course, the sound card.

---

### Post by jdunn on 2009-05-16
I'm having a similar problem.  i made a clean install of 9.04 x64 over 8.10 x64 on an HP Pavillion using the HDA Intel driver on an 82801I (ICH9 Family) HD Audio Controller.  Sound worked fine on 8.10 but I have no sound on 9.04.

Here is my aplay -l output:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Longshoreman on 2009-05-17
**No sound either**
Ouput from aplay -laplay: device_list:217: no soundcards found...
My installed sound card is 
**Audio device: Intel Corporation 82801H (ICH8 Family) HD ** 
 [B]Audio Controller (rev 03) 00:1c.0 PCI bridge: 
[/B]
**From checking the ALSA site it would seem that my souncard is not supported so there you go I am stuck!**
**It would seem that Ubuntu is not as easy to install as one would hope!**
**Not at all sure what to do next**
[B]David :(
[/B]

---

### Post by Yellow Pasque on 2009-05-17
Check the obvious. Make sure nothing muted itself:
```
alsamixer
```
The pavucontrol package might be helpful too.

---

### Post by MetapostAddict on 2009-06-04
I'm having the same problem on my new HP HDX16t with an Intel HDA driver.  I've checked "the obvious" and the not so obvious to no avail.

---

