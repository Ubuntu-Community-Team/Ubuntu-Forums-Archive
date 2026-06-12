---
title: "Strange networking problem"
date: 2006-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by xraycharlie on 2006-03-25
I'm hoping somebody has some insite.

I have an ASUS A8N-VM board with 4200 x2 and 2 gigs ram.

A while back I installed breezy amd64 on it and except for the sound everything was working.

I messed a few things up on it so I decided to do a fresh install this evening.

Nothing has been changed with the hardware but networking is no longer working.  It seems to recognize that eth0 is there but I can't connect to anything using a static address. Trying dhcp gives a failure also.

I'm using the same install cd that I did the first time.

Just to try I also tried installing the 32 bit version of breezy and also the latest dapper. I'm having network troubles with both.

I've read through the forums and see how people have had networking problems with this board but it just seems strange that it would work for one install but not another.

Any thoughts would be appreciated.

Regards

---

### Post by localzuk on 2006-03-25
It is strange that it doesn't work now. Just to be on the safe side, have you checked that it isn't the network cable and/or hub/switch?

---

### Post by _Groove_ on 2006-03-25
I've found that my networking is started but something prevents the adaptor from actually getting an address (even though the link has been brought up). I do an "invoke-rc.d networking restart" and it comes good.

Does this work for you?

---

### Post by localzuk on 2006-03-25
I have just had an issue with my network connection that seems to be linked to Windows hibernation. Do you use the system in a dual boot? If so, do you use hibernation in Windows? If so, try shutting windows down and using ubuntu...

---

### Post by _Groove_ on 2006-03-25
I do use Windows dual boot, but no hibernation. I think it's something else for me.

---

### Post by xraycharlie on 2006-03-25
Thanks for all the suggestions.

I finally just went and spend the 14 dollars on a nic. plugged it in and it got recognized and works no problems.

Now onto the sound issues.

I'm starting to think that maybe I should have gotten myself something other than an nforce4 board.  

Regards

---

### Post by localzuk on 2006-03-26
Oh, I just realised it was an nvidia nforce4 board. Did you try installing the binary drivers for it from the nvidia website?

---

### Post by xraycharlie on 2006-03-27
I did.

The graphics driver worked but the audio/network driver didn't do it for me.

Regards

---

### Post by dpicker on 2006-04-05
Did you fix the sound problem?

I have the same board as yours and i managed to fix it eventually.

---

### Post by xraycharlie on 2006-04-07
I would love to know how you fixed it.

Not so much the network as I have the other card in it now, but I'd love to get the sound going.

Regards

---

### Post by dpicker on 2006-04-09
Ok download alsa 1.0.10 source: [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.10.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.10.tar.bz2)

and the patch: [http://www.student.uib.no/~hmy079/Linux_on_asus_csm/alsa_asus_csm-steroe.patch.txt](http://www.student.uib.no/~hmy079/Linux_on_asus_csm/alsa_asus_csm-steroe.patch.txt)

Extract the source and put the folder in the same directory as the patch. Open terminal and do:

```
cd /path/to/patch/and/source/
patch -p0 < alsa_asus_csm-steroe.patch.txt
```

Make sure you have build-essential and kernel headers installed. cd to the alsa source folder and:

```
./configure --with-cards=hda-intel
make
sudo make install
sudo ./snddevices
sudo rm /etc/modprobe.d/alsa-base
```

Now make a text file in the /etc/modprobe.d/ folder:

```
sudo gedit /etc/modprode.d/sound
```

And paste this into it:

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel position_fix=1

Now finally do

```
sudo modprobe snd-hda-intel
```

It will say a new audio device has been detected in a pop up window but I think you need to reboot before it works. Make sure you turn up all the volume levels because they get reset to 0. Let me know how it goes.

Did you notice asus released a beta bios 0902 that seems to fix the acpi problems?

---

