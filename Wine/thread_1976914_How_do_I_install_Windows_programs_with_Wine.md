---
title: "How do I install Windows programs with Wine?"
date: 2012-05-09
forum: Wine
---

### Post by iMurshaq on 2012-05-09
Quite simple really, and I'm running Lucid.

---

### Post by Enigmapond on 2012-05-09
Not so simple if the program in incompatible. Install playonlinux and try to install though that. It makes the installation easier.

---

### Post by iMurshaq on 2012-05-09
I'm a bit of a noob, what is playonlinux and whats the command to get it?

---

### Post by CrusaderAD on 2012-05-09
[http://www.playonlinux.com/en/download.html]("http://www.playonlinux.com/en/download.html") Get the DEB file for Ubuntu.

---

### Post by Enigmapond on 2012-05-09
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

What exactly are you attempting to install?

```
sudo apt-get install playonlinux
```

---

### Post by CrusaderAD on 2012-05-09
> **Enigmapond said:**
> [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

What exactly are you attempting to install?

```
sudo apt-get install playonlinux
```

I'd get the file from the website. PlayonLinux always complains about having the latest version. The Ubuntu Software Center will install it for you.

---

### Post by iMurshaq on 2012-05-09
I want to install sketchup and steam

---

### Post by CrusaderAD on 2012-05-09
You're going to have a tough time with steam. I believe it's possible, but it's just not stable.

---

### Post by Enigmapond on 2012-05-09
I don't know about this sketchup but you can forget steam. It will not work.

---

### Post by iMurshaq on 2012-05-09
Crap, does anyone have an idea on when valve is planning on releasing the steam client

---

### Post by Enigmapond on 2012-05-09
No idea. Valve just announced the idea of doing Linux games so I wouldn't hold your breath...Steam, however, may never be available as per the current talks.

---

### Post by CrusaderAD on 2012-05-09
[http://www.desura.com/]("http://www.desura.com/")

---

### Post by iMurshaq on 2012-05-09
Yeah, I thought I read about them making an ubuntu client but I didn't remember them saying anything about a date.

---

### Post by oldos2er on 2012-05-09
Thread moved to Wine.

---

### Post by iMurshaq on 2012-05-09
Thanks all

---

### Post by kdane4 on 2012-05-09
It seems you like gaming. Why not dual boot? Myself, I keep a copy of windows because I like playing pc games.

---

### Post by iMurshaq on 2012-05-09
I already have a dedicated Win 7 laptop with decent processor and a really good graphics card, I just wanted to see what I could do with this old laptop that I had laying around.

---

### Post by userqq on 2012-05-09
I dont know about lucid but FYI steam running smooth on ubuntu  oneric 11.10 and precise 12.04. good luck!

tips for installing steam here:
[https://wiki.archlinux.org/index.php/Steam](https://wiki.archlinux.org/index.php/Steam)
[http://ubuntuforums.org/archive/index.php/t-839091.html](http://ubuntuforums.org/archive/index.php/t-839091.html)
also might need
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

And for your initial question:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by cogadh on 2012-05-11
Yeah, you've been given a bit of bad info here. PlayOnLinux is not necessary, but it can be helpful, especially for inexperienced users. [Steam works fine in Wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444") and has for years now. Now, the games available through Steam, that can be a little hit or miss. You should check the [AppDB]("http://appdb.winehq.org/index.php") entries for any game you want to attempt running before you get into it. As for a native Linux version of Steam, [according to current reports]("http://www.phoronix.com/scan.php?page=article&item=valve_linux_dampfnudeln&num=1"), it is coming and Valve is already running games like L4D on Ubuntu machines in-house, but you know how Valve is bout sticking to or even creating schedules. We could see it show up next week, or it could be another 3 years, we just don't know.

---

### Post by donkyhotay on 2012-05-12
> **cogadh said:**
> As for a native Linux version of Steam, [according to current reports]("http://www.phoronix.com/scan.php?page=article&item=valve_linux_dampfnudeln&num=1"), it is coming and Valve is already running games like L4D on Ubuntu machines in-house, but you know how Valve is bout sticking to or even creating schedules. We could see it show up next week, or it could be another 3 years, we just don't know.

If you do a search through these forums for "steam linux port" you'll see posts for similar articles from various sources going back years, many of them from phoronix which seems to love to post news about a linux steam client. Don't believe anything that says steam is coming out for linux (even from the valve website) until there is a working downloadable client on the steam website itself. Also, even if steam ever comes out for linux that does not mean all those games available on steam will magically work on linux. They would need to be ported as well. Personally I couldn't care less if steam was ported or not. I'd be just fine seeing all those games ported to linux and able to work without the steam client.

---

### Post by cogadh on 2012-05-13
> **donkyhotay said:**
> If you do a search through these forums for "steam linux port" you'll see posts for similar articles from various sources going back years, many of them from phoronix which seems to love to post news about a linux steam client. Don't believe anything that says steam is coming out for linux (even from the valve website) until there is a working downloadable client on the steam website itself. Also, even if steam ever comes out for linux that does not mean all those games available on steam will magically work on linux. They would need to be ported as well. Personally I couldn't care less if steam was ported or not. I'd be just fine seeing all those games ported to linux and able to work without the steam client.

Did you even read the article before dismissing it? Unlike previous reports that were based on rumors and anecdotal evidence at best (the infamous "Linux coding" found in the beta client), this is an actual interview with Gabe, including a tour of the Valve offices with photos of games running on Ubuntu. Gabe even goes so far as to say that the direction Windows is heading is not the best for gaming, making Linux a preferred platform. You are correct that Steam on Linux is a small step at best without the games, but if the largest digital distributor in the business is already taking steps to get there, the games won't be far behind.

---

### Post by iMurshaq on 2012-05-13
This thread went so much farther than I expected!

---

### Post by donkyhotay on 2012-05-15
> **cogadh said:**
> Did you even read the article before dismissing it? Unlike previous reports that were based on rumors and anecdotal evidence at best (the infamous "Linux coding" found in the beta client), this is an actual interview with Gabe, including a tour of the Valve offices with photos of games running on Ubuntu. Gabe even goes so far as to say that the direction Windows is heading is not the best for gaming, making Linux a preferred platform. You are correct that Steam on Linux is a small step at best without the games, but if the largest digital distributor in the business is already taking steps to get there, the games won't be far behind.

Yes I know he spoke with valve, I don't care. There have been too many rumors and false starts over the years, most of them from phoronix. As I've posted many times, I refuse to believe steam is coming out for linux until about 3 days after a working downloadable client is available on the steam website. If I see something on the valve/steam website stating "steam coming for linux on this date" even then I'd consider it a maybe. So far I I haven't seen anything there yet thought I admit I haven't paid close attention. Even if it is advertised on the valve/steam site the project could still easily end up in development @#$% and never actually be released.

---

