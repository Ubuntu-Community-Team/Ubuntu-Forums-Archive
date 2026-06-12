---
title: "What video player is best for Ubuntu PPC?"
date: 2005-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Axios on 2005-11-15
Hi

Which video player should I use for ubuntu ppc?

I mostly want to be able to play things embedded in mozilla.
Totem is really bad at anything! It played some theora from ubuntu below zero, but the sound was bad and everything, and it took up _all_ my cpu power. (iBook 1,2 Ghz G4)

On my desktop (x86) i use mplayer, and mplayer plugin, again, totem sucks, it works pretty neet. But how does it work on ppc?

What about VLC?

What is the best on ppc?

---

### Post by tiagobt on 2005-11-16
VLC + Mozilla plugin works fine, but I personally prefer MPlayer + Mozilla plugin, it seems to support more video codecs.

---

### Post by Axios on 2005-11-16
[QUOTE=tiagobt]VLC + Mozilla plugin works fine, but I personally prefer MPlayer + Mozilla plugin, it seems to support more video codecs.[/QUOTE]

Can I just apt-get install mplayer ?

---

### Post by DJ_Max on 2005-11-16
Totem is simply a frontend. I use Totem with Xine and it works fine. The default Totem-Gstremer I've never had success with.

---

### Post by Axios on 2005-11-17
mplayer works fine

I can view wmv from big-boys.com and mov from trailers.apple.com embedded in firefox.

sudo aptitude install mplayer-powerpc
sudo aptitude install mozilla-mplayer

and remove the libtotem* from /usr/local/share/mozilla-firefox/plugins/

Totally nice, it works better than anything I used on OS X.

Thanks guys!

---

### Post by Brian McConnell on 2005-11-17
[QUOTE=Axios]mplayer works fine

I can view wmv from big-boys.com and mov from trailers.apple.com embedded in firefox.

sudo aptitude install mplayer-powerpc
sudo aptitude install mozilla-mplayer

and remove the libtotem* from /usr/local/share/mozilla-firefox/plugins/

Totally nice, it works better than anything I used on OS X.

Thanks guys![/QUOTE]
Wow! I'll try when I get off work tonight... I've got both of those installed, no luck with trailers.apple.com.... so.... hopefully I can have the same experience as you.

---

### Post by Brian McConnell on 2005-11-18
[QUOTE=Axios]mplayer works fine

I can view wmv from big-boys.com and mov from trailers.apple.com embedded in firefox.

sudo aptitude install mplayer-powerpc
sudo aptitude install mozilla-mplayer

and remove the libtotem* from /usr/local/share/mozilla-firefox/plugins/

Totally nice, it works better than anything I used on OS X.

Thanks guys![/QUOTE]


Although I have all mplayer-powerpc, mozilla-mplayer and of course also mozilla firefox, I do not have a mozilla-firefox directory in my /usr/local/share . I don't know why. Where else could I look for the libtotem* to remove it so I can try your suggestion?
Any help would be appreciated.
Thanks.
Brian

---

### Post by Axios on 2005-11-19
[QUOTE=Brian McConnell]Although I have all mplayer-powerpc, mozilla-mplayer and of course also mozilla firefox, I do not have a mozilla-firefox directory in my /usr/local/share . I don't know why. Where else could I look for the libtotem* to remove it so I can try your suggestion?
Any help would be appreciated.
Thanks.
Brian[/QUOTE]

My bad!
I don't have a mozilla-firefox directory there either.

It is at:

/usr/lib/mozilla-firefox/plugins/

---

### Post by Brian McConnell on 2005-11-19
[QUOTE=Axios]My bad!
I don't have a mozilla-firefox directory there either.

It is at:

/usr/lib/mozilla-firefox/plugins/[/QUOTE]
okay, in that folder I have:
libtotem_mozilla.so
libtotem_mozilla.xpt

Do I remove both or just one?

---

### Post by Axios on 2005-11-20
[QUOTE=Brian McConnell]okay, in that folder I have:
libtotem_mozilla.so
libtotem_mozilla.xpt

Do I remove both or just one?[/QUOTE]

all of them

---

### Post by Axios on 2005-11-20
[http://doc.gwos.org/index.php/Replace_Totem_as_Mozilla_plugin](http://doc.gwos.org/index.php/Replace_Totem_as_Mozilla_plugin)

---

### Post by Brian McConnell on 2005-11-21
[QUOTE=Axios]mplayer works fine

I can view wmv from big-boys.com and mov from trailers.apple.com embedded in firefox.

sudo aptitude install mplayer-powerpc
sudo aptitude install mozilla-mplayer

and remove the libtotem* from /usr/local/share/mozilla-firefox/plugins/

Totally nice, it works better than anything I used on OS X.

Thanks guys![/QUOTE]


yessirree! Works great at trailers.apple.com now.
Thanks for the help.

---

### Post by Axios on 2005-11-22
No problem.

Im glad it worked for you!

---

### Post by majkmil on 2005-11-22
It works great at apple trailers also but on a site like NFL.COM it connect to the server and then starts t buffer and just stops. Tried on another site same thing. Any ideas.

---

### Post by Brian McConnell on 2005-11-23
[QUOTE=majkmil]It works great at apple trailers also but on a site like NFL.COM it connect to the server and then starts t buffer and just stops. Tried on another site same thing. Any ideas.[/QUOTE]

I just went to NFL.com and played the realmedia file that's on the left side of the main page. Do you know what type of media you're having problem streaming? It sounds like quicktime/.mov are okay for you since traielrs.apple.com worked for you. Perhaps install realplayer if you haven't already? More info, please.

---

### Post by tiagobt on 2005-11-23
[QUOTE=Brian McConnell]I just went to NFL.com and played the realmedia file that's on the left side of the main page. Do you know what type of media you're having problem streaming? It sounds like quicktime/.mov are okay for you since traielrs.apple.com worked for you. Perhaps install realplayer if you haven't already? More info, please.[/QUOTE]
Do you have RealPlayer/PPC working? I installed it, but it crashed for all streamings I tried to play.

---

### Post by Brian McConnell on 2005-11-23
[QUOTE=tiagobt]Do you have RealPlayer/PPC working? I installed it, but it crashed for all streamings I tried to play.[/QUOTE]
Actually, I lied, but  didn't mean to!! I was under my openSuSe install to test the nfl.com realmedia stream and it worked fine. Also, the realmedia file was on the right side of the NFL's homepage and not the left :D
My RealPlayer with Ubuntu Breezy is not functional. It hangs whenever I try to play a file. I am probably going to remove and install a newer one and see if it helps. I'll post back here with any relevant infos.

---

### Post by Axios on 2005-11-25
[QUOTE=Brian McConnell]I just went to NFL.com and played the realmedia file that's on the left side of the main page. Do you know what type of media you're having problem streaming? It sounds like quicktime/.mov are okay for you since traielrs.apple.com worked for you. Perhaps install realplayer if you haven't already? More info, please.[/QUOTE]

I could also play the video on the right side on NFL.com. In ubuntu with mplayer.

---

### Post by Axios on 2005-11-25
[QUOTE=Axios]I could also play the video on the right side on NFL.com. In ubuntu with mplayer.[/QUOTE]
Dohh, I just tested it on my AMD _not_ my iBook. Sorry for the confusion

---

### Post by Brian McConnell on 2005-11-25
[QUOTE=Brian McConnell]Actually, I lied, but  didn't mean to!! I was under my openSuSe install to test the nfl.com realmedia stream and it worked fine. [/QUOTE]
[QUOTE=Axios]Dohh, I just tested it on my AMD _not_ my iBook. Sorry for the confusion[/QUOTE]
We're both confused! :D
RealPlayer with Ubuntu Breezy is not functional for me. It hangs whenever I try to play a file. I thought maybe installing an updated version would fix me, but same hang ups.

---

### Post by Axios on 2005-12-06
Why didn't I find this earlier?

essential-ppc and all-ppc codecs on mplayerhq.hu site!

[http://www4.mplayerhq.hu/homepage/design7/codecs.html](http://www4.mplayerhq.hu/homepage/design7/codecs.html)

This I must try!

Thanks mplayer devs!!

---

### Post by peter_m on 2005-12-07
Hi everyone, just installed Mplayer and it runs nicely. But I never had to add any codecs, it just worked after the followings installation commands:

```
sudo aptitude install mplayer-powerpc
sudo aptitude install mplayer-fonts
sudo aptitude install mozilla-mplayer
sudo rm /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.*
```

I just played the X-men III teaser at [www.quicktime.com](www.quicktime.com) with no problems. Why the fuss about getting codecs?

Also when installing in this manner, does the system keep these additional components (MPlayer) updated when I update Ubuntu?

---

### Post by Axios on 2005-12-07
[QUOTE=peter_m]

I just played the X-men III teaser at [www.quicktime.com](www.quicktime.com) with no problems. Why the fuss about getting codecs?

Also when installing in this manner, does the system keep these additional components (MPlayer) updated when I update Ubuntu?[/QUOTE]

Yes, but it's probadly only security updates until dapper drake. I haven't actually tried anything that didnt work, except wmv 9.0 and mov high definition.

---

### Post by MonolithTMA on 2005-12-07
```
Couldn't find any package whose name or description matched "mplayer-powerpc"
No packages will be installed, upgraded, or removed.
```

That is what I get every time I try

```
sudo aptitude install mplayer-powerpc
```

and the same for these two as well

```
sudo aptitude install mplayer-fonts
sudo aptitude install mozilla-mplayer
```

I think I have all the extra repositories open.

Any ideas

ps. my darned shift key stopped working, gotta figure that one out too. ;)

---

### Post by Axios on 2005-12-08
axios@axios2:~$ sudo aptitude search mplayer
id  mozilla-mplayer                 - MPlayer-Plugin for Mozilla
v   mplayer                         -
id  mplayer-386                     - The Ultimate Movie Player For Linux
p   mplayer-586                     - The Ultimate Movie Player For Linux
p   mplayer-686                     - transitional dummy package which can be s
v   mplayer-altivec                 -
v   mplayer-amd64                   -
p   mplayer-custom                  - The Ultimate Movie Player For Linux
p   mplayer-doc                     - Documentation for mplayer
i   mplayer-fonts                   - Fonts for mplayer
v   mplayer-g4                      -
ciA mplayer-k6                      - The Ultimate Movie Player For Linux
p   mplayer-k7                      - transitional dummy package which can be s
p   mplayer-nogui                   - The Ultimate Movie Player For Linux
v   mplayer-powerpc                 -
v   mplayerplug-in                  -
p   xmms-xmmplayer                  - XMMS plugin that uses MPlayer to play vid
axios@axios2:~$

---

