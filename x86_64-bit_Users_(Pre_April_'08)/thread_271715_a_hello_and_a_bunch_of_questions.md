---
title: "a hello and a bunch of questions"
date: 2006-10-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by weird_c00kie on 2006-10-05
hello there :)

i'm completely new to the linux scene, having had to suffer with windows for far too long, so i'm pretty full of question hehe

i've only been running linux since yesterday and I've already managed to make it crash once and corrupt 'X' so that my visual interface was gone and i had to reinstall :p

i'm running ubuntu 6.06 on a dual core 64bit AMD processor and it's already causing me problems.
i'll number the questions to make them easier to refer to :D :

(1) i tried downloading the w32codecs, but to no avail. i can't find a version for amd64 :( is there a way around it?

(2) is it possible to get my HP iPAQ h5550 (PDA) to run with ubuntu?

(3) is there a linux equivalent of iTunes? ideally, if i'm going to fully migrate to linux, i'd like to be able to keep all the additional information in my itunes library, such as ratings, times played etc.

(4) can i get my ipod to work with linux as well?

(5) how do i install that Xgl/Compiz stuff? i tried following the guide here [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) and that's how i ended up messing up the visual interface

(6) what's a good email client for linux? 


that's all that comes to mind right now. answers to any or all of those questions are VERY appreciated in advance :D

---

### Post by kuja on 2006-10-05
Hi there!

1) You can get the w32codecs from the [mplayer website]("http://www.mplayerhq.hu"). You need to extract the archive and copy the files to /usr/lib/win32; however, these codecs will not work with your average 64-bit player. Fortunately, this problem will soon cease to exist... though it will probably be not until edgy+1 until most Ubuntu users see it. The current svn(basically, bleeding edge alpha source code) of ffmpeg (used by players like mplayer and xine), have support for it. There's [a thread](http://www.ubuntuforums.org/showthread.php?t=270066) going on about this currently. Alternatively, you could use a 32-bit player, to do so, see the sticky in this sub-forum.

2) I have no idea

3) A linux equivalent of itunes? Not really, Apple hasn't released such a thing; although, there are some very good audio players available, such as Amarok.

4) I've never tried it, though I'm pretty sure it's doable.

5) I personally don't bother with it, it's a bit of a hassle to get it working, but I think there is a sobigitsenourmousliketotallywaytoolong thread going on about it in the General forum.

6) Depends on your taste. Three of the bigger ones are Kmail, Evolution, and Thunderbird (which I hear has issues in the 64-bit Ubuntu(Thunderbird does, that is)).

---

### Post by weird_c00kie on 2006-10-05
hey kuja, thanks for the reply :)

i don't see why i have to have a 64bit player, so i'll look into what you said about getting a 32bit one

the other problem i'm running into now is with installing Wine.
once again, having an amd dual core is a hassle, because they only have it available for intel processors. it says some stuff about compiling it yourself, but i'm way out of my depth already, so i don't know how to tackle that one :(

---

### Post by kuja on 2006-10-05
Don't even bother trying to compile wine, you'll just lose sleep over it without any gain in progress. I know this first hand.

I started working on [a small program](http://ubuntuforums.org/showthread.php?t=266290) a couple weeks ago that might be worthwhile for you. It can handle installing wine, and a 32-bit player(with the w32codecs) (MPlayer).

---

### Post by weird_c00kie on 2006-10-05
sweet, thanks :D

i'm currently in the process of going through this thread
[http://www.ubuntuforums.org/showthread.php?t=270066](http://www.ubuntuforums.org/showthread.php?t=270066)

i'm up to wget [http://www.mplayerhq.hu/MPlayer/rele...060611.tar.bz2](http://www.mplayerhq.hu/MPlayer/rele...060611.tar.bz2) and i haven't run into errors yet, so i'm pretty happy heheh
if it all goes to sh*ts like it usually does, i'll try out your program as well :)

thanks for all the help so far :D

---

### Post by weird_c00kie on 2006-10-05
just to clarify, the w32codecs are the codecs needed for running the various types of video files, right?

---

### Post by kuja on 2006-10-05
Most notoriously WMV, not sure which other ones fall into the boat though.

---

### Post by weird_c00kie on 2006-10-05
the going sure is pretty slow.

after 9 hours, all i've done today was to reinstall ubuntu, download 180+ nameless updates, install 4-5 programs, a couple of which i can't even find, and finally have my graphics card recognised.
sounds like a fair amount... but not given the 9 hours it took to do it :p

---

### Post by kuja on 2006-10-05
I'm betting the main of that was downloading your "180 nameless updates". I can sympathize with that though, updating does take FOREVER. I've done it on dialup before, that was fun. I'd account part of the 9 hours to inexperience. I can get myself up and going pretty quick anymore, in the event I feel like reinstalling for x_y_z reason or to test x_y_z feature &c. Once you know what you're looking for it goes a ways faster, IMO.

---

### Post by weird_c00kie on 2006-10-05
i think so too, but it doesn't stop me from exaggerating in the exasperated manner only permissible to newbies, does it? :)

---

### Post by StandardBlueCaboose on 2006-10-05
I had a nice, proper post written up, but XP crashed on me (that's what I get for using Windows.) So my new post will be a little less proper and a little less exciting than the last one, but... whatever.

(1) I had trouble too, but Kuja's program is turning out excellent.

(2) CNET says no. It only works on windows, not Linux or Macs.

(3) Amarok's the closest thing to iTunes that I've found, and it's... IMO a lot better.

(4) GTKpod is supposed to do that, I haven't used it. It'll probably be just as good (or better) than iTunes.

(5) Xgl/Compiz is pretty annoying for noobs (like us) to install. Once you get it working though, it's all worth it. 

(6) I dunno. I just use gmail.

Keep dual booting. It'll be a while before you can move away from windows, if you ever completely do so.

---

### Post by weird_c00kie on 2006-10-05
thanks for that standard :)

i'm definitely keeping my dual boot for a while to come. i'm not entirely confident i'll be able to shift all my windows operations to linux without losing anything, so windows gets to stay there as my backup :)

i'll look into amarok and gtkpod tomorrow if time and the condition of my over-linuxed brain allows heheh

---

### Post by StandardBlueCaboose on 2006-10-05
> **weird_c00kie said:**
> thanks for that standard :)

i'm definitely keeping my dual boot for a while to come. i'm not entirely confident i'll be able to shift all my windows operations to linux without losing anything, so windows gets to stay there as my backup :)

i'll look into amarok and gtkpod tomorrow if time and the condition of my over-linuxed brain allows heheh

"Over-linuxed"

^^ I find that much more amusing that I probably should. It's just funny because I know exactly how you feel. 

Btw, I was just thinking, you might want to apt-get install yakuake. Not that it's really an important program, but it allows you to open a terminal with F12. It's pretty useful in that you don't have to go looking for a terminal anytime you want to do something. You just press F12 and there it is. If I remember correctly, it installed fine with no trouble. I hope the same holds true for you.

---

### Post by Relain on 2006-10-05
just about the terminal thing, you can just hit: <ctrl>-<alt>-F[1..5] (thats the keys F1 to F5 and you can have a whole new non X-server login. That's a fullscreen huge font terminal. Not that usefull if you have to read docs at the same time but you can switch about a lot.

It's one of my bestest fave features

---

### Post by fabertawe on 2006-10-05
> **kuja said:**
> 6) Depends on your taste. Three of the bigger ones are Kmail, Evolution, and Thunderbird (which I hear has issues in the 64-bit Ubuntu(Thunderbird does, that is)).

Hmn... personally I've not had any issues with Thunderbird and transferred my profile from Windows when I came to Ubuntu.

Paul

---

### Post by JAPrufrock on 2006-10-07
> 6) Depends on your taste. Three of the bigger ones are Kmail, Evolution, and Thunderbird (which I hear has issues in the 64-bit Ubuntu(Thunderbird does, that is)).
What are the issues with Thunderbird?- I've been using it with Ubuntu64 for a month now and, so far, it seems to be working ok???

---

### Post by Kilz on 2006-10-07
> **JAPrufrock said:**
> What are the issues with Thunderbird?- I've been using it with Ubuntu64 for a month now and, so far, it seems to be working ok???

I think some people had issues with version 1.5.0.4 64bit. But I have been running it as my main email client without problems.

---

