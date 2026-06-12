---
title: "[SOLVED] Amazon MP3 Downloader"
date: 2008-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2008-02-09
I Just installed the Amazon MP3 Downloader.  It's an i386 format deb, but it works great in 64-Ubuntu.  Since I have a house full of kids (6) and 10 PC's running Ubuntu in the house, I'll be installing this little jewel on all of them.  I just wish my wife hadn't wasted so much money downloading DRM music files when we were using windows.  I can't find a way to convert them to usable mp3's for Ubuntu.

Anyway, I've downloaded several songs using the downloader and it works great on 64-bit.

---

### Post by srt4play on 2008-02-11
Where did you get the deb from?

---

### Post by Maybelline on 2008-03-01
I tried installing on amd64 using
```
sudo dpkg --install --force-architecture amazonmp3.deb
```
but there are unmet dependencies.  Besides manually installing each of those, is there a  better way to get this installed?

---

### Post by NullHead on 2008-03-01
> **crjackson said:**
> I Just installed the Amazon MP3 Downloader.  It's an i386 format deb, but it works great in 64-Ubuntu.  Since I have a house full of kids (6) and 10 PC's running Ubuntu in the house, I'll be installing this little jewel on all of them.  I just wish my wife hadn't wasted so much money downloading DRM music files when we were using windows.  I can't find a way to convert them to usable mp3's for Ubuntu.

Anyway, I've downloaded several songs using the downloader and it works great on 64-bit.

> I can't find a way to convert them to usable mp3's for Ubuntu.

Well there is a lovely little program called tunebite(for windows) and it works like a charm :D Not sure if it works in wine as I don't have an DRM files anymore :twisted: [http://tunebite.com/en/remove_drm/index.html](http://tunebite.com/en/remove_drm/index.html)

---

### Post by lam2988 on 2008-03-01
hi,i am a newby and have found the wonder's of ubuntu. still working out some of the small problem but have found that looking at past post i have been able to fix every problem i have come across. i was looking to see if amazon mp3 was safe to download because i get a message saying it would be an error to down load it did you get that message. i also have to find a way to get all my itunes files on here but thanks to all the wonderful person on this site i will find the answer its just a mater of time. thanks to all!!!!!!:)

---

### Post by crjackson on 2008-03-01
> **Maybelline said:**
> I tried installing on amd64 using
```
sudo dpkg --install --force-architecture amazonmp3.deb
```
but there are unmet dependencies.  Besides manually installing each of those, is there a  better way to get this installed?

Do a search on the forums for a script called GETLIBS by Capy.  Read the 1st post and it will show you how to run the script.  It will install all the dependencies in one fell swoop for you.  It's quick and easy.  Thanks Capy...

---

### Post by crjackson on 2008-03-01
> **lam2988 said:**
> hi,i am a newby and have found the wonder's of ubuntu. still working out some of the small problem but have found that looking at past post i have been able to fix every problem i have come across. i was looking to see if amazon mp3 was safe to download because i get a message saying it would be an error to down load it did you get that message. i also have to find a way to get all my itunes files on here but thanks to all the wonderful person on this site i will find the answer its just a mater of time. thanks to all!!!!!!:)

I emailed Amazon and they sent me the deb by email.  I didn't download it.

---

### Post by crjackson on 2008-03-01
> **NullHead said:**
> Well there is a lovely little program called tunebite(for windows) and it works like a charm :D Not sure if it works in wine as I don't have an DRM files anymore :twisted: [http://tunebite.com/en/remove_drm/index.html](http://tunebite.com/en/remove_drm/index.html)

I current have a house full of windows computers (four with linux) and I could convert some for you *if you like*.

I can dual boot windows, but I'm not looking to invest anymore money in Windows software.

---

### Post by BFris on 2008-04-27
GETLIBS worked quite nicely for me. It doesn't work so well before you install the deb file. But it works nicely if you run it *after* you install the deb file.
```
sudo dpkg --install --force-architecture amazonmp3.deb
```
then
```
sudo getlibs /usr/bin/amazonmp3
```

I had to run getlibs a couple of times before it said there were no more unmet dependencies. Sweet.:guitar:

---

