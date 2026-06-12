---
title: "usb sound hardy virtualbox"
date: 2008-05-27
forum: x86 64-bit Users
---

### Post by Mgiacchetti on 2008-05-27
I installed virtualbox on hardy 64, running xp sp2 mce as guest, tried to use logitech usb headset but the out sound is choppy.
 
In messenger the mic works perfect but the speaker sound for the headset does not work correctly.
 
anyone else have this issue?
 
please post what you did to get your usb headset working, as i think when i set this up with the tutorial (i followed more than one because one didnt work)  i got my settings muffed up.

---

### Post by Kablooie!! on 2008-05-29
Hi,

Has anyone solved this issue?  I've got the same problem with my Logitech USB headset.

I saw in another thread that someone said version 1.6.2 of VirtualBox is out, but when I go to the Sun download site I see 1.6.0, which is the version I'm running.

I also saw in another thread (that I can't find now) that someone said the USB audio works in a previous release (1.5.2?) of VirtualBox, so I was thinking of down-grading to that version.  However I can't find where I can download it.

Does anyone have any suggestions?
Thanks,
Grant

---

### Post by P4man on 2008-06-30
Looks you can get 1.5.2 here:
[http://www.virtualbox.org/download/1.5.2/](http://www.virtualbox.org/download/1.5.2/)

If you try this, I would be most interested in hearing the result. I have the same issue, but I fear the virtual machine file will not be compatible when I downgrade to 1.5.2, so I will have to reinstall my (virtual) windows.  So if you feel like testing, please let me know if this solved the USB audio issues. I do seem to recall it did work for me with an older version of virtualbox, so I think your chances are good.

---

### Post by marclang on 2008-07-11
I had the same problem with Virtualbox 1.6.2, choppy sound and the mic would record very badly. Used a regular soundcard though, no USB audio. Same effect, however, so maybe it's not a USB issue?

Anyway, downgraded back to 1.5.6 which worked flawlessly (why did I upgrade again?) :) Downloaded it from here: [http://www.virtualbox.org/download/1.5.6/]("http://www.virtualbox.org/download/1.5.6/")

As for the incompatibilities: Luckily I did select "Make Backups" when 1.6.2 asked me to update my Virtual-Machines-Config files. I simply copied those back and everything worked without a hitch. I guess one could manually delete the lines added by 1.6.2 and get the config files to work again with 1.5.x -- it's an XML file afterall, and only a few lines were added by the 1.6.2 install.

---

### Post by cholapoker on 2008-08-17
Not sure if my solution applies.

Regardless of version virtualbox-1.5.6 or the later virtualbox-ose-1.6.2, either
1. fresh install windows xp without setting any audio (not even null audio)
  install virtualbox-guest-additions
  shutdown and set audio.
  restart winxp. It configures correct audio drivers.
  (note: at least to my pc, apparently, the previous sigtel audio is wrong)
  Also, both ALSA and OSS works smoothly in my case.)

2. I tried an existing *.vdi where the audio is not working.
  (note: it was not even booting until I changed General-Advanced-IDE controller type = PIIX3)
  booted in safe mode. Uninstalled the existing guest-additions.
  in device-manager, removed any audio drives.
  shutdown; un-set audio.
  rebooted and cancelled any installing of earlier drivers (such as VGA)
  reinstalled guest-additions and shutdown.
  set audio driver and booted.
  unfortunately it still detected the earlier audio drivers and sound was choppy.
  in the device-manager, chose to update the audio driver.
  Selected to install from my own location or something.
  Found there was another driver choice and installed it.
  Audio works.

I guess it is all about the Virtualbox not detected the correct audio driver correctly.

Thus ended my month of trial and error. Hope it helps someone.

Note:
my system is Debian lenny/testing.

---

