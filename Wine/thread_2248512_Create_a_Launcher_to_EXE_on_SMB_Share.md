---
title: "Create a Launcher to EXE on SMB Share"
date: 2014-10-15
forum: Wine
---

### Post by highpass on 2014-10-15
Is it possible to create a launcher item that will open an EXE on a Windows server share? I have tried opening the EXE in Wine (which works fine) then locking to launcher, but upon rebooting and reconnecting to the server, the launcher item fails. 

---
Additional info:
This need is due to our office using an estimating program that must reside and launch from the server. Currently the office is Windows based, and we simply open a shortcut on the desktop to access the estimating program. I'm attempting to coerce my workmates into moving the office to Ubuntu, and must duplicate this simplicity (there are one or two valid reasons for wanting to switch, but to be honest it's mostly because I can't stand using Windows all day).

On further googling it seems a launcher with the command "wine /share/folder/executable" may be the way forward, which I'll have a stab at tomorrow.

---

### Post by Mark Phelps on 2014-10-15
> but to be honest it's mostly because I can't stand using Windows all day

WOW -- so EVERYONE ELSE is being "coerced" (your word) into leaving Windows simply because YOU don't like it??

Believe me, no one likes Change, and one that is imposed on others, is almost certainly going to be viewed negatively by those affected.

I've gone through such "migrations" myself, and an approach that is likely to be much more successful, and meet with more positive views from your customers, is to do a test migration yourself, and then SHOW them how much better off they are using a Linux approach, than keeping their existing Windows approach.

Once they see how much better their office lives will be, you'll become a "hero" in their eyes.

---

### Post by highpass on 2014-10-15
Obviously "coerce" couldn't have been a more incorrect choice of word if I tried. I was attempting to have a laugh, and should have remembered that I'm not funny. Yes of course the point is to show them how much nicer life can be; I'm not going to force anything upon anyone. At the end of the day - if they don't like it - no big deal; I'll still be able to use it on my workstation assuming I can figure this out.    

Note that these aren't customers, they're old friends. Old friends that spend all day griping about Windows and Office. So it won't take much to make them see the light.   Now that all the Dawson's Creek back and forth is out of the way, do forgive me, and let me know if you can help out. Cheers!

Update: Added samba mounts to fstab and was able to create a .desktop launcher for the application. Unfortunately the application cannot then load the support/database files it uses. These are located in the same directory as the EXE. Back to the drawing board!

Update: Success! Here is what I did to make it work. Mind this is probably not the best way of going about it.

1) Add server mounts to /etc/fstab
2) Create bash script as follows:
     ```
cd /mnt/share
wine "program name.exe"
```
3) Create .desktop file that runs the script:
     ```
[Desktop Entry]
Type=Application
Terminal=false
Name=whatever
Exec=sh bashscript.sh
```

Simple really!

I had dabbled with setting the .desktop Exec=cd /mnt/share && wine "program name.exe", which didn't work.

---

