---
title: "wine and WoW 2.2 patch voice chat?"
date: 2007-09-28
forum: Wine
---

### Post by spydirweb on 2007-09-28
I've had a couple of the same problems as others with 2.2 patch, but I mostly have it setup to playable.  What I'm looking to do is get the new voice chat working!  Using OSS takes the mic out of my setup, but in ALSA it shows up in WoW.  Even so, in ALSA it still couldn't really do anything from what I could tell.  Maybe my mic's not setup right, but I'm fairly sure it was/is...  Anyone have any success yet with this?

---

### Post by TidusBlade on 2007-09-29
Do you mean the built in voice chat that was supposed to be released in 2.2 but didnt or another program like teamspeak or ventrilo ?

---

### Post by spydirweb on 2007-09-29
yeah, I mean WoW's new interal voice chat.  I'm actually pretty sure it's active in 2.2, because if it's not active when you go to the main menu the Sound button stays as sound, but when it is active on your server it changes to Sound & Voice... mine's Sound & Voice.  Plus a few others on my server have used it so far... and by a few I mean everyone who's wanted to... except me of course.

---

### Post by Faud on 2007-09-29
Its active on my server, i can hear in the voice chat using OSS but like you I cant use my mic.

I dont like it because I have to have my speakers like on max to hear anyone talking which means that I cant run any external sounds (music etc)

So sticking to vent or ts for now

---

### Post by gfordham on 2007-10-01
I have Feisty Fawn 7.04 with all current patches as of October 1st 2007 and I've gotten the in-game sound/mic both working using the alsa driver. Bring up a terminal and type

[FONT="Courier New"]winecfg[/FONT]

click the Audio tab and deselect OSS and select ALSA

on the wine wow wiki they mention this doesn't work for everybody but for me it seems to work fine. Also I was looking at ventrillo but it seems to have some issues with the push-to-talk functionality, where if it isn't the active window it doesn't work.

Hope that helps.

--Greg

---

### Post by reets on 2007-10-01
I ran it with ALSA and no go. I am going to try it with just wine instead of Crossover Office and see how that goes.

What do you have in the list in WoW where it says what your mic is?

---

### Post by reets on 2007-10-01
Working perfectly fine with wine 0.9.46 and winecfg set to ALSA only. Looks like it's a Crossover Office issue I was having.

w00t!

---

### Post by Drezliok on 2007-10-01
I can't talk to anyone, but I can hear them I am using alsa.


Sound Card
Sound Blaster Live Value [it's old but it sounds better than my on board.

---

### Post by sk8dork on 2007-10-01
holy crap...well, i don't have voice chat input working yet, but i upgraded to wine 9.46 and my previous alsa issues are gone..... it used to be really stuttery and echoey, but now it's clear as oss... this is exciting to me. and while we're on the subject of wine/wow, they fixed the exit crash bug. even if i don't get voicechat working (it sounds like *** anyway) i'm happy with this latest wine release!

edit, i got sound input working, but it's kinda choppy when i come across to others... not sure what the problem is. it sounds like i have a terrible connection, even when someone else in this same house is listening in, and we have a business class connection here practically.

here's my settings:
wine 9.46, from the winehq repo (winehq.org for info)
(in winecfg)
audio tab - alsa checked, oss unchecked (nothing else checked for that matter)
hardware acceleration set to full
sample rate set to 22050, default bits per sample set to 8 (i'm going to try changing these next)
driver emulation checked

i used alsamixer to set my mic capture volume all the way up, and have mic boost turned on
(press esc to exit alsamixer and then do "sudo alsactl store" to save configuration)

i'm using push to talk. i'll post more if i have updates.

oh, and i have soundblaster live audigy zs2

---

### Post by Drezliok on 2007-10-01
I'm looking into buying that card you have, my live value needs to go, Ijust got 5.1 surround sound speakers and I want to use the center speaker

---

### Post by spydirweb on 2007-10-01
mine's still not working.  I got it setup for ALSA again but it seems like nothing records.  It seems like ALSA isn't allowing any mic input, though.  My volume settings are changing frequently, even if I save and everything.  When I use Audacity, which uses OSS, I can get it to record but it's super quiet.  Any ALSA based recorders don't seem to do anything, though.  arecord, for example, is constantly saying the device is busy.  I assume this is my problem.  I'm gonna have to do some hunting tonight to see if I can find any major culprits, but it'll have to wait until after my shows (heroes, weeds, and californication... to much excellent television for one night!).

---

### Post by Pikestaff on 2007-10-01
I'd love to hear a good fix for this... OSS lets me hear others but they can't hear me, ESound doesn't let me use my microphone, and ALSA crashes my game on startup as of the lastest patch...

---

### Post by Naegling23 on 2007-10-01
I cant get this working either, the game runs fine using the oss drivers, but when i switch to alsa, it doesnt run (the sound stutters, and the frame rate drops to 1-2fps if it doesnt disconnect from the server).  I cant seem to find any settings to make this work.

---

### Post by Brokenrgv on 2007-10-02
pretty much sums up my experience as well hopefully we get some solution on this so we can share the love.

---

### Post by Naegling23 on 2007-10-02
I noticed something last night after my reply.

I am using the latest version of wine in the repro's, but this is not the latest version of wine available.  Could this be the issue?

Or perhaps my game sound settings, or my wine sound settings are not configured correctly?

Im running an audigy2, and set everything to what one of the previous posters had listed, the only difference was that I have a slightly older version of wine.  The game was not playable for me....trying to get this to work....

---

### Post by Joebob06 on 2007-10-02
I have Ubuntu 7.04 and Wine 0.9.46 and Wow ran fine for me.  I switched my audio from Oss to Alsa and the voice chat works fine for me.  Except for People hear me real soft which alot of people are having problems with.  Aoss wouldn't allow my mic to pickup the sound.  Is there any setup for Aoss besides installing it, and putting aoss wine Wow.exe?  I have a Realtek alc8883 sound card.  is there anything else I could change or setup to get better sound quality out of WIne?

Joseph.

---

### Post by sk8dork on 2007-10-02
> **Joebob06 said:**
> I have Ubuntu 7.04 and Wine 0.9.46 and Wow ran fine for me.  I switched my audio from Oss to Alsa and the voice chat works fine for me.  Except for People hear me real soft which alot of people are having problems with.  Aoss wouldn't allow my mic to pickup the sound.  Is there any setup for Aoss besides installing it, and putting aoss wine Wow.exe?  I have a Realtek alc8883 sound card.  is there anything else I could change or setup to get better sound quality out of WIne?

Joseph.

if you're just coming across quiet then you're practically there. don't change any more winecfg settings or anything, and don't run with aoss. the only reason anyone should need aoss is if they have oss set in winecfg and they want to run more than one oss app at a time. make sure your in game voice settings are so that your input volume is higher, like 250%. then in a terminal type "alsamixer" and press tab to get to the capture options and make sure your mic capture volume is turned up, then press tab again and look for mic boost and press "m" until it shows "00" instead of "MM". hit escape to exit alsamixer, then type "sudo alsactl store" to save the config. restart wow and see if that helps.

---

### Post by sk8dork on 2007-10-02
> **Naegling23 said:**
> I noticed something last night after my reply.

I am using the latest version of wine in the repro's, but this is not the latest version of wine available.  Could this be the issue?

Or perhaps my game sound settings, or my wine sound settings are not configured correctly?

Im running an audigy2, and set everything to what one of the previous posters had listed, the only difference was that I have a slightly older version of wine.  The game was not playable for me....trying to get this to work....

alsa never worked well for me until version 9.46 of wine. you need to go to [www.winehq.org](www.winehq.org) and follow their instructions on installing wine for ubuntu. that will get you the latest version. be sure to post your results.

---

### Post by Naegling23 on 2007-10-02
well, the servers are down for maintenence on my lunch break, so I'll try this out later.
I had setaudiosystem to 1 in my wow config.wtf file.  Poking around online, it looks like 1 is for oss, and 2 is for alsa, so I changed it to 2...ill see if this helps sometime tonight, ill let everyone know.

---

### Post by Drezliok on 2007-10-02
I can hear myself but no one in game can hear me, I think it's not recording or "grabbing my input for use.

---

### Post by sk8dork on 2007-10-02
> **Naegling23 said:**
> well, the servers are down for maintenence on my lunch break, so I'll try this out later.
I had setaudiosystem to 1 in my wow config.wtf file.  Poking around online, it looks like 1 is for oss, and 2 is for alsa, so I changed it to 2...ill see if this helps sometime tonight, ill let everyone know.

hmm, i was not aware of what setaudiosystem really did. i actually think i took it out of my config.wtf. i can't check it from work, so i'll look at home.

---

### Post by sk8dork on 2007-10-02
> **Drezliok said:**
> I can hear myself but no one in game can hear me, I think it's not recording or "grabbing my input for use.

when you say you can hear yourself, do you mean when you talk into the mic you can hear it in the speakers at the same time? if so, that just means you have mic playback turned up. you need to make sure that your capture settings are set to only capture the mic and that the volume is up there. i did notice that in game when the game is picking up your mic the little speaker icon that appears near your portrait animates with waves. when i had mine set up incorrectly it would just sit there like a speaker icon with no waves. once i got my mic working the in game sound test worked too. i used push to talk and when i hit the record button it turned gray and there was a little sound levels thing that moved when i talked. then hitting play actually played back my voice.

---

### Post by madsmeg on 2007-10-02
It depends on your server, some servers do not have voice chat enabled yet some do, i think blizz are slowly introducing it to iron out the problems, for all we know some windows users may be experiencing the same problems.

I think we should all wait until everything is patched properly and all is running normally before worrying about how your sound is working

P.S. i havent read through all the posts just skimmed, if someone has said somthing similar, or anyone knows ts working properly ignore this post, as for me it isnt up and running on my server yet so i cant test :p

---

### Post by sk8dork on 2007-10-02
it's implemented and up and running in gilneas. make a character there and test =p
i am sure that blizzard is still ironing out problems and will continue to do so going forward. the main complaint i hear from windows users is that some people are just soo loud, and that the quality is not so good even if the sound volume is right. my guild has tested the ingame stuff and decided that it won't cut it, so we've purchased a vent server. i pusehd for TS, but that didn't fly. oh well.

---

### Post by Joebob06 on 2007-10-02
sk8dork, 

Thanks for the info on alsa and command setup of it.  My mic is already running at 100.  Not sure if I should worry about the volume any more than what is at for now.  I left it at alsa since it was working, and no aoss since it doesn't work right.

Thanks again.

---

### Post by Naegling23 on 2007-10-02
so I tried the setoutputsystem from 1 to 2, didnt work

im going to just wait until the wine update appears in the repro's, I dont need the voice chat right now anyway, so Ill work on it at a later time.

But if anyone figures it out.....

---

### Post by Naegling23 on 2007-10-02
got the update, game works fine with the alsa drivers now...
sweet...

got the microphone test working in the setup, havnt had a chance to see if the voice chat actually works yet though.

---

### Post by Faud on 2007-10-03
ive got the microphone working using ALSA but its extremly choppy when people hear me talk. Also, how to I stop hearing myself through my speakers ?

---

### Post by tparker on 2007-10-03
> **sk8dork said:**
> alsa never worked well for me until version 9.46 of wine. you need to go to [www.winehq.org](www.winehq.org) and follow their instructions on installing wine for ubuntu. that will get you the latest version.

I went to winehq last night (Oct. 2nd) and followed the instructions and it did get me a newer version, but it looks like not the new-est- version. I went from 9.22 to 9.45. WoW itself had worked in 9.22 but after these last two patches I had no game sound at all. All my regular Ubuntu sound, you-tube, dvds, banshee, etc. still had sound, but nothing at all in WoW. I was hoping that moving to a newer wine would at least give me game sound back, if not voice chat, but it didn't. 

Any suggestions?

I have gone in game and verified that I have game sound turned on.
I tried switching settings between oss and alsa in winecfg.
I tried changing winecfg settings for sound hardware/emulation.

I have onboard ac97 sound and a Logitech USB head set. Both have worked for WoW in the past. I am now running wine 9.45 in Dapper AMD64.

---

### Post by sk8dork on 2007-10-03
> **tparker said:**
> I went to winehq last night (Oct. 2nd) and followed the instructions and it did get me a newer version, but it looks like not the new-est- version. I went from 9.22 to 9.45. WoW itself had worked in 9.22 but after these last two patches I had no game sound at all. All my regular Ubuntu sound, you-tube, dvds, banshee, etc. still had sound, but nothing at all in WoW. I was hoping that moving to a newer wine would at least give me game sound back, if not voice chat, but it didn't. 

Any suggestions?

I have gone in game and verified that I have game sound turned on.
I tried switching settings between oss and alsa in winecfg.
I tried changing winecfg settings for sound hardware/emulation.

I have onboard ac97 sound and a Logitech USB head set. Both have worked for WoW in the past. I am now running wine 9.45 in Dapper AMD64.

9.45 was crap for me too. in 9.45 the crash on exit bug is still present and you have to use OSS with hardware acceleration mode set to emulation, alsa didn't work too well in this version. do an update in synaptic then mark all upgrades, wine 9.46 should be in there if you followed the instructions from the winehq site. with 9.46 alsa seems to have been greatly improved to the point where i have absolutely zero problems, whereas before i had nothing but problems.

> **Faud said:**
> ive got the microphone working using ALSA but its extremly choppy when people hear me talk. Also, how to I stop hearing myself through my speakers ?

i am at the same point you are. alsa is great, mic works, in the sound/voice settings the mic test works but when people hear me it is very very choppy. 

you can stop hearing yourself through speakers by turning the volume of your mic all the way down. note: i mean playback volume, not capture volume. whatever sound volume manager thing you use, take notice whether you are in playback settings (you will also see master, pcm, things like that) or capture (there are less options in capture settings typically). the way i did it was by going into a terminal and running "alsamixer" without the quotes. you use tab to change between playback, capture, and all. in the playback settings turn down the mic all the way.

---

### Post by spydirweb on 2007-10-03
Ok, it seems that my system can actually do the voice chat like a few others.  The problem is people can't hear me.  I'm not sure why considering system volume's all the way up, wow's is at 250%, and blah blah blah.  However, they say "well I can see that you're talking... but I can't hear it."  I think the best thing to do is wait and see if the wine developers go "oh wow, that's a silly bug."

---

### Post by mad chey on 2007-10-10
Great thread guys, having been playing wow thru cedega for a very long time perfectly im now trying it thru wine as cedega will not seem to get the mic for wow.

im not sure why it wont, i do know that we used to use vent thru cedega perfectly fine so its prob the wow/cedega relationship as opposed to cedega alone.

installing the latest wine as i type so fingers crossed

:)

installation of wine and wow went flawlessly, ive got voice chat working, been told they hear me fine, but im getting a bit of choppyness my end, and bonus to boot, my frame rate is fantastic compared to the norm i got running wow thru cedega, used to get between 15 and 45, averaging 90 - 120 so far, so i must say im mucho impressed with wine,

hats off to the designers, if this continues i can see our subs to cedega stopping

sources

[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

[http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft](http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft)

tbh i cant remember what i did, and in what order, i just read the pages, and tinkered, :)

---

### Post by babacan on 2007-10-13
Any idea to increase the sound ? I maxed everything to max in wow and in ubuntu control panel but still sound is very low :S

---

### Post by Rajia on 2007-10-21
> **sk8dork said:**
> ... then in a terminal type "alsamixer" and press tab to get to the capture options and make sure your mic capture volume is turned up...

Sk8, My <Mic> setting in the capture tab is red and it says Captur with a little L and R above it--I can't make modifications to this setting at all, it seems.  Not the normal sort of up and down white/green/red bar here--just the word captur and the L and R immediately above it.  Is there something I haven't done here?  Like--is the mic not turned on??  I've had this working on vent before but that was with dapper and now I'm using feisty.  I can hear fine with the voice chat but, of course, am unable to speak.  Was using aoss at WoW launch, have switched to alsa and now have driver options when I choose the input device in WoW in the voice chat menu options.  Hmm.  Hope that's enough info . . . let me know if you need more.  Any thought?

Cheers

---

### Post by adw404 on 2007-10-22
Similar problem, the grey bar animates and the mic works with audicity, mic input set to USB audio. guildmates can hear interference and no voice chat. any help?

---

### Post by hikaricore on 2007-10-23
In an effort to clean up the Gaming and Leisure section of our forums and
reduce the number of World of Warcraft threads, I have stickied this thread
for you all to use: [http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

Please consider posting there instead.

I'm moving new posts but leaving existing threads such as this alone with only the suggestion.

Thanks,

--Aaron

---

### Post by mnfiddledragon on 2008-03-06
> **Joebob06 said:**
> I have Ubuntu 7.04 and Wine 0.9.46 and Wow ran fine for me.  I switched my audio from Oss to Alsa and the voice chat works fine for me.  Except for People hear me real soft which alot of people are having problems with.  Aoss wouldn't allow my mic to pickup the sound.  Is there any setup for Aoss besides installing it, and putting aoss wine Wow.exe?  I have a Realtek alc8883 sound card.  is there anything else I could change or setup to get better sound quality out of WIne?

Joseph.



Joseph,

My housemate has this same issue in Windows, so it may not entirely be a linux issue. That being said, I used her headset when testing and found that I had lower volume, which went away when I switched headsets.

aoss has no problems with allowing me to switch in-game pickup settings.

Something to think about. 
LIz

---

