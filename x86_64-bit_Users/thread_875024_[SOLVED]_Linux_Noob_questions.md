---
title: "[SOLVED] Linux Noob questions"
date: 2008-07-30
forum: x86 64-bit Users
---

### Post by alt3rn1ty on 2008-07-30
Hello world... of linux, Ubuntu x64 variety, and all you extreme nerds (wearing it with pride as you should be)

Loving Ubuntu already, reminds me of the old Amiga in many ways (okay you can stop splurting out your coffee :) )

I have dual boot XP Service pack 3 and Ubuntu 8.04.1 x64, grub boot loader, on my laptop (Compaq Presario r3000, athlon 64 3400, 756mb ram, Nvidia Geforce4). Old machine but still very capable.

Seriously cut down XP now just to run the odd game, linux has surprised me in that there isnt anything it cant do with style, and so much more configureable, so much so it has already impressed my eldest daughter enough to want it on her Vista machine O_o, and all this only 2 days after deciding to give it a go. The desktop is next.

I have already gone though Stchman's site and recommendations for clean-up, installing unusual/propriety codecs etcetera which conform to x64

So... Questions,

1. Probably simple but I cant find a solution, while playing around installing themes/art/icons, I installed Edubuntu. Decided I preferred standard Ubuntu load screens and un-installed edubuntu. 
Now I have one part of that left which refuses to un-install, after grub loader, then Kernel alive, theres a graphical load screen with the Ubuntu logo and a progress bar, before logon... this logo/progress screen is still Edubuntu. All other parts are back to normal, even the similar after logoff shutdown progress screen is back to normal. Anyone know how to change the startup one back to Ubuntu?

2. Is there a Winamp equivalent in linux?

3. Avast anti-virus has been a reliable protection for us for a long time, now I know with good practise no nasties should be downloaded, but I believe with the emergence of Linux distros which are so user friendly popularity is going to increase and hence more problems from malicious software, and having a family who are not so tech savvy I would feel better with similar protection in place as Avast, so what is the current feeling as to the best Anti virus/malware for linux distros?

Thank you all in advance for taking time out to listen/help.

---

### Post by Thelasko on 2008-07-30
1. I don't know
2. [XMMS]("http://en.wikipedia.org/wiki/XMMS")
3. Avast! is a available for Linux but I'm not sure about 64-bit.  The best supported AV for Ubuntu is [Clamav.]("http://en.wikipedia.org/wiki/Clamav") 

Please install any software through the repositories, I suggest using "Add and Remove Programs" if you are new to Ubuntu.  I don't think Avast! is in the repositories, so I don't recommend using it.

---

### Post by Stunts on 2008-07-30
Hello and welcome to Ubuntu!

1 - Try to install startup manager. It's in the repros. ```
sudo apt-get install startupmanager 
```

2 - I've never tried XMMS, but Amarok seems very popular. Personally I just use Rhytmbox ou Banshee (they are somewhat different from winamp tough). They are also all in the repros.

3 - Clamav seems to be well supported for linux and is in the repros. When I migrated from windows I kept using Avira Antivir XP. Was quite good and has a linux version. Though it's closed source, not in the repros and I'm not sure it will work on 64bit.

Did I say "Welcome to Ubuntu?"

---

### Post by alt3rn1ty on 2008-07-30
=D>:grin:Thank you both, all problems resolved, startup manager did the trick, dont know how yet but im sure i will be delving deep into such things in the near future :)

---

### Post by alt3rn1ty on 2008-07-30
@ TheLasko : The link you gave to XMMS on wikipedia shows exactly the kind of interface I am looking for, but from there I cant find a link to that particular client for XMMS, I notice a reference that says this is the default player but how do you install that?

---

### Post by opr8ive on 2008-07-30
> **alt3rn1ty said:**
> @ TheLasko : The link you gave to XMMS on wikipedia shows exactly the kind of interface I am looking for, but from there I cant find a link to that particular client for XMMS, I notice a reference that says this is the default player but how do you install that?

Check out audacious.. Its in the repos, and looks like a win-amp-esque interface..

-Jason

---

### Post by jeremy1138 on 2008-07-30
according to wikipedia, there is a version of winamp for Linux...

[http://en.wikipedia.org/wiki/Winamp](http://en.wikipedia.org/wiki/Winamp)

check that - it appears wikipedia is wrong.  Sorry.

see this - [http://forums.winamp.com/showthread.php?threadid=249591](http://forums.winamp.com/showthread.php?threadid=249591)

---

### Post by steveneddy on 2008-07-30
> **opr8ive said:**
> Check out audacious.. Its in the repos, and looks like a win-amp-esque interface..

-Jason

XMMS isn't supported anymore and audacious will use the same skins and the same pugins as XMMS.

```
sudo aptitude install audacious
```

---

### Post by alt3rn1ty on 2008-07-30
Woa loads of help :), Audacious is the puppy I needed, the Refuge skin under preferences is the same as the XMMS on wikipedia, and audacious flicks all my happy switches. The themed skin is ideal because it fits nicely with a theme I am converting from windows visual style, based around Azenis2 (go deviantart and type it in the search, you will see what I mean).

Many thanks to all, no doubt there will be more OS quirks I will be bugging you all about but I hope to be more helpful than noobish soon, having loads of success here... and ooooh, check out the alladins cave of free stuff on add/remove, its awesome <everyone rolls eyes "We know dude">, audacious led me to find another windows fave aswell, audacity.

Now wheres that rar plugin and compiler.... :lolflag: Im going to need a new hard drive soon. Anyway best get some sleep I think.

---

### Post by opr8ive on 2008-07-31
Heh.. Right on.

Glad I could help (Im quite the noob myself)

Ive heard 7zip is quite useful for rar, but havn't used it myself yet (I think the package is called p7zip) might give it a check out..

Congrats, and like said above, welcome to Ubuntu!

-Jason

---

### Post by Sef on 2008-07-31
> Avast anti-virus has been a reliable protection for us for a long time, now I know with good practise no nasties should be downloaded, but I believe with the emergence of Linux distros which are so user friendly popularity is going to increase and hence **more problems from malicious software, and having a family who are not so tech savvy** I would feel better with similar protection in place as Avast, so what is the current feeling as to the best Anti virus/malware for linux distros?

The best solution would be to only give them user access, not administrative (root) access.

---

### Post by soxs on 2008-07-31
> **Sef said:**
> The best solution would be to only give them user access, not administrative (root) access.

In fact that was the problem Xp had: Everyone being admin, it's the simplest way to keep yourself in a "bottle" knowing the admin passwd for certain tasks getting superuser, but stay the bottled dwarf for web/gaming/3rd party apps.

---

### Post by Thelasko on 2008-07-31
Sorry about that, I used XMMS back in Feisty(Ubuntu 7.04), I didn't know it was replaced with audacious or Beep Media Player(BMP), depending on your preference.

---

### Post by opr8ive on 2008-07-31
I rather liked xmms.. 

All through my last few years of tinkering off and on with linux, xmms always seemed to just work, even if I had everything else fouled up.. LOL.

-Jason

---

### Post by alt3rn1ty on 2008-07-31
@ Thelasko... No problem, I have learned a lot of new things along they way and amazed how quick this OS is, I just discovered the cube thing, 9 x 9 workspace is just ridiculous lol, but amazing to watch in action, all on my previously humble presario. I do believe this OS is a lot tighter than windows in coding, I am positively itching to pounce on the family desktop but better make my baby steps on this machine first.
Thanks again all.

---

