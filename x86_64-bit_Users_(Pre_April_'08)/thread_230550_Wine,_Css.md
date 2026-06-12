---
title: "Wine, Css"
date: 2006-08-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Stickittotheman on 2006-08-06
I am having one hell of a time installing WINE for my PC.

Gigabyte sumthin mobo
AMD 3500+
512 Corsair Valueselect RAM
80 Gig HD

I have found every single guide, how-to, wiki, etc. and I still seem to be unable to exec SteamInstall.exe to install Steam (derr). Could someone please give me a straight-forward set of instructions? I think I ****** up my system pretty bad, and I plan to reformat (I added bits of code everywhere that I don't know what they do :( )

Could someone please help? This whole 64bit thing really has me stumped. All I want to do is play some CSS with my clan...

Edit: Also I am leaving for a few days, when I get back I would really love to see a couple people explain this to me. And please don't just link me to how-to's or guides, they aren't helping me.

I'm a super linux noob, just installed tonight :P

---

### Post by Kilz on 2006-08-06
> **Stickittotheman said:**
> I am having one hell of a time installing WINE for my PC.

Gigabyte sumthin mobo
AMD 3500+
512 Corsair Valueselect RAM
80 Gig HD

I have found every single guide, how-to, wiki, etc. and I still seem to be unable to exec SteamInstall.exe to install Steam (derr). Could someone please give me a straight-forward set of instructions? I think I ****** up my system pretty bad, and I plan to reformat (I added bits of code everywhere that I don't know what they do :( )

Could someone please help? This whole 64bit thing really has me stumped. All I want to do is play some CSS with my clan...

Edit: Also I am leaving for a few days, when I get back I would really love to see a couple people explain this to me. And please don't just link me to how-to's or guides, they aren't helping me.

I'm a super linux noob, just installed tonight :P

You may want to [look at this page]("http://appdb.winehq.org/appview.php?iVersionId=1554") for the step by step instructions it gives

---

### Post by Stickittotheman on 2006-08-08
I worded that badly. What I'm having trouble with is compiling WINE from the source, like it tells you to on winehq. I'm running the command it gives you, but the terminal gives me this:
```
deb-src http://wine.budgetdedicated.com/apt dapper main
bash: deb-src: command not found
```

---

### Post by christhemonkey on 2006-08-08
You need to insert that line into your sources.list! 
Not into the terminal,
```
gksudo gedit /etc/apt/sources.list 
```
And add that line to the bottom.

---

### Post by Stickittotheman on 2006-08-08
OHHH I was misreading some of the lines in that wiki, I got it now... too bad I used a script before that I have no idea what it did, and now when i try to install it I get an error that mentions a conflicting previous installation...

Meh. Reformat tonight. Not worth the effort of trying to fix.

---

