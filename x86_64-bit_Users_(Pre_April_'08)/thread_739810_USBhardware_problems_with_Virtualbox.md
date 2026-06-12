---
title: "USB/hardware problems with Virtualbox"
date: 2008-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by guitarguy on 2008-03-30
I'm not an uber-geek, but this is my 2nd time around at trying to avoid a dualboot situation.I had to reformat recently and upgraded to Ubuntu 7.10 AMD64.
I downloaded the non-free version of Virtualbox and have got XP running on it.
But I haven't been able to get the USB devices to work in Windows.
I have used gedit to modify     [COLOR="Blue"]/etc/init.d/mountdevsubfs.sh[/COLOR] 
and                                /[COLOR="Blue"]etc/udev/rules.d/40-permissions.rules[/COLOR]    as per [[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=653853&highlight=VBoxManage]("http://ubuntuforums.org/showthread.php?t=653853&highlight=VBoxManage")
[COLOR="Black"] But I still get a[/COLOR] [COLOR="Blue"]Current state: Unavailalble[/COLOR] [COLOR="Black"]when I run [/COLOR][/COLOR][COLOR="Blue"]VBoxmanage list usbhost.[/COLOR]
I'm trying to hook up a 200G External USB HD and an HP Deskjet F300 printer/scanner. They both work in Ubuntu.

I did download and install Ubuntu Studio which has a modified kernel 2.6.22-14-rt.
It is a realtime kernel adapted for music production.I don't know if that is effecting the situation. All the files to edit seem to be the same as in the forums.

Hopefully I'll be able to get the USB straightened out.... but the soundcard issues (MIDI)
have got me more worried. I do a lot of music scoring and would really like to use a MIDI keyboard in the Virtual Windows setting.I really don't want to have to dual boot anymore. Any help would be appreciated.

---

### Post by caver1 on 2008-03-30
Whan you have Xp running in VirtualBox go to DEVICES, Under it click on Shared Folders, then Machince folders. Navigate to your USB drive and choose it. Should work fine.
You did remember to install Guest Addititions?
caver1

---

