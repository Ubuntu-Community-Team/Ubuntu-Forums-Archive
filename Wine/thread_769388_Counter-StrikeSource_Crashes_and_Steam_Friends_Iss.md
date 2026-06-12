---
title: "Counter-Strike:Source Crashes and Steam Friends Issues"
date: 2008-04-26
forum: Wine
---

### Post by TacOpsDELTA on 2008-04-26
Ok If i sound noob I apologize. I am a fairly proficient windows user but have decided to go to linux as hoping to get some better performance out of my older PC.

My System is

AMD Semperon 3300+
1.5 Gig Ram
Biostar m7NCG mainboard
ATI Radeon 9600 Pro Vid card (probally issue)

I have found a .exe for steam and have installed that successfully and downloaded Counter-Strike Source.

I launch CSS and my computer locks up. It goes black then flashes for just an instant what you would see if you were loading CSS. I have tried to install the Drivers from ATI and had no success. 

I put it on my home dir and then go to terminal and type 

```
 ati-driver-installer-8-4-x86.x86_64.run 
```
and get error
```
 bash: ati-driver-installer-8-4-x86.x86_64.run: command not found

```

2nd Issue

In Steam Chat I can send messages but can not see the text i typed (once i hit enter but until then i can see the text) nor the reply to the msg. 


Any ideas on what i can do to fix this?


Also I do believe i have wine installed.

---

### Post by ad_267 on 2008-04-26
To run this installer you would first probably need to make it executable using:
```
chmod +x ati-driver-installer-8-4-x86.x86_64.run
```

Then execute it using:
```
./ati-driver-installer-8-4-x86.x86_64.run
```

The ./ part is needed when executing files in the current directory.

See if anything here helps: [http://blog.linuxoss.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://blog.linuxoss.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)

---

### Post by TacOpsDELTA on 2008-04-26
Ok I type in the 2 Lines of Code you Give me and On the 2nd Bit it gives me the error that i need to be logged in as a super user. I am the only user lol. And I try and follow that tout and get lost. Could I contact you on IM or something like that so I can try and get this figured out?

---

### Post by ad_267 on 2008-04-26
To use a command as superuser you need to put sudo (superuser do) in front of it, so:
```
sudo ./ati-driver-installer-8-4-x86.x86_64.run
```

I don't have any experience using counter strike source in wine, or even using wine at all for that matter and I've only had experience setting up my nVidia card so I probably can't help you much more than that sorry. Hopefully someone else can be more helpful.

---

### Post by TacOpsDELTA on 2008-04-26
Ok Thanks That Launched the Installer and I got it installed (i think) did a restart on computer (not sure if neccecary but im an ex windows user and well you restart after everything LOL...(as in your sig)). But im getting the same issues with my game. Also I have The Font the link you gave me has me get and i tried to put it in there, but there wa already a font in there like that, yet i can not see the text being sent to me?

---

### Post by ad_267 on 2008-04-26
Ok, do you also have the msttcorefonts package installed? Try:
```
sudo apt-get install msttcorefonts
```

From that page there was this in the troubleshooting section:
> Q: Steam runs fine but the game freezes on start.

Try setting the OSS sound driver in winecfg.

Like I said I haven't used wine before so I don't know about how to change settings in winecfg. I'm guessing you can just type winecfg into a terminal or something. It sounds like this could help though.

There was also this one:
> UPDATE 0.49.x (25.11.07): When loading CS:S you see the loading screen (that with the two CT guys) and then you get a black screen, see the loading screen again and then the game crashes/doesn&#8217;t launch, then here is what might help:

1. Launch regedit -> wine regedit

2. Navigate to [HKEY_CURRENT_USER\Software\Wine\Direct3D]

3. Add a String with the name &#8220;VideoMemorySize&#8221; , and then amount of video RAM you have, ex: 256

---

### Post by TacOpsDELTA on 2008-04-27
Ok I did the Font Install and the Driver that I was asked to do, and am updating CSS once more after reinsalling Ubuntu 

The Steam Friends Does not work even after i put the tahoma.ttf font in the wine/windows/font folder and also after installing the font pack that i was asked to do? Any other ideas. I will update this post as soon as i can launch CSS.

---

