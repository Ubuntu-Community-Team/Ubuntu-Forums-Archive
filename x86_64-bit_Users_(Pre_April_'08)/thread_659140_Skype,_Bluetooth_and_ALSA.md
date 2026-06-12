---
title: "Skype, Bluetooth and ALSA"
date: 2008-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by squaregoldfish on 2008-01-05
Hi there,

I've just got Skype installed, and got my Bluetooth headset working as well. Unfortunately, I can't get the two to work together. I can run Skype and select the bluetooth audio device, but when I try to make a call I get the following error:

```
Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_bluetooth.so
```

This particular file exists, but I presume that's the 64-bit version, which is why Skype doesn't like it. I don't have a /usr/lib32/alsa-lib directory, so I presume I just don't have 32-bit versions of the necessary libraries. Does anyone know where I can get them, if indeed that is the problem? (Incidentally, I do have lib32asound2 installed.)

Thanks,
Steve.

---

### Post by Cappy on 2008-01-05
Try installing getlibs from here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and running
```
sudo getlibs -p bluez-utils
```

---

### Post by squaregoldfish on 2008-01-06
Thanks for your reply, Cappy.

I've managed to get the 32bit alsa libraries installed successfully, but Skype is still giving me the same error message.

I've rebooted, run ldconfig, and reinstalled Skype (v2) according to your tutorial elsewhere on this forum, all without luck, unfortunately.

Do you have any other suggestions?

Steve.

---

### Post by BoardDWorld on 2008-01-09
Skype I found easiest to set up, take a look at my thread:
[http://ubuntuforums.org/showthread.php?t=660802](http://ubuntuforums.org/showthread.php?t=660802)

---

### Post by squaregoldfish on 2008-01-09
Hi BoardDWorld,

Thanks for your reply. I've got as far as you did with running btsco, and as far as the system's concerned, everything's fine (I can play music through the headset using mplayer quite happily).

The problem I have is that Skype keeps finding the 64bit sound library instead of the 32bit one, and then doesn't know what to do with it, so it gives up and reverts to using my sound card.

Steve.

---

### Post by squaregoldfish on 2008-02-05
OK, so after a lot of mucking about, I finally gave up and symbolically linked my 32bit libraries into the 64bit lib directory. It's an evil hack, but it works.

The next stage of the problem is this: When Skype attempts to talk to my Bluetooth headset, it gets stuck in an infinite loop, constantly disconnecting and reconnecting the headset. Skype dumps the following output to the command line:

```
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL bluetooth
```

I've archived the output of hcidump for the relevant time period, and put it up at this URL:

[http://www.squaregoldfish.co.uk/externals/hcidump.txt]("http://www.squaregoldfish.co.uk/externals/hcidump.txt") (80Kb)

I haven't managed to decipher any of it yet, so if someone could give me a hand I'd be pathetically grateful.

Steve.

---

### Post by tontaube on 2008-02-21
Hi!
I've exactly the same problem. I can playback sound in Rhytmbox but Skype gives me the same error loop when setting the device to bluetooth.

My configuration:
Laptop: Dell XPS M1710
Dell Bluetooth 355 adapter (based on Broadcom bcm2045)
Headset: Plantronics Voyager 520
Ubuntu 7.10

installed packages:
bluetooth-alsa
bluez-gnome
bluez-utils

my  .asoundrc looks like this

pcm.bluetooth {
	type bluetooth
	device 00:19:7F:5F:87:24
	profile "auto"
}

I hope someone can help. If you need further information please let me know. Thanks.
tontaube

---

### Post by Samir33 on 2008-02-26
To report; same problem here, Gutsy amd64, bluez stack used, (not btsco):
```
Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_bluetooth.so
```

Also, manual installing or preloading 32-bit **libasound_module_pcm_bluetooth.so** and **libbluetooth2** in /usr/lib32/ doesnt help either. Does anybody have an idea why 32-bit skype looks for this particular library in /usr/lib/ but not in /usr/lib32/ ???

I know **libasound_module_pcm_bluetooth.so** is userspace alsa "driver", but can one install and use 32-bit userspace bluetooth headset libraries, only for the skype???

---

### Post by oddiofile on 2008-04-18
Using Dell D630, Plantronics Voyager 520, Linux 2.6.24.
I've successfully created the sound device, but as soon as Skype tries to talk to it, I also get this:

ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL bluetooth
ALSA lib pcm_bluetooth.c:458: (bluetooth_hsp_hw_params) BT_SETCONFIGURATION failed : Input/output error(5)

Also, I can't find a module called snd-bt-sco.
I have a "sco" and "bluetooth" only.
Is this related to the problem?
How do I get snd-bt-sco?

---

### Post by psyke777 on 2008-05-08
Try this: [http://ubuntuforums.org/showthread.php?p=4910397](http://ubuntuforums.org/showthread.php?p=4910397)

---

### Post by descentspb on 2008-07-23
Hey, guys, that's how i managed to do that, i've been having an exactly the same problem.

Skype was complaining about /usr/lib32/alsa-lib/....[some *.so files]

I didn't know how to compile that stuff for 32-bit on a x86-64 machine, so i googled for that particular files. It gave me a couple of RPM's. I downloaded them, and extracted the files that i needed in /usr/lib32/alsa-lib. Using the latest Skype, and it worked like a charm.

---

