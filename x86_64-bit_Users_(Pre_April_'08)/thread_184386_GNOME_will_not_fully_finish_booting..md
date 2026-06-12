---
title: "GNOME will not fully finish booting."
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by iamdigitalman on 2006-05-29
hello everyone!! new to the forums, but not new to linux. before Ubuntu, I had a little i386 laptop that I ran Knoppix, xandros, and finally Ubuntu on before the original hard drive went. 

to replace it, I bought a Powermac G3 B&W and Powerbook G3 Wallstreet, for less than $100 for both. I love them both to death, but I am not new to the mac scene.

when I first got the tower, I ran Ubuntu 5.10 on it, until a friend gave me a copy of Mac OS 9. figured might as well run the Apple software on the Apple hardware. so, I used that for 6 months, got frustrated with it's limitations, and here we are.

on Friday, I backed up the hard drive, wiped it, and retured to Ubuntu (good thing I was able to find my burned set of CDs). I installed it, and it ran fine. 

this next part is different, but I think it is the reason for my troubles: the DSL went down on saturday, but my system kept running. 

then, I shut it doen for a bit, pulled all the cables, and cleaned out the area behind it. I then re-assembled it, and turned it back on a few hours later. note that I moved it from on the left underside of my desk, to the right underside, for the increaced legroom. not important. what is important is that some of my USB cables were plugged into different ports. I doubt that has anything to do with it, but you never know.

upon booting the machine, everything was fine until I logged in. upon doing so, the mouse pointer came up, the brown-ish backdrop (not wallpaper) also came up, and the default startup chime played. that's it. nothing else happened. no nautilis, not even that loading fraphic thing. I even let it set overnight.

I tried everything: ctrl-alt-backspace to force restart GNOME, rebooting the machine, reinstalling the system, with and without zeroing the hard drive.

here it is monday night, and it's still FUBAR. the DSL hasnt come back up yet (they said it was a major problem with a substation server, and it's a holiday weekend, so hopefully tommarow.), so I am using the good old dial-up line.

could the lack of network/internet have something to do with it? or is it another hardware problem? note that i also unplugged all my USB devices, including the mouse, and plugged in an old ADB mouse. that didnt work either. note the tower also doesnt have a modem.

I hope this is a simple problem, because I want to try the drapper RC. so lets hope it fixes it's self soon, or somebody here can help me. 

also note that this problem also happens on the 5.10 Live CD. that didnt used to happen, so it is deffinantly a hardware issue.

thanks for any help in advance.

me=](*,) 

-digital ;)

---

### Post by qamelian on 2006-05-29
I had this problem on early Dapper flights. Purely by accident I found that if I waited for all hard drive activity to cease before logging in, it worked fine. If I didn't wait, I got what appears to be the same situation that you're experiencing. The problem seems to be resolved now.

Don't know if this helps at all. Good luck!

---

### Post by iamdigitalman on 2006-05-29
I dont have an external hard drive light (it's on the inside, on the mobo), and I cant unhinge the door, because the tower is inclosed, so I will just guess it and wait 10 minutes to try logging in, or does anybody know how long after the login screen comes up that hard drive activity ceases?

here are the details... (pause while I wait for 10 minutes to go buy... )

damn, that didnt work either.

thanks for helping, unfortunantly it didnt work.

any thing else I can try short of chucking the system out the window?

thanks. -digital ;)

---

### Post by iamdigitalman on 2006-05-29
well, I must have a dead PRAM battery, and letting my computer to set for a few hours unplugged killed it.

I found [this.]("http://www.ubuntuforums.org/showthread.php?t=180826") there is an odd datebug. no wonder it effects the live cd.

i'll run the fix, and let you all know.

btw, [here]("https://wiki.ubuntu.com/UbuntuDateBug") is the link to the Ubuntu wiki date bug fix.

enjoy. -digital ;)

---

### Post by LittleBuddha on 2006-06-06
I have the same problem.

It causes the Live CD to crash, am going to try this trick of yours tomorrow. And I will hopefully be able to install it now.

Is it possible to put this new date definition into some of the start up files that it is set every time the computer restarts??

---

### Post by iamdigitalman on 2006-06-06
[QUOTE=LittleBuddha]I have the same problem.

It causes the Live CD to crash, am going to try this trick of yours tomorrow. And I will hopefully be able to install it now.

Is it possible to put this new date definition into some of the start up files that it is set every time the computer restarts??[/QUOTE]

I dont think it's possible. but if you do get the problem, you know you need a new PRAM battery, so that's a good indicator. then, just restrart GDM, choose failsafe terminal for the session, and edit the date.

hope this helps. -digital ;)

---

### Post by LittleBuddha on 2006-06-07
Well, I've tried doing what is described in the wiki and I can now install Xbuntu.

I tried with Gnome, but I could not restart it. When I ran the restart command, it said it stopped, but it could not restart. But when I did the ctrl-option-F7 thingy i could still see the desktop so .....  

But anyways, am now installing Xbuntu and looking forward to playing around. 

Since this is an old laptop I don't want to by a new PRAM battery, and I don't care that the clock doesn't work. So I will try running the commands in the wiki at startup.

But it does seem a bit implausible, even thoug I'm an noob, that some date defining commando can't be added to the /etc/init.d/ xfc or gdm 

I would really appreciate if someone that knows bash in and out could supply me with that magic. Then I will try it out and get back to you.

---

