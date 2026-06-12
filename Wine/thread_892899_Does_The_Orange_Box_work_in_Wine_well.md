---
title: "Does The Orange Box work in Wine well?"
date: 2008-08-17
forum: Wine
---

### Post by RATM_Owns on 2008-08-17
I've been thinking about buying The Orange Box and I wanted to know if it would work fine under Wine. Didn't really want to waste $20.

The App Database at winehq.org says Portal and Team Fortress 2 work fine, but has anyone here ever tried them?

---

### Post by aoanla on 2008-08-18
Yes. I've played through every game in The Orange Box in Wine.

Half-life 2 and the Episodes are fine (although you need to tweak some settings to avoid slowdown in the reactor in Episode One).

Portal and Team Fortress 2 are fine, with -dxlevel 81 set (there's some interaction between the Source Engine's DirectX 9 stuff and Wine which causes it to be Really Slow).

This using a Geforce 8800GT with the latest nVidia drivers and any version of wine after 0.9.60 

With ATI cards, your mileage may (and apparently, from some of the threads here, will) vary.

---

### Post by Brynster on 2008-08-18
> **aoanla said:**
> Yes. I've played through every game in The Orange Box in Wine.

Half-life 2 and the Episodes are fine (although you need to tweak some settings to avoid slowdown in the reactor in Episode One).

Portal and Team Fortress 2 are fine, with -dxlevel 81 set (there's some interaction between the Source Engine's DirectX 9 stuff and Wine which causes it to be Really Slow).

This using a Geforce 8800GT with the latest nVidia drivers and any version of wine after 0.9.60 

With ATI cards, your mileage may (and apparently, from some of the threads here, will) vary.

I absolutely agree with the above

Been playing Counterstrike and HL2 since wine 0.9.15 (ish) and they have improved to a point where they are 95-98% identical to Windows installs.

a few small grievances but no show stoppers, mainly to do with the steam client rather than the games.

If you struggle theres plenty of threads and bods to help here.

---

### Post by Toupee on 2008-08-18
Yep.  Just make sure you right click the game in Steam, go to Properties, set launch option -dxlevel 81 ... some games might work with dxlevel 90 but I'm likely to get black boxes where important information should be (health, ammo).  I also use -window, seems to make things work a little more smoothly for me at least.

---

### Post by Bios Element on 2008-08-19
For me, with a Nvidia card and PulseAudio everything but the headset works absolutely fine. The Orange Box games all work fine for me. The biggest bug i think i saw was a strange texturing on a box or something along those lines. Nothing that would hinder your gameplay.

---

### Post by dansued on 2008-08-30
When I load the game up, it goes through the valve and source spash screens and then quits out with something along the lines of "Engine error: No Permissions to run tf" This is especially frustrating because when I was fiddling with it earlier I was able to get it to work and join a server. Can anybody help me?

---

### Post by aoanla on 2008-08-30
That's not a Wine error, but a well-known glitch in Steam that sometimes happens (even on Windows). The normal advice is just to restart Steam, and it should work.

---

### Post by nicbul on 2008-10-05
I just purchased the Orange Box and am having some difficulty.

Wine itself has some issues-half of whatever screen is opened is not visible and can only be made visible by dragging it around the desktop.

I can load Half Life 2 but I get nothing after the splash screen (which is very glichy looking-artifacts, etc.).  I have to restart X or restart completely to get out of it.

I installed WINE 1.1.5 (the one in synaptic) and followed some instructions here:

[http://news.softpedia.com/news/How-To-Play-Half-Life-2-on-Ubuntu-74731.shtml](http://news.softpedia.com/news/How-To-Play-Half-Life-2-on-Ubuntu-74731.shtml)

I'm using using 8.04lts 64bit.


It appears to me that wine is very unstable and the site itself describes 1.1.5 as a development release.  

What version of wine is stable and can run the Orange Box successfully?

---

### Post by Gcentrex on 2008-10-05
I'm currently running the Orange Box on Wine 1.1.5 and I am not having many issues just Steam window is slow no point installing flash support as it wont load right and slows steam down anyways, but in game when launched with -dxlevel 81 -window, my Source engine games run just fine, but this was the same even when I was running Wine 1.0 stable.

I find 1.1.5 is much better for the common games I play now install without using Native files this has saved me messing around changing files just to get another game/application running. The games/applications that need Native files are now installed into another wine prefix this same a lot of bother later on.

---

### Post by Twitch6000 on 2008-10-06
I do not have steam or orange box,but from what I read and what other friends have said it should work well.

I have also looked on the wine db and the only game that has given trouble alot would be half life 2 or counter strike 1.6.

---

### Post by thefishki345 on 2008-10-06
The orange box runs fine for me. Though just remember for some reason everytime I start portal, hl2 ep2 and tf2 my graphics settings go back to very low and low, but I usually have them on very high no problem, so everytime you start the game you should redo your graphics settings.

---

### Post by jyaan on 2008-11-25
I play it on Wine 1.1.8 and it runs very well. I use "Very High" for whatever settings can be set that way. Latest stable should be fine too.

---

### Post by forest.r on 2008-11-25
> **dansued said:**
> When I load the game up, it goes through the valve and source spash screens and then quits out with something along the lines of "Engine error: No Permissions to run tf" This is especially frustrating because when I was fiddling with it earlier I was able to get it to work and join a server. Can anybody help me?

I have had that problem when running TF2, I found that making sure that my avant window navigator bar is hidden when the game starts prevents that error. If you use AWN this should help; otherwise, ignore me.

---

### Post by Outlit on 2008-11-25
Are you interested in making absolutely free money?

Nothing better then Bux.to!

Click here and join today -----V

[[IMG]http://i423.photobucket.com/albums/pp318/Outlit/banner.png[/IMG]]("http://bux.to/?r=Outlit")

---

### Post by chris062689 on 2008-11-26
Remember: You only need to add the -dxlevel 81 option once.
Once it's set to DX8.1 (on that first run) you need to remove that line, otherwise it'll revert your graphics again.
It will stay in DX8.1 mode.

---

