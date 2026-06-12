---
title: "Trouble in amarok"
date: 2006-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rick069 on 2006-06-03
I have my amarok setup to automatically play any .mp3 file. The strange thing that is happening is that when I double-click on a .mp3 file, amarok loads, but something will flash very quickly and then amarok will say, "playlist finished" in a blue caption and the file never plays. What can be done to make the file play normally?

---

### Post by Princey on 2006-06-03
Did you have the multimedia codecs installed?

---

### Post by FluffyElmo on 2006-06-03
I don't use amarok myself but as a general tip when a program dies quickly try running it from a terminal window. Any errors will then usually print to the terminal. 

If it's like Rhythmbox you can probably include the path to the file (ie: *rhythmbox ./mp3/test.mp3*) and it will try to play it.

---

### Post by Rick069 on 2006-06-03
[QUOTE=Princey]Did you have the multimedia codecs installed?[/QUOTE]

This is what I got when going through the terminal as root:


rick069@rick069-desktop:~$ su
Password:
root@rick069-desktop:/home/rick069# which amarok
/usr/bin/amarok
root@rick069-desktop:/home/rick069# cd /usr/bin
root@rick069-desktop:/usr/bin# ./amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


This stuff reads like greek to me. Anyway, if somebody can make heads or tails of this, than let me in on it.

---

### Post by Rick069 on 2006-06-03
[QUOTE=Princey]Did you have the multimedia codecs installed?[/QUOTE]

Every one of them.

---

### Post by FluffyElmo on 2006-06-03
Could be having problems with a device. Do you have anything attatched to your system? USB Dongles, MP3 players etc?

Can you play sound from other apps? What sound card are you using?

---

### Post by FluffyElmo on 2006-06-03
These guys seem to be having a similar issue but it's in German so I can't be sure:)
[http://forum.ubuntuusers.de/topic/29999/]("http://forum.ubuntuusers.de/topic/29999/")

From what I gather if you edit *kde/share/config/amarokrc*, there is a line called *Output Engine* where you can change the value to *alsa*, *oss* or *esd*. I'd try them in turn to see if that is the problem.

---

### Post by cwf on 2006-06-04
Try this and see if it works:

[https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970]("https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970")

Be happy,
Siva

---

### Post by DoddyUK on 2006-06-04
It's a problem with the Kubuntu Dapper repos. Amarok requires libxine-extracodecs in order to play MP3s using the Xine engine. However, that library is currently not in the Repos, so the Xine engine cannot play back the file. However, it should also be noted that it is strange that Xine tries to play the file anyway without throwing up an error message.

[https://launchpad.net/distros/ubuntu/+source/xine-lib/+bug/37248](https://launchpad.net/distros/ubuntu/+source/xine-lib/+bug/37248)

The libxine-extracodecs .deb can be found here:
[http://packages.ubuntu.com/dapper/libs/libxine-extracodecs](http://packages.ubuntu.com/dapper/libs/libxine-extracodecs)

Works fine for me after installing the .deb.

---

### Post by _teo_ on 2006-06-11
[QUOTE=DoddyUK]The libxine-extracodecs .deb can be found here:
[http://packages.ubuntu.com/dapper/libs/libxine-extracodecs](http://packages.ubuntu.com/dapper/libs/libxine-extracodecs)

Works fine for me after installing the .deb.[/QUOTE]

Great! Thanks. That worked for me too. I wonder why the package isn't in the repositories... :confused:

---

### Post by a-v0id on 2006-06-15
Cheers DoddyUK, solved my problems and took away my misery :D

---

### Post by sirlancelot on 2006-06-19
w00t!! Fixed my problem too!

You're great, DoddyUK! =D>

---

### Post by tymek666 on 2006-07-25
I wonder why this package is not present in Kubuntu repos?!!!!
Without it amarok is useless.

---

### Post by easyease on 2006-07-25
because its not technically legal in the states.....lol.

---

### Post by tymek666 on 2006-07-26
who cares since kubuntu isn't us-based distro?

---

### Post by Crackez on 2006-10-10
It turns out that this package is in the multiverse repository. Enable it by adding "multiverse" to the end of the following two lines in /etc/apt/sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe *multiverse*
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe *multiverse*

After that, I was able to run "apt-get update && apt-get install  libxine-extracodecs" without issue. 

:-D

---

### Post by BatteryCell on 2006-10-10
> **Rick069 said:**
> This is what I got when going through the terminal as root:


rick069@rick069-desktop:~$ su
Password:
root@rick069-desktop:/home/rick069# which amarok
/usr/bin/amarok
root@rick069-desktop:/home/rick069# cd /usr/bin
root@rick069-desktop:/usr/bin# ./amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


This stuff reads like greek to me. Anyway, if somebody can make heads or tails of this, than let me in on it.
I dont think you need to worry about those X errors.  Ever since dapper came out the default xorg.conf has a bunch of stuff in  it about stylus and eraser and such (for tablet pcs and such)...and these are throwing u the errors.  To fix it edit your xorg.conf so that any references to devices that u dont have (stylus, eraser, most use the driver wacom,etc...) are commented out and then restart x.

---

### Post by cyberia81 on 2006-12-19
I can listen to my music now! Thanks so much!! :KS

---

