---
title: "Sound problems on Ubuntu 9.04 (Acer Aspire 6530)"
date: 2009-06-10
forum: x86 64-bit Users
---

### Post by Tauriel on 2009-06-10
Hi all,

I have a problem with sound on my new Acer Aspire 6530 laptop on which I installed Ubuntu 9.04 (64bit). The sound from the laptop speakers is very quiet, and even when I turn everything to the maximum, it's merely medium loud.

Also, the system seems to ignore when I plug my headphones in and continues to play sound through laptop speakers.

In my Sound Preferences, all the devices are set to "Autodetect" and the device for Default Mixer Tracks is "HDA ATI SB (Alsa mixer)".


I understand that problem with sound is quite common, but I haven't been able to find any simple guides on how to solve this for my case. I'm a total newbie when it comes to Linux and I'm a bit hesitant to follow guides which list a series of commands to type in the Terminal, because I'm worried I might mess something up. :)

If anyone could please help me out, I'd be most grateful. :)

---

### Post by Dezeo on 2009-06-10
I have the exact same problem, only I have a Acer Aspire 5930.

can some on PLEASE help us. I'm really desperate now..

---

### Post by VastOne on 2009-06-10
> **Tauriel said:**
> Hi all,

I have a problem with sound on my new Acer Aspire 6530 laptop on which I installed Ubuntu 9.04 (64bit). The sound from the laptop speakers is very quiet, and even when I turn everything to the maximum, it's merely medium loud.

Also, the system seems to ignore when I plug my headphones in and continues to play sound through laptop speakers.

In my Sound Preferences, all the devices are set to "Autodetect" and the device for Default Mixer Tracks is "HDA ATI SB (Alsa mixer)".


I understand that problem with sound is quite common, but I haven't been able to find any simple guides on how to solve this for my case. I'm a total newbie when it comes to Linux and I'm a bit hesitant to follow guides which list a series of commands to type in the Terminal, because I'm worried I might mess something up. :)

If anyone could please help me out, I'd be most grateful. :)

In terminal run

```
alsamixer
```

And make sure the master and the front are turned up. You must use your arrow keys to navigate to each one left and right and then up and down to adjust. If Master and front do not solve, try the other choices.

VastOne

---

### Post by Tauriel on 2009-06-10
I turned everything up, but the sound is still too quiet when I compare it with how it sounds on Windows XP (I have dual boot). Also, my laptop features a subwoofer for better sound, and this is completely missing in Ubuntu. On XP I have nice rich sound, whereas on Ubuntu it's quiet, bad quality "classic laptop speakers" sound.

Should I try and look for drivers for my sound card?

EDIT: And it still ignores it when I plug my headphones in. The headphones option wasn't even available in Alsamixer (well, it was, but I couldn't turn it up).

---

### Post by VastOne on 2009-06-10
> **Tauriel said:**
> I turned everything up, but the sound is still too quiet when I compare it with how it sounds on Windows XP (I have dual boot). Also, my laptop features a subwoofer for better sound, and this is completely missing in Ubuntu. On XP I have nice rich sound, whereas on Ubuntu it's quiet, bad quality "classic laptop speakers" sound.

Should I try and look for drivers for my sound card?

EDIT: And it still ignores it when I plug my headphones in. The headphones option wasn't even available in Alsamixer (well, it was, but I couldn't turn it up).

I would search the forums here for the type of sound card you have and see if there others with the same issue.  

Sorry I cannot be of more help....

---

### Post by Nittalope on 2009-07-14
Have bought a Aspire 6530 and had the same problem. Fixed it opening the volume control's preferences and then preferences again and enabling all the options.
Then you have to turn up PCM and Side switcher to the maximum (and then you use your master option to control the volume, obviously).
The sound is quite a lot better..
My problem is that I cannot find out how the use the mic... and so cannot use skype...

---

### Post by RayArdia on 2009-07-14
> **Nittalope said:**
> Have bought a Aspire 6530 and had the same problem. Fixed it opening the volume control's preferences and then preferences again and enabling all the options.
Then you have to turn up PCM and Side switcher to the maximum (and then you use your master option to control the volume, obviously).
The sound is quite a lot better..
My problem is that I cannot find out how the use the mic... and so cannot use skype...
Thanks Nittalope, I have an Acer Aspire 5735 which HAD the same problem! Now solved.

---

### Post by salsel on 2009-08-15
Hi,
I have the same problem (or almost the same :( ). I have an Acer Aspire 5935G with ubuntu 9.04. I followed the previous instruction but I have not any change  :confused: ...the sounds doesn't work at all...  ](*,)
can someone help me?

---

### Post by Nittalope on 2009-09-06
You should try to check which device are you using (open Sound Control)... and tell us something more.

By the way I'm still having problem with the mic... I cannot record anything with the built-in mic, in skype I'm using and external web-cam (logitech, usb connected) as mic while the built-in camera works great as web cam (but in the skype windows, where I should see myself portrayed by the cam, I only see a part of the picture, while the people I am speaking with see perfectly all the field portrayed...).
And also the headphones jack doesn't work.
Has anyone found a solution to this problems?

---

### Post by ken78724 on 2009-09-06
see jaunty sound solutions

---

### Post by Nittalope on 2009-09-09
I too read about the OSS solution and tried that way, but could solve nothing... maybe because I could not follow step by step. Now I am back to the alsa way and sound works great... with the mic problem I wrote above.
Try to go back to the alsa sound driver!

---

### Post by gmsbeak22 on 2009-09-10
What web browser did you download Ubuntu with?

---

### Post by Nittalope on 2009-09-11
Well... I don't understand the question, but I downloaded the 9.04 version with my old pc (with Ubuntu 8.10), and I use Firefox on it.

---

### Post by harlock59 on 2009-09-11
Hello,
on my aspire 5315, my speakers have always been very low, but the headphones jack plug works great. i use external speakers plugged on the headset plug if i want to get louder sound.
i think it was about the same on windows.
i have only an issue on flash video sound on firefox.

for dvd playing, it's ok. (excepted for the low volume with built in speakers)

for those who can't play dvds, you have to install some packages.

i'm french so i found the ubuntu-fr.org page to install the cssread libs and dvdread packages. there's a command line to execute the shell script to make those packages to work.
from the medibuntu repository.

this page seems clear also
[http://www.cyberciti.biz/faq/howto-ubuntu-linux-playback-dvd/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-playback-dvd/)
but you only need to install libdvdread
vlc is ok, not necessary since totem is already on jaunty
(i use vlc) but totem can play dvds if the libdvdread is installed
after the
sudo apt-get [or] aptitude install libdvdread4 [and] libdvdcss2 
type this command-line to execute the install script for libdvdread4 to install. 
sudo /usr/share/doc/libdvdread4/examples/install-css.sh

here for the link (french ubuntu doc page dvd):
[http://doc.ubuntu-fr.org/lire_un_dvd]("http://doc.ubuntu-fr.org/lire_un_dvd")

equivalent in english (not ubuntu official page)
[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux]("http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux")
(seems different from the french official ubuntu doc)
french ubuntu doc seems cleaner and no advertising

---

### Post by bender1234 on 2009-09-29
> **Tauriel said:**
> Hi all,

I have a problem with sound on my new Acer Aspire 6530 laptop on which I installed Ubuntu 9.04 (64bit). The sound from the laptop speakers is very quiet, and even when I turn everything to the maximum, it's merely medium loud.

Also, the system seems to ignore when I plug my headphones in and continues to play sound through laptop speakers.

In my Sound Preferences, all the devices are set to "Autodetect" and the device for Default Mixer Tracks is "HDA ATI SB (Alsa mixer)".


I understand that problem with sound is quite common, but I haven't been able to find any simple guides on how to solve this for my case. I'm a total newbie when it comes to Linux and I'm a bit hesitant to follow guides which list a series of commands to type in the Terminal, because I'm worried I might mess something up. :)

If anyone could please help me out, I'd be most grateful. :)

Hey hope you solved the issue, this is an old post I came a cross looking for issues with my 6930G.
Since I struggeled with this problem myself, I decided to post anyways.

The driver doesn't understand that you insert the headphone, you have to manually mute the Front "channel" in the volume mixer. Also the "channel" for your minijack lineout is the surround "channel". I think this is similar for all the "new" acer laptops. The driver that comes out of the box with ubuntu should work, but I also have some issues here with the minijack output. Generally the sound on my system is really crappy(also in win7) compared to other systems, this probably varies from system to system I assume. The soundcard is the part wich I'm least satisfied on this notebook, my 4 year old kn1(generic aopen thing) rules in comparison. The sound comming from the minijack is low and "boxy" here, but the sound from the internal speakers is fairly decent.

ATM acer don't support linux, wich I find really sad. I hope they will change this in the future, and that they will start making drivers for us :)

regards,
bender

---

### Post by salsel on 2009-10-17
> **Nittalope said:**
> You should try to check which device are you using (open Sound Control)... and tell us something more.

I'm using the HDA Intel (alsa mixer), I put on all the setting available...

---

### Post by grege on 2009-10-18
It is always advisable to install gnome-alsamixer from Synaptic as it gives you much more control than the standard gnome applet.

Common problems are PCM level set low (sometimes wave level as well), muted outputs, digital out set as the default.

No sound at all can often be fixed just by systematically playing with volume controls, unmuting devices and selecting and deselecting channels.

Once it is working go into the Gnome mixer and in preferences turn off restore volumes. Then go back in and reselect restore volumes so that you settings become the new default on startup.

Install Gnome-alsamixer now.

---

