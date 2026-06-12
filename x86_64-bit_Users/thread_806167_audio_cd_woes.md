---
title: "audio cd woes"
date: 2008-05-24
forum: x86 64-bit Users
---

### Post by ARlyLngUsrNameJustBecause on 2008-05-24
Im using a fresh install of the amd64 flavor of ubuntu 8.04. I have had no problems watching videos on youtube or playing mp3s or downloaded videos, or dvds, or listening to radio in rhythm box.

However now Im trying to play an audio cd. Ive tried several to make sure it wasnt just the cd i was trying that is causing my problem. but whenever i put an audio cd in my drive, rhythm box crashes on startup. the only message it gives when started in a console is "Segmentation fault". Audio Juicer will start up and it correctly displays the cd information - track titles, band, album etc but if i click play or extract it ammediatly crashes. the error msg in the console sometimes says says "Segmentation fault" or it says:

"(sound-juicer:12848): WARNING **: Could not lock drive: Extracting audio from CD
Segmentation fault"


Ive already searched the forums and googled but i havent found anything that has helped. i found a post that mentioned enabling and disabling cdrom polling using:

 sudo hal-disable-polling --device /dev/scd0 --enable-polling

however that did not help. Any ideas?

---

### Post by ARlyLngUsrNameJustBecause on 2008-05-24
I just tried playing a cd on my brothers computer which is a fresh install yesterday of 32bit Ubuntu 8.04. It works fine in both rhythmbox and audio juicer.

---

### Post by ARlyLngUsrNameJustBecause on 2008-05-25
Resolved. 

I must have had a process hanging that I couldnt find. I rebooted and it works fine now.

---

### Post by raven on 2008-06-07
I'm having issue with audio or data cd

I can play DVD's,
I can mount data DVD's

but I cannot play or mount audio or data cd's

error "mount: No medium found"

usually I will have an icon that shows the cd data or audio is ready
but not anymore

system:
Hardy amd64 fresh install, I just tried the cdrom just today so I don't know if it worked before or some of the latest update that screwed it

it worked on gutsy before I freshly installed hardy

---

