---
title: "ABC.com Move Player + wine causes weird graphics mode"
date: 2008-06-09
forum: Wine
---

### Post by jsestri2 on 2008-06-09
I have attempted to watch ABC.com tv shows via instructions found on an archived forum page:

[http://ubuntuforums.org/showthread.php?t=679165](http://ubuntuforums.org/showthread.php?t=679165)

Every time I start up the abc.com player, the commercials and menus all play fine. When the show itself begins, the graphics mode flips into a weird coloring scheme that is not particularly useful (looks sort of like tie dye.) The video itself also appears extremely pixelated compared to what it should be. Once the mode has been entered, the only way to get out of it, that I have found, is to restart the x server with Ctrl+Alt+Backspace.

I have not seen other reports of this, except recently at the very end of the thread above, so I am wondering if this is a new bug. I have created a bug report: [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/237818](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/237818) it has not had any responses yet. I am wondering if anyone else sees this, or if anyone has a work around yet.

Thanks,
J.J.

---

### Post by TracyO on 2008-06-11
Hi there,

I can't help you with the problem, but I can say that you're not the only one.  I've been having this problem, too, since last week.  I used Wine for a couple weeks, and now, what you described happens every time.

Anyone?

Tracy

---

### Post by jsestri2 on 2008-06-11
Did you update the Move Player at all to your knowledge? -- I am trying to guess whether it was a change to Wine or the Move Player (abc.com's player plugin for firefox)

---

### Post by TracyO on 2008-06-11
Not to my knowledge.  I don't know if this is normal, but every time I use it, I have to reinstall the plug-ins for Mozilla (like it's the first time).  Maybe the plug-in changed?

---

### Post by yankes1903 on 2008-06-11
It happens with fox's web-site too which also uses the Move player. other networks are fine that don't use it.  I just downloaded everything (I'm new to ubuntu, only installed it for the first time last week!) so I definitely have the most up-to-date versions of move player and flash.  I've tried firefox 2.0.0.14 and 3 beta with the same result.
(This is actually further that I ever got it to work in Vista, after the commercials it would just stop and there was no sound.)

---

### Post by Meph1st0 on 2008-06-17
This is happening to me too.  Unfortunately, I don't have any discoveries to help solve the problem either.

---

### Post by newsy on 2008-07-17
having the same problem here. I have a screen resolution of 1400x900 perhaps it's a problem with the screen resolution.

Could it be that color depth is changed from 24 bit to 4 bit (or anything like that)?

I hear of people that got it working with wine, could they upload their move media plugin? Perhaps only the recent version of that plugin shows these errors.

EDIT: BTW I have a NVIDIA graphic device, so it's nothing only ATI specific.
Perhaps it's an option that is activated in xorg.conf and causes the problem.

---

### Post by Watchtow3r on 2008-07-18
same problem with graphics. Also I'm not sure if anyone mentioned it, but abc used to support Linux, and seeing how they now don't, even though they support firefox on windows and mac, this is clearly a way to stick it to Linux users. Maybe ABC has a partnership with microsoft who forced them to stop support of linux. You know how much Microsoft hates free software.

---

### Post by adarkmethod on 2008-07-23
maybe someone has the old video player plugin and could share with the rest of us?

---

### Post by newsy on 2008-07-28
after reading this page [http://amyslab.wordpress.com/2008/06/26/watching-espn-360-video-in-ubuntu/](http://amyslab.wordpress.com/2008/06/26/watching-espn-360-video-in-ubuntu/)

it seems that old version works fine with wine and new version doesn't.

Doesn't anyone still have the old version?

Or is the old version not working with abc.com any more???

---

### Post by jjrp78 on 2008-07-29
well I dont think  anybody with a working plugin will get in here, and any ways doesnt it ask you to install the new plugin if you are using the old one? thats why we all updated in the first place =(

---

### Post by thutch on 2008-08-02
I was able to get the player to work using Xnest:

Xnest -geometry 1280x720 -ac :2 &
env DISPLAY=:2 /usr/bin/gnome-wm &
env DISPLAY=:2 wine "C:\Program Files\Mozilla Firefox\firefox.exe"

The above was with a bash shell.

However, while the video played it would occasionally fast-forward.  I'm guessing that this was the Move media players way of dealing with the stream falling behind real-time.  I'm on Comcast cable, so it should have enough bandwidth.  Anyway, it wasn't quite watchable on my system, but it was close.

Perhaps there's a reason why Xnest works and straight X doesn't work--could there be a setting in X that we could use?

---

### Post by asforme on 2008-08-19
Has anyone else found a fix for this yet?  Or a fix for the choppyness in the xnest window?

---

### Post by komodojay on 2008-08-24
I'm curioaus as well. I'm having the same exact situation going on. ABC and fox cause the funky colors as if it cant change the color depth correctly. Have to restart x just to get back to normal.

---

### Post by newsy on 2008-08-30
me having problems with this Xnest thing.

When starting an linux application like gedit in that Xnest window everything is fine but when starting firefox (no matter if 2.0.16 or 3.01) the adressbar and menubar is completely black. Also parts of webpages are hidden by black filds.

Anyone experienced the same problem? Is it a wrong settings in Wine?

---

### Post by newsy on 2008-08-30
some erros messages I get when starting firefox with wine:
```
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender
fixme:xrender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender

```

---

### Post by jjrp78 on 2008-09-03
thanks thutch ! it worked lika a charm.

shame that we dont have a native plug in but this trick does the work.

For those having problems with firefox opening without showing the menus I just opened firefox on normal X server then set my home page to the page of the streaming video I wanted to watch and then open it on xnest

---

### Post by jdeslip on 2008-09-11
Thutch's xnest fix works for me at espn360.com as well.  I still hope this is fixed in wine soon or that move releases the media player for linux: [http://www.mydigitallife.info/2008/08/29/intel-showcased-move-networks-media-player-on-atom-based-moblin-mid-in-idf/](http://www.mydigitallife.info/2008/08/29/intel-showcased-move-networks-media-player-on-atom-based-moblin-mid-in-idf/)

---

### Post by nynoah on 2008-09-29
I have tried wine windows firefox with the correct plugins............ I tried both firefox 2 and 3 too.  Did not work.  I get the player and the commercials.   When it comes to the program it is a black screen.  Does not lock my computer.  Just does not show anything.

Hope this helps............. but here is a site where I watch Lost.

[http://www.free-tv-video-online.info/](http://www.free-tv-video-online.info/)

---

### Post by diver858 on 2008-10-25
> **thutch said:**
> I was able to get the player to work using Xnest:

Xnest -geometry 1280x720 -ac :2 &
env DISPLAY=:2 /usr/bin/gnome-wm &
env DISPLAY=:2 wine "C:\Program Files\Mozilla Firefox\firefox.exe"

The above was with a bash shell.

However, while the video played it would occasionally fast-forward.  I'm guessing that this was the Move media players way of dealing with the stream falling behind real-time.  I'm on Comcast cable, so it should have enough bandwidth.  Anyway, it wasn't quite watchable on my system, but it was close.

Perhaps there's a reason why Xnest works and straight X doesn't work--could there be a setting in X that we could use?

Would you be so kind as to provide more detailed instructions for a newbie?

---

### Post by chengt on 2008-11-02
It means install Xnest
(sudo apt-get install Xnest)

and put the lines above into a bash script.

For example I can have ~/bin/xnestFF with
> 
Xnest -geometry 1280x720 -ac :2 &
env DISPLAY=:2 /usr/bin/gnome-wm &
env DISPLAY=:2 wine "C:\Program Files\Mozilla Firefox\firefox.exe"

then run xnestFF and it will open FF using xnest instead of x.

---

### Post by diver858 on 2008-11-06
> **chengt said:**
> It means install Xnest
(sudo apt-get install Xnest)

and put the lines above into a bash script.

For example I can have ~/bin/xnestFF with

then run xnestFF and it will open FF using xnest instead of x.

Thanks, chengt.

Followed the instructions. When I ran xnestFF, the wine Firefox window opened and I opened [www.espn360.com](www.espn360.com). Unfortunately, the result was still the same - I could hear the audio, but the video was scrambled, and eventually went to a fixed espn360.com graphic - on the main window, and the series of smaller windows across the bottom.

The terminal scrolled the following information:
```
DepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':2'.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":2.0"
      after 28 requests (28 known processed) with 0 events remaining.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":2.0"
      after 963 requests (962 known processed) with 29 events remaining.
/bin/xnestFF: line 3:  6888 Segmentation fault      Xnest -geometry 1280x768 -ac :2
```

Any suggestions?

---

### Post by wege on 2008-11-12
hello,

got the same problems with esp360.com and Move Media Player. I've searched the web and tried severall solutions. Two of them are working for me on Debian Lenny AMD64 / with wine 1.1.8 and firefox2.0.17 and NVIDIA 7900GS graphics card.

1) With Xephyr (Xnest)
Xephyr :1 -ac +extension GLX -screen 1280x1024x16 & DISPLAY=:1 wine "C:\Programme\Mozilla Firefox\firefox.exe"

alltough a little bit slow.


2) Better and much faster win-firefox2 "native" on wine 1.1.8. You have to go to the site [www.movenetworks.com/support/renderer.html](www.movenetworks.com/support/renderer.html) 
A new "Move Media plugin" will be downloaded. On the site you can adjust the settings. The video on the site will not play - you will only hear the sound - but thats ok.

Start espn360.com go to the player - login - start an archive game - wait a little bit (till you can here the sound). you will see nothing the screen should not be garbled. Go Fullscreen screen ... still dark. Press ESC to go to normal mode and YES!!!!! it works (fast). To scale the video you have to switch the X-server resolution CTRL ALT +/-. Credits to a guy on the net who gives the tip with the support site from Move (sorry lost the link of that blog).

Have fun ... :)))) ...

---

### Post by diver858 on 2008-11-14
> **wege said:**
> hello,

got the same problems with esp360.com and Move Media Player. I've searched the web and tried severall solutions. Two of them are working for me on Debian Lenny AMD64 / with wine 1.1.8 and firefox2.0.17 and NVIDIA 7900GS graphics card.

1) With Xephyr (Xnest)
Xephyr :1 -ac +extension GLX -screen 1280x1024x16 & DISPLAY=:1 wine "C:\Programme\Mozilla Firefox\firefox.exe"

alltough a little bit slow.


2) Better and much faster win-firefox2 "native" on wine 1.1.8. You have to go to the site [www.movenetworks.com/support/renderer.html](www.movenetworks.com/support/renderer.html) 
A new "Move Media plugin" will be downloaded. On the site you can adjust the settings. The video on the site will not play - you will only hear the sound - but thats ok.

Start espn360.com go to the player - login - start an archive game - wait a little bit (till you can here the sound). you will see nothing the screen should not be garbled. Go Fullscreen screen ... still dark. Press ESC to go to normal mode and YES!!!!! it works (fast). To scale the video you have to switch the X-server resolution CTRL ALT +/-. Credits to a guy on the net who gives the tip with the support site from Move (sorry lost the link of that blog).

Have fun ... :)))) ...
Attempted option 2; When I pressed ESC - nothing happened - black screen with audio. 

Also tried to download espn360 beta - Ubuntu crashed when attempting to watch a game...

---

### Post by wege on 2008-11-16
> **diver858 said:**
> Attempted option 2; When I pressed ESC - nothing happened - black screen with audio. 

Also tried to download espn360 beta - Ubuntu crashed when attempting to watch a game...

Did you try to change the renderer with the version of the move media player from their support site?

I also have a notebook with kubuntu 8.04.1 (with NVIDIA NVSxxx graphiccard)- works in the same way (very well).

---

### Post by diver858 on 2008-11-16
[QUOTE=wege;6193825]Did you try to change the renderer with the version of the move media player from their support site?

[QUOTE]

No idea how to change render - can you please elaborate?

---

### Post by wege on 2008-11-19
> **diver858 said:**
> [QUOTE=wege;6193825]Did you try to change the renderer with the version of the move media player from their support site?

[QUOTE]

No idea how to change render - can you please elaborate?

As described above you have to start the windows version of firefox 2.0.x (within wine) and than go to the site   [www.movenetworks.com/support/renderer.html](www.movenetworks.com/support/renderer.html) . Another version of the move media network plugin for windows firefox will be downloaded. On that site you can change the renderer (button). The video on that site will stay black but you should be able to view espn360.com from now on.

---

### Post by walkerk on 2008-11-19
> **wege said:**
> hello,

got the same problems with esp360.com and Move Media Player. I've searched the web and tried severall solutions. Two of them are working for me on Debian Lenny AMD64 / with wine 1.1.8 and firefox2.0.17 and NVIDIA 7900GS graphics card.

1) With Xephyr (Xnest)
Xephyr :1 -ac +extension GLX -screen 1280x1024x16 & DISPLAY=:1 wine "C:\Programme\Mozilla Firefox\firefox.exe"

alltough a little bit slow.


2) Better and much faster win-firefox2 "native" on wine 1.1.8. You have to go to the site [www.movenetworks.com/support/renderer.html](www.movenetworks.com/support/renderer.html) 
A new "Move Media plugin" will be downloaded. On the site you can adjust the settings. The video on the site will not play - you will only hear the sound - but thats ok.

Start espn360.com go to the player - login - start an archive game - wait a little bit (till you can here the sound). you will see nothing the screen should not be garbled. Go Fullscreen screen ... still dark. Press ESC to go to normal mode and YES!!!!! it works (fast). To scale the video you have to switch the X-server resolution CTRL ALT +/-. Credits to a guy on the net who gives the tip with the support site from Move (sorry lost the link of that blog).

Have fun ... :)))) ...


Thanks man. Both options worked and obviously I prefer option 2 :) I can't live w/o ESPN360.

---

### Post by diver858 on 2008-11-21
> **wege said:**
> [QUOTE=diver858;6194284][QUOTE=wege;6193825]Did you try to change the renderer with the version of the move media player from their support site?



As described above you have to start the windows version of firefox 2.0.x (within wine) and than go to the site   [www.movenetworks.com/support/renderer.html](www.movenetworks.com/support/renderer.html) . Another version of the move media network plugin for windows firefox will be downloaded. On that site you can change the renderer (button). The video on that site will stay black but you should be able to view espn360.com from now on.

Tried the above link - still no good. Session crashes when I close the wine FF window.
It is not necessary for me to login to [www.espn360.com](www.espn360.com). We have ATT-DSL, and there is an ATT logo at the top right side of all 360 windows. I receive audio, but the video starts out as a series of noisy horizontal lines on all 360 channels, and eventually default to a red and white 360 image.
When full screen, pressing escape does not seem to have an effect.
Also attempted 360 beta - also crashes the session when attempting to watch a game.

---

### Post by wege on 2008-11-22
> **diver858 said:**
> [QUOTE=wege;6212596][QUOTE=diver858;6194284]

Tried the above link - still no good. Session crashes when I close the wine FF window.
It is not necessary for me to login to [www.espn360.com](www.espn360.com). We have ATT-DSL, and there is an ATT logo at the top right side of all 360 windows. I receive audio, but the video starts out as a series of noisy horizontal lines on all 360 channels, and eventually default to a red and white 360 image.
When full screen, pressing escape does not seem to have an effect.
Also attempted 360 beta - also crashes the session when attempting to watch a game.

Is your opengl setting correct?
Please type the following on a xterm shell prompt:
$ glxinfo | grep vendor

You should get something like this (If you have a nvidia graphic card):

server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

---

### Post by diver858 on 2008-11-27
> **wege said:**
> [QUOTE=diver858;6226981][QUOTE=wege;6212596]

Is your opengl setting correct?
Please type the following on a xterm shell prompt:
$ glxinfo | grep vendor

You should get something like this (If you have a nvidia graphic card):

server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

Not sure what is meant by the vertical line and grep vendor, so I just ran glxinfo - see the following:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays
```

---

### Post by twister65 on 2008-12-05
first a ):P @ all from germany

> **diver858 said:**
> [QUOTE=wege;6231479][QUOTE=diver858;6226981]

Not sure what is meant by the vertical line and grep vendor, so I just ran glxinfo - see the following:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays
```

grep is a helpful command -> [http://en.wikipedia.org/wiki/Grep](http://en.wikipedia.org/wiki/Grep) :)

back to topic :D

i used the Move Player for the NFL Gamepass HD.
it works fine when i used the renderer direct from movenetworks.com, so thanks for the info!

my problem is, the nfl player dont allowed to resize the window. u can watch in fullscreen or in the small window. On a fullHD display it es not very usefull and the fullscreen is only black.

someone an idea / information why the fullscreen dont work? it is the same with Xenst

i used wine 1.1.9 and a portable version of firefox 2.0.18

---

### Post by bkolb on 2008-12-06
> **jsestri2 said:**
> I have attempted to watch ABC.com tv shows via instructions found on an archived forum page:

[http://ubuntuforums.org/showthread.php?t=679165](http://ubuntuforums.org/showthread.php?t=679165)

Every time I start up the abc.com player, the commercials and menus all play fine. When the show itself begins, the graphics mode flips into a weird coloring scheme that is not particularly useful (looks sort of like tie dye.) The video itself also appears extremely pixelated compared to what it should be. Once the mode has been entered, the only way to get out of it, that I have found, is to restart the x server with Ctrl+Alt+Backspace.

I have not seen other reports of this, except recently at the very end of the thread above, so I am wondering if this is a new bug. I have created a bug report: [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/237818](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/237818) it has not had any responses yet. I am wondering if anyone else sees this, or if anyone has a work around yet.

Thanks,
J.J.

Getting anywhere?

---

### Post by Laysan_A on 2008-12-19
Hi,
Just wanted to add my two cents. Tried to change my renderer at Move and it crashes every time (sends me back to the log-in splash - crashes X??). It's the same with the button for the audio.  

I don't know a thing about Xephyr or Xnest, which I assume to be utilities to alter X configurations. I'm leery of using anything like that for fear that I'd be unable to remove any changes I might make. 

Anyway, I hope someone figures out what this is soon. I really don't like to have to rely on 
windows for something like this.

Oh, by the way, I'm using Kubuntu Intrepid.

---

### Post by thecolor11 on 2009-01-28
I am having the same problem (weird colors when using the Move player in Wine). When I try the Xnest solution from above, firefox crashes and complains about a GLX error.

---

### Post by reader4 on 2009-02-15
Not having weird color problems, but the video on abc.com looks scrambled (attached).  Same when I go to the move media renderer site.  Does anyone have this working with the current move media player?  If so, please post the setup and configurations... lots of changes over the last 6 months in this thread.

---

### Post by the_weekend on 2009-02-18
Hi all,
I'm also trying to get ESPN360.com to work. I installed the ESPN movemedia plugin in my Xnested wine -> Firefox.exe. I reloaded the page and it started to load but crashed. My GLX seems fine.

I really need to watch my NC State vs. North Carolina game!

I also tried the movenetworks.com/support/renderer.html version, but now it just asks me to reinstall the plugin everytime Firefox reloads. Help!

---

### Post by the_weekend on 2009-02-18
So I seem to have gotten soudn on my girlfriend's laptop with wine, no xnest and windows ff, but it slows everything down. There's normal flash stuff around what is either a black box or says "ESPN360.com." Anyone have ideas?

---

### Post by jdeslip on 2009-02-27
I just tried this with wine 1.15 and firefox 2 for windows - no tricks.  ESPN360 and ABC.com player load fine and I can hear audio but the video is blank for both...

I wish move would just make a linux client already...

---

### Post by reader4 on 2009-02-28
> **jdeslip said:**
> I wish move would just make a linux client already...

I wouldn't hold my breath... so far, it's been more of the "stay tuned!" (for months on end) garbage from the developers...

---

### Post by jvin248 on 2009-03-19
Move Networks had several rounds of Microsoft investments poured in... so we won't be seeing any Linux support.  

Per Microsoft, they don't view apple as a competitive threat, they do however view Linux as a credible risk.  Unlikely they will allow Move Networks to support Linux.

---

### Post by woodgdo1 on 2009-03-26
I don't know if anyone cares, but I started a petition to see if Move Networks will listen to us.

[http://www.petitiononline.com/movlinux/petition.html](http://www.petitiononline.com/movlinux/petition.html)

-Doug

---

### Post by jdeslip on 2009-03-28
I signed.  I don't think it will do much good, though...

---

### Post by ddewaner on 2009-04-05
(semi-related)

Firefox+Linux+Hulu.com works like a charm.  No WINE required, just open it up and a lin compatible adobe-based player takes over.  YAY HULU!!!

---

### Post by geoffree on 2009-04-09
> **nynoah said:**
> i have tried wine windows firefox with the correct plugins............ I tried both firefox 2 and 3 too.  Did not work.  I get the player and the commercials.   When it comes to the program it is a black screen.  Does not lock my computer.  Just does not show anything.

Hope this helps............. But here is a site where i watch lost.

[http://www.free-tv-video-online.info/](http://www.free-tv-video-online.info/)

What is the story with the link that "nynoah" provided? ([www.free-tv-video-online.info](www.free-tv-video-online.info)) Is it a genuine site? Has anyone had any problem with it? Who developed it? Just normal paranoid concern about a 'free' offer.

geoffree

---

### Post by geoffree on 2009-04-09
What is the story with the link that "nynoah" provided? ([www.free-tv-video-online.info](www.free-tv-video-online.info)) Is it a genuine site? Has anyone had any problem with it? Who developed it? Just normal paranoid concern about a 'free' offer.

geoffree

---

### Post by bwestover on 2009-04-28
> **ddewaner said:**
> (semi-related)

Firefox+Linux+Hulu.com works like a charm. No WINE required, just open it up and a lin compatible adobe-based player takes over. YAY HULU!!!

But Hulu.com doesn't show ABC shows. I think Abc.com is foolish for not partnering with hulu, but thats their business. 

Also, I think Move is doing their customers (Fox, ABC, CW, Espn etc) a big disservice by failing to support Linux.

I signed the petition above, and in the mean time I'll simply get my entertainment elsewhere.

---

### Post by nefffffffffff on 2009-05-07
I am having a similar problem.  I followed the steps in the thread, and everything loads correctly.  I can see the commercial in the beginning just fine, but then when the show starts playing there is no audio or video -- but the progress bar at the bottom says that the show is playing.  Anybody else have this problem?

---

### Post by lalitgaur on 2009-06-18
Has anyone had a fix yet?

---

### Post by Philly McBlunt on 2009-06-22
I don't understand this sort of exclusion. I would really like to watch ESPN360 to catch games and things I can't see without cable television.

---

### Post by thefluxster on 2010-01-29
Ubuntu user here.  Signed petition. Passed it on to my FB friends to sign as well.  Also pinged Move Networks in their forums.

We've got to be vocal on this so they'll know how many of us there are...

---

### Post by zekemx on 2010-02-08
The latest Movenetworks player MoveMediaPlayerWin_071706000001.exe

I just installed Mozilla Firefox 3.6 with the latest movenetworks player and it worked fine.. except it was kind of slow.

So I went and test it in my Mandriva 2010 with wine 1.1.32 and WOW.. it works great... it is almost as fast as in windows.

Follow this steps..

Install the latest Firefox for windows 3.6.
Visit [www.movenetworks.com](www.movenetworks.com) and install their pluging.

Like I said.. I installed MoveMediaPlayerWin_071706000001.exe

I hope movenetworks release the linux version soon. or at least let us use it with Wine.

Good luck guys.

---

### Post by amsue on 2010-02-10
abc.com works just fine using the Opera browser in Ubuntu. Just thought I would toss that in here.

---

### Post by zekemx on 2010-02-14
> **amsue said:**
> abc.com works just fine using the Opera browser in Ubuntu. Just thought I would toss that in here.

Is that opera browser for windows in wine mode?. 

I'm confused.

---

