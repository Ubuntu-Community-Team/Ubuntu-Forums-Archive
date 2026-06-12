---
title: "64 bit question"
date: 2008-02-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by TouchuvGrey on 2008-02-03
I have a HP laptop currently running ubuntu 7.04 ( 32 bit ) i think
the machine will support the 64 bit version:

AuthenticAMD
AMD Turion(tm) 64 Mobile Technology ML-34 [Family 15 Model 36 Stepping 2] 	Linux
2.6.20-16-386

  A. Am i correct ?
  B. What do i need to do to change to 64 bit ?
  C. Why should i ?

---

### Post by kaivalagi on 2008-02-03
A. Am i correct ? [COLOR="Navy"]Yes, 64 bit linux runs on amd 64 and core 2 duo processors for example[/COLOR]

  B. What do i need to do to change to 64 bit ? [COLOR="Navy"]You're best backing up what you need and installing from scratch, I don't know of anyone who has upgraded, all the libraries would change...ANYONE know otherwise?[/COLOR]

  C. Why should i ? [COLOR="Navy"]Your call, IMHO if you just use the laptop for surfing, writing the odd letter etc then keep what you have. If however you need the extra grunt (arguable that there is any...) for compiling/rendering/computation etc or what to tinker with the linux 64 bit side of things then go right ahead. 

I run ubuntu gutsy 64 bit as I develop software and tinker :), even then I don't see much in it. It took me a while to get the OS setup how I wanted it and I did need to install 32 bit library support for the likes of adobe flash player.

I am happy with it though, and I think, the more of us who use it in the linux community, the better it will get!

Hope that helps

Mark

[/COLOR]

---

### Post by Yellow Pasque on 2008-02-03
A. Yes
B. Install the amd64 version. The transition would be easier with a separate home partition.
C. We have a sticky in this forum that answers this.

---

### Post by xpod on 2008-02-03
Having just built my own 64bit AMD desktop i found myself installing the 32bit Xubuntu cd i had lying handy on the day and waited about a week before i eventually downloaded & installed the 64bit edition on the other drive.
It was just after New Year hence i was still a bit pre-occupied with the kids and *their* toys.

Total overkill for me of course as i probably never used 32bits and *one* processor on any of those old/er machines we had/have let alone the 64bit here with it`s  two processors:???:
Either way i have both OS`s on their own drives and i cant say i`ve noticed toooo much of a difference.
Not that i`ve really done any heavy duty rendering or encoding etc but then i never do anyway.
As long as the TVout works i wont do that encoding lark and the rendering...........i dont think scaling down an image in the Gimp really counts:)

I dont even use 1 of the 2G of ram in this thing and to be perfectly honest and i`d be just as happy with any of our old single core 32bit beige machines we have around.
The wife wanted the glass & silver look to match the rest of her furniture though so i just bought the glass and filled a new silver box with some new bits,all 64 of them.:)

---

### Post by utUtu on 2008-02-03
> **TouchuvGrey said:**
> I have a HP laptop currently running ubuntu 7.04 ( 32 bit ) i think
the machine will support the 64 bit version:

AuthenticAMD
AMD Turion(tm) 64 Mobile Technology ML-34 [Family 15 Model 36 Stepping 2] 	Linux
2.6.20-16-386

  A. Am i correct ?
  B. What do i need to do to change to 64 bit ?
  C. Why should i ?

I have the ML-28, and since Feisty have 64bit.  I tell you I'm  not going back to 32bit.  64bit is significantly faster.

---

### Post by Bad_Byte on 2008-02-04
I'm building a new computer.

Last time I tried 64 bit was 4 years ago on an athlon 64 2800+ with Gentoo and it was a horrible experience. Back then video codes and flash where a mess and a bitch to setup, requring their own 32bit os base to run making it a 32bit system ontop of a 64bit system.

Has this changed, is 64bit ready for desktop use?.

---

### Post by Yellow Pasque on 2008-02-04
> **Bad_Byte said:**
> I'm building a new computer.

Last time I tried 64 bit was 4 years ago on an athlon 64 2800+ with Gentoo and it was a horrible experience. Back then video codes and flash where a mess and a bitch to setup, requring their own 32bit os base to run making it a 32bit system ontop of a 64bit system.

Has this changed, is 64bit ready for desktop use?.
Yes, there's been an invention called "nspluginwrapper" that lets you use 32-bit plugins in a 64-bit browser. 64-bit development has come a long way since Intel  and Microsoft hopped on board, though I think MS is also holding the 64-bit cause back by continuing with 32-bit releases of their OS's (even announcing that their next OS will have a 32-bit version). C'mon MS, bite the bullet already.

---

### Post by Bad_Byte on 2008-02-04
That would take care of my flash concern, video codecs still a bitch?

---

### Post by TouchuvGrey on 2008-02-04
My main interest besides having a new toy to play with
is running my SETI@Home [BOINC]("http://boinc.berkeley.edu/") Project. As it involves
a lot of number crunching i suspect the 64 bit application
will crunch faster. I will go to 64 within a week and report back.

---

### Post by crjackson on 2008-02-04
> **Temüjin said:**
> Yes, there's been an invention called "nspluginwrapper" that lets you use 32-bit plugins in a 64-bit browser. 64-bit development has come a long way since Intel  and Microsoft hopped on board, though I think MS is also holding the 64-bit cause back by continuing with 32-bit releases of their OS's (even announcing that their next OS will have a 32-bit version). C'mon MS, bite the bullet already.

Well, the problem isn't just with MS.  There are lots of 32-bit machines still in operation.  I have 8 64-bit machines in my house AND 2 32-bit machines.  I would hate to have to run an old OS just because Ubuntu or MS didn't have a 32-bit version.

---

### Post by Kilz on 2008-02-04
> **crjackson said:**
> Well, the problem isn't just with MS.  There are lots of 32-bit machines still in operation.  I have 8 64-bit machines in my house AND 2 32-bit machines.  I would hate to have to run an old OS just because Ubuntu or MS didn't have a 32-bit version.

I dont think anyone wants the 32bit version to be discontinued. But that the focus of development shift from 32bit to 64bit. Right now 32bit projects dominate development and things trickle to 64bit, I think it should be the other way around. Right now linux has the edge in 64bit, I have no idea why developers dont push that advantage to its fullest.

---

### Post by Thelasko on 2008-02-04
@ Bad_Byte There is no difference in video codec support with 64-bit.  I'm not a programmer but from what I understand if the source is available then it will run on 64-bit.  The only problem is with closed source software such as Flash and a few drivers (like for printers).  Workarounds have been developed for most of those too.

---

### Post by shane2peru on 2008-02-04
I just recently dual realized that I have a 64 bit system and installed Ubuntu Gutsy 64, and after only a mere two days of use I have noticed a difference.  When installing programs, it doesn't hog the computer with the actual install process whereas in the 32 bit, it did use the computer more (perhaps hog the computer is an overstatement, but I did notice a difference in that).  I have done some other work, and noticed it is a little faster overall.  I have yet to try some backup things like rsync, tar, or scanning with clamscan in the background, I think those may run faster too, but I have to try them. I would say this, backup your current installation, and install the 64 version, if you have the room, install it even on a separate partition and dual boot both, that is what I'm doing.  You can really see the difference then.  Keep your backup for your 32 bit in case you want to go back.  Hang around this forum, and read a lot of the posts you will find a lot of answers before you ever need to ask the question.  Good info here and help.  

Shane

---

### Post by phidia on 2008-02-05
> **Kilz said:**
> I dont think anyone wants the 32bit version to be discontinued. But that the focus of development shift from 32bit to 64bit. Right now 32bit projects dominate development and things trickle to 64bit, I think it should be the other way around. Right now linux has the edge in 64bit, I have no idea why developers dont push that advantage to its fullest.

I just installed Gutsy 64 bit to my new laptop. It is quite a bit faster than vista was and from what I can observe it is as good with battery life if not a little better.

As you have said before kilz, what's the point of having this technology (64 bit) and not taking advantage of it?

Still, overcoming the myths and negative impressions about 64 bit takes time.
To that end kilz has been a true leader here.

---

