---
title: "Steam - Wine - OSS: No sound using OSS"
date: 2007-09-14
forum: Wine
---

### Post by OffHand on 2007-09-14
Hi All,

I got Steam and Steam games like Half Life 2 running with sound using ALSA. Unfortunately ALSA crashes/freezes the games. I tried to use OSS but OSS does not give me any sound at all. Is there any way I can use the OSS sound drivers and get sound?

Thanks in advance,

OffHand

---

### Post by OffHand on 2007-09-14
Not solved. I think I did put it back to ALSA last night.

---

### Post by Ferrat on 2007-09-14
try installing ALSA-OSS from synaptic if you don't have it, could help

---

### Post by OffHand on 2007-09-15
> **Ferrat said:**
> try installing ALSA-OSS from synaptic if you don't have it, could help

alsa-oss is installed already. And I know it works because the cat /dev/urandom >> /dev/dsp gives me a static noise.

---

### Post by OffHand on 2007-09-16
Anyone? I know OSS works because I am able to play hear sound when I play music in my music player.

---

### Post by ubu-for on 2007-09-18
> **OffHand said:**
> Unfortunately ALSA crashes/freezes the games. I tried to use OSS but OSS does not give me any sound at all.

I have the same problem since the last Steam update couple days ago.

---

### Post by wana10 on 2007-09-18
i was having that same problem. i found that if i started a web-stream through mplayer in the terminal i would hear sound in steam games, but i didn't like this solution as i wanted to listen to the sound of the games without background music. so here's what i did. pull up a terminal and run 'winecfg' go to the audio tab, unclick everything except alsa. on the bottom set sample rate to 48000 , hardware accel to full, and driver emulation is not clicked. now your results may vary but this did it for me and i once again get full sound in all steam programs.

---

### Post by nchase on 2007-09-19
> **wana10 said:**
> i was having that same problem. i found that if i started a web-stream through mplayer in the terminal i would hear sound in steam games, but i didn't like this solution as i wanted to listen to the sound of the games without background music. so here's what i did. pull up a terminal and run 'winecfg' go to the audio tab, unclick everything except alsa. on the bottom set sample rate to 48000 , hardware accel to full, and driver emulation is not clicked. now your results may vary but this did it for me and i once again get full sound in all steam programs.

This seems to have worked for me. Thanks a lot!

---

### Post by OffHand on 2007-09-19
ALSA works without a problem. It is OSS that refuses t work with WINE.

---

### Post by bsmith on 2007-09-19
Hey, I've been having the same problems, until the latest steam update hl2 has been working awesomely, but now if I run it with OSS I have no sound with the following error in the console

```
Failed to write block to device
```

And if I try to run using ALSA it works fine until i turn the Shadow detail to high (it will run, but freezes).

It looks fugly without the Shadow detail on High, any ideas on a solution, Thanks in advance.

---

### Post by bsmith on 2007-09-20
I seem to have fixed the problem by forcing a lower dx level using

```
-dxlevel 70
```

So I'm not sure if the crashing is related to the sound issues.

---

### Post by ubu-for on 2007-09-20
> **wana10 said:**
> i was having that same problem. i found that if i started a web-stream through mplayer in the terminal i would hear sound in steam games, but i didn't like this solution as i wanted to listen to the sound of the games without background music. so here's what i did. pull up a terminal and run 'winecfg' go to the audio tab, unclick everything except alsa. on the bottom set sample rate to 48000 , hardware accel to full, and driver emulation is not clicked. now your results may vary but this did it for me and i once again get full sound in all steam programs.

ALSA-OSS and your tips don't work for me!

---

### Post by anemptygun on 2007-10-04
> **wana10 said:**
> i was having that same problem. i found that if i started a web-stream through mplayer in the terminal i would hear sound in steam games, but i didn't like this solution as i wanted to listen to the sound of the games without background music. so here's what i did. pull up a terminal and run 'winecfg' go to the audio tab, unclick everything except alsa. on the bottom set sample rate to 48000 , hardware accel to full, and driver emulation is not clicked. now your results may vary but this did it for me and i once again get full sound in all steam programs.

Im gonna try this out, thanks in advance if it works.

---

### Post by ubu-for on 2007-10-05
With Win98 CSS didn't crash very often, but since the new Steam update Win98 is not supported any longer.

So I've switched to WinXP and Vista, but now CSS freezes within 5 minutes.

I need OSS back!

---

### Post by anemptygun on 2007-10-06
> **ubu-for said:**
> With Win98 CSS didn't crash very often, but since the new Steam update Win98 is not supported any longer.

So I've switched to WinXP and Vista, but now CSS freezes within 5 minutes.

I need OSS back!

I have the exact same problem. PLEASE HELP[-o<

---

### Post by ubu-for on 2007-10-07
ALSA works here with Wine 0.9.44 and WinXP mode.

---

### Post by anemptygun on 2007-10-07
Was wine updated as well?

---

### Post by ubu-for on 2007-10-07
The current Wine version is 0.9.46 and I've downgraded to [0.9.44](http://wine.budgetdedicated.com/archive/index.html), but it still crashes sometimes.

---

### Post by anemptygun on 2007-10-08
> **ubu-for said:**
> The current Wine version is 0.9.46 and I've downgraded to [0.9.44](http://wine.budgetdedicated.com/archive/index.html), but it still crashes sometimes.

do i need to manually installed the update? because synaptic is not recognizing there is an update.

I am on 0.9.33

---

### Post by OffHand on 2007-10-08
> **anemptygun said:**
> do i need to manually installed the update? because synaptic is not recognizing there is an update.

I am on 0.9.33

He is using the version from the WINE repositories...

---

### Post by ubu-for on 2007-10-08
I've posted a bug report at launchpad.net, so if you would like to add some further informations, please use the following link.

[Bug #150575](https://bugs.launchpad.net/ubuntu/+bug/150575)

---

### Post by peabody on 2007-10-14
A thing to try is the alsa-oss package.  Install that, then run steam from the command prompt:

cd ~/.wine/drive_c/Program\ Files/Steam
aoss wine steam

That got the original half-life working with oss.  HL2 never worked with OSS for me, I had to use alsa.  Playing with the sound settings in winecfg can prove fruitful.  Main thing is to make sure Hardware acceleration is set to emulation if you have a crappy soundcard (like I do).

Running Half-Life 2 just fine with alsa here on a POS intel i950.  Believe it or not, the game is somewhat playable on this thing.

---

### Post by sardiax on 2007-10-15
i'm fairly new to linux so i don't understand the underlying mechanisms, but lately i've had problems with steam itself like stealing the oss sound focus. the solution i found was basically to setup wine to use oss. launch a music player - or some other app to block steam from using oss. launch steam, close the music player, and then launch the game - half-life, team fortress, tf2 etc. it's the only way i can seem to get sound working in-game. maybe this'll help some of you other guys, but i'm sure there's a better way to stop steam from blocking the games off, i'm just not knowledgable enough about the underlying sound system.

---

### Post by jakommo on 2007-10-19
Hi,

I had the same problem, i've installed alsa-oss and applied the setting posted here and now it works.

thank you very much indeed.

---

### Post by ubu-for on 2007-10-20
> **peabody said:**
> cd ~/.wine/drive_c/Program\ Files/Steam
aoss wine steam

No difference!

Wine 0.9.44, ALSA and low audio volume settings for CSS works nearly stable.

---

### Post by Norrbagge on 2007-10-26
> **wana10 said:**
> i was having that same problem. i found that if i started a web-stream through mplayer in the terminal i would hear sound in steam games, but i didn't like this solution as i wanted to listen to the sound of the games without background music. so here's what i did. pull up a terminal and run 'winecfg' go to the audio tab, unclick everything except alsa. on the bottom set sample rate to 48000 , hardware accel to full, and driver emulation is not clicked. now your results may vary but this did it for me and i once again get full sound in all steam programs.

awesome... i had the problem where i had sound in WoW but not in CS 1,6... I tried this and it works. now i have sound in CS and in WoW... I also want to add that i use 7,10 Gutsy, but did the trick for me... Thanks alot...:guitar:

---

### Post by juamez. on 2007-11-10
> **wana10 said:**
> i was having that same problem. i found that if i started a web-stream through mplayer in the terminal i would hear sound in steam games, but i didn't like this solution as i wanted to listen to the sound of the games without background music. so here's what i did. pull up a terminal and run 'winecfg' go to the audio tab, unclick everything except alsa. on the bottom set sample rate to 48000 , hardware accel to full, and driver emulation is not clicked. now your results may vary but this did it for me and i once again get full sound in all steam programs.

This did it for me also.

Using Ubuntu 7.10 and wine version 0.9.46.

---

### Post by MACRI on 2007-11-10
same problems here, going to try wana's solution - will post resaults. thanks guys.

---

### Post by FilmAficionado on 2007-11-10
That fix worked for me as well guys.

But is there a way to notify somebody (a specific bug-report) that we could ALL file in order to get this fixed, so this won't remain the state of gaming under Linux?

---

### Post by stiansoftcore on 2008-03-21
> **wana10 said:**
> i was having that same problem. i found that if i started a web-stream through mplayer in the terminal i would hear sound in steam games, but i didn't like this solution as i wanted to listen to the sound of the games without background music. so here's what i did. pull up a terminal and run 'winecfg' go to the audio tab, unclick everything except alsa. on the bottom set sample rate to 48000 , hardware accel to full, and driver emulation is not clicked. now your results may vary but this did it for me and i once again get full sound in all steam programs.

this worked. Mind if i make a _small_ guide on the ubuntu.no forum? if u say no, I'll still do it :P

---

### Post by Gigopepo on 2008-04-24
Same problem, Steam games doesn't run with sound with ALSA nor OSS.
The weird thing is that when I first installed steam and downloaded my games it worked just fine!

Now I doesn't work...

I just NEED steam games!!!

Using Ubuntu 7.10 64bits.
And I have a fairly good pc...

---

### Post by Gigopepo on 2008-05-02
Mine is now working!!
 Just changed the configuration in the "system > sound" menu to ALSA (instead of "Auto-detect"
And now I have sound with my dear steam games! 
(my profile ID is gigopepo bt the way, if anyone wants to play DoD:S, CS:S, CS 1.6 and TF2!!!!)

---

### Post by DocPaine on 2008-05-06
Solved!  Thanks for all the advice -- HL, HL:S, HL2, CS, CS:S all working again!  Honestly, the only reason I ever boot back into MS anymore is for TES4:Oblivion, DoW, and Bioshock (purchased through Steam but *still* can't get it working -- but I'll leave that issue for another thread...)

Cheers,

Doc

---

