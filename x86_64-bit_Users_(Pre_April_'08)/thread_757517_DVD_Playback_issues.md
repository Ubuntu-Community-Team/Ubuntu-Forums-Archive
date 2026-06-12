---
title: "DVD Playback issues"
date: 2008-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by cjb5089 on 2008-04-17
Ok, I've tried a few different ways to get dvd's to play, I am new to ubuntu with basic line command skills.  First off, in totem, i got video to work when the dvd is first inserted, but the main audio doesn't work, only the background noise, which is kinda wierd.  In VLC, both the video and the audio are scrambled and distorted for the first 2/3 of the movie, the last third works perfectly fine as far as i can tell, which is pretty random.  If anybody could help, i would appreciate it, i run ubuntu 7.10 with the amd64 bit desktop version..... could it be that its not working cus its 64bit?

---

### Post by Kilz on 2008-04-17
> **cjb5089 said:**
> Ok, I've tried a few different ways to get dvd's to play, I am new to ubuntu with basic line command skills.  First off, in totem, i got video to work when the dvd is first inserted, but the main audio doesn't work, only the background noise, which is kinda wierd.  In VLC, both the video and the audio are scrambled and distorted for the first 2/3 of the movie, the last third works perfectly fine as far as i can tell, which is pretty random.  If anybody could help, i would appreciate it, i run ubuntu 7.10 with the amd64 bit desktop version..... could it be that its not working cus its 64bit?

[Did you read and follow this page?]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by cjb5089 on 2008-04-17
ya, I've already done most of those things and I did the things i havent done yet, i installed xine media player and i get an error "xine engine error: there is no plugin avaible to handle 'dvd:/ ' maybe MRL syntax is wrong or file/stream source doesnt exist" and then it suggests that i either dont have enough rights to play it, or that there is no data on the disk, which i know there is. plus i still get the same results with vlc and mplayer

---

### Post by crjackson on 2008-04-17
Try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 64-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w64codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by cjb5089 on 2008-04-17
I got to step two and i encountered some problems, i failed to get the medibuntu pages "302 found" and then it gave me GPG error" W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263"  What and/or how do i obtain the pubkey???

---

### Post by Kilz on 2008-04-17
> **cjb5089 said:**
> ya, I've already done most of those things and I did the things i havent done yet, i installed xine media player and i get an error "xine engine error: there is no plugin avaible to handle 'dvd:/ ' maybe MRL syntax is wrong or file/stream source doesnt exist" and then it suggests that i either dont have enough rights to play it, or that there is no data on the disk, which i know there is. plus i still get the same results with vlc and mplayer

Not the player, did you install libdvdcss2? Without it Ubuntu cant play encrypted DVD's regardless of the player. When someone suggests to look at a page, you might just want to read the whole thing.

---

### Post by cjb5089 on 2008-04-17
Yup, I already have libdvdcss2 installed, when i first tried to play a movie, i got nothing, i tried a bunch of stuff including libdvdcss2, and now im with the described playback, i tried to regionset thing but i got an error:

$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.

---

### Post by crjackson on 2008-04-17
> **cjb5089 said:**
> Yup, I already have libdvdcss2 installed, when i first tried to play a movie, i got nothing, i tried a bunch of stuff including libdvdcss2, and now im with the described playback, i tried to regionset thing but i got an error:

$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.

Does it do this on all movies or just a particular movie?

---

### Post by cjb5089 on 2008-04-17
ive tried two and the same thing happens to both

---

