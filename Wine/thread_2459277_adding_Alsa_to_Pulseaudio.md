---
title: "adding Alsa to Pulseaudio"
date: 2021-03-15
forum: Wine
---

### Post by mastablasta on 2021-03-15
i've been trying to solve an issue where some wine games get a slow down in audio and overall slowdown every once in a while (GTA:SA and Oblivion might also have this issue with sound). so i was thinking that perhaps adding and using alsa might solve the problem. Pulsewire supposedly solves these kind of issues but on 18.04 it is still very beta. i also saw a solution from one user where they switched to Alsa in wine configuration for GTA and it then worked fine.

so how do i add alsa driver without damaging default pulseaudio set up (which is now default and works fine for native linux games)?

so mission is to keep pulseaudio and just add alsa option in wine.

---

### Post by Holger_Gehrke on 2021-03-15
There's a setting in winetricks ('Select the default Wineprefix'->'Change settings'->'sound=alsa'). You might have to start wine with pasuspender to disable Pulse for the duration of your wine session.

Holger

---

### Post by Yellow Pasque on 2021-03-15
Your system is already using ALSA for the kernel modules (aka drivers), so you cannot "add" ALSA.
(Pulseaudio does not handle kernel modules/drivers. Think of it as a software mixing layer that sends sound to the ALSA device.)

WINE can use pulseaudio directly (libpulse). If you switch WINE to use "alsa", it's really using libasound, which was the native way to use ALSA devices before pulseaudio. Nowadays, distros configure libasound to go through pulseaudio via a wrapper/plugin.

If you want to bypass pulseaudio, you can use pasuspender as Holger_Gehrke suggested. You will have to add your user to the "audio" group in /etc/groups, and other configuration may be needed.

---

### Post by mastablasta on 2021-03-15
uf sounds difficult. then what are all the alsa packages in repos not currently installed? do i need some extra packages added maybe?

wine says selected driver winepulse.drv   
in winecfg only pulseaudio or system default are the options, but i've seen other screenshots where they had ability to also choose alsa.


i really don't know much about sound drivers. as i understand alsa communicates all directly with kernel and pulse audio communicates with alsa.

heh, not pulse wire. it's pipewire: [https://wiki.archlinux.org/index.php/PipeWire](https://wiki.archlinux.org/index.php/PipeWire)

probably available in 22.04? and supposedly solvles these kind of sound stuttering and slowdowns in game where CPU handles all the sound (instead of sound chip) and then everything gets suden slowed down. people talk in slow motion. it happens in spikes, so it is not constant, but slow down, no slow down, slow down...kind of annoying when you listen people talk and i think it is because this old CPU is handling (maybe to much) sound processing. it's interesting that this is not present in all wine games. some work very fluently with defaults. but then again maybe not all have so many channels? so i was hoping for an easy solution for the couple of games that act strange with sound.

---

### Post by CatKiller on 2021-03-15
> **mastablasta said:**
> i've been trying to solve an issue where some wine games get a slow down in audio and overall slowdown every once in a while (GTA:SA and Oblivion might also have this issue with sound). so i was thinking that perhaps adding and using alsa might solve the problem. 

I think you're mistaking cause and effect. The sound is slow because the computer is slow, not the other way round. If the game isn't producing the sound samples fast enough, they can't get to the sound card. 

If you're resampling your audio you will have higher CPU usage than if you're not, but it's only a marginal difference. Your machine just seems to be under specced for what you're asking it to do. A couple of percent from avoiding resampling is unlikely to make a difference, but it's easy enough to try. 

> **mastablasta said:**
> i really don't know much about sound drivers. as i understand alsa communicates all directly with kernel and pulse audio communicates with alsa.

Yes. ALSA handles all the sound hardware. Initially you could only have one thing playing at a time. Then ALSA got a software mixer, called dmix, that could mix streams together, but it was still pretty limited. Dmix is what got replaced by PulseAudio. There's absolutely no benefit to using dmix rather than PulseAudio.

---

### Post by mastablasta on 2021-03-16
yes, CPU is old, but so are the games. maybe i missed a windows library or something else in wine.

i have a bunch of native steam games - source games - Half life 2 series, L4D2, CS:GO, Synergy, Gary's mod, Original HL, Portal 1 & 2... then A Story about my unlce and few other native games that i got over steam and they all work fine. ok some load slow (like CS:Go) but otherwise they work fine on medium or high settings.

Then i installed native games like Minecraft, various kind of pixel art games like Don't starve, FTL, Supertux Cart, then UFO AI, 0AD, smokin guns, Xonotic...

Then a bunch of old games into opensource ports/engines like Doom 3 in dhewm3, Morrowind in OpenMW, Arx Fatalis in Arx Libertatis, Doom 1,2 + Heretic + Hexen in Doomsday engine, Jedi Academy in OpenJA, Jedi Knight in openJK...

Finally i also installed a bunch of games using Play on linux / Wine such as FEAR, Far Cry 1 & 2, Oblivion, Company of Heroes, Hitman Blood Money, Stalker Clear Sky, Rome Total war, Civ4, Halo, Star Trek Elite force 1&2, Galactic Civilizations 2 Call of Duty 2, Unreal, Unreal Tournament 2004, Hearts of iron 2, Torchlight (Arx Fatalis (yes also wine version to compare...), Battlefield 2...

Anyway i've been busy. all native engine games are set to max or medium settings (CS:GO, 0AD i salso medium i believe) and i have no major issues. same goes for opensource engines. with wine games i start low and then increase settings. Far cry 2 has much better performance on linux, most are about the same. some maybe slightly worse, but you can lower the settings a bit or turn off some things and you are back in business.

the only ones that are acting kidn of strange are Hitman - the character movement is kind of strange at times (like he is sliding across the floor instead of walking) and occasionally FPS would drop. so i attribute this to some library maybe msisign or maybe wrongly setup. in any case i played it thorugh a couple of times. so the issue is not that terrible.

Oblivion - sudden slow downs and FPS drops when there is more sound or talking arround, but overall still quite playable and i already finished about half of quests and game but now i don't have much time to finish the main quest. but i was thinking if maybe same issue is causing the trouble here.
GTA: SA - this one has slow down as soon as more than one sound is playing. e.g. when you go to car and they strat talking while the music is playing and car engine is working. this one is th emost curious of them all as everythign actually slows down. it's not like there are interuptions, but music tempo slows down. ther eis some fix on wine website about some shaders that are causing that but this fix is no longer available it seems. or maybe it was incorporated into the wine already (since report is so very old). anyway i moved to the next reported slow down trouble & solution and the solution given was to switch in wine from pusleaudio to alsa and supposedly theslow down dissapears.


which is why i though that adding some pakcage could help me do that, but ti seems this solution is also too old. or way too complicated. seems easier to me to just get a new CPU :D GTA are not really known for their optimised engine.

---

### Post by Yellow Pasque on 2021-03-16
winealsa.drv is included as part of libwine. You don't need any extra packages.
Try this:
```
winetricks sound=alsa
pasuspender winecfg
```
Set your device(s) and test it. If it works, try running problematic game with pasuspender:
```
pasuspender wine <path to game.exe>
```

---

### Post by mastablasta on 2021-03-18
some progress is made, now only music is slow. all movement and everything else is much smoother now. but i need more time to try some other things.

This is definitely wine /playonlinux configuration issue not system wide as i originally thought. i will report this thread to be moved to wine forum. if i figure it out (maybe over weekend) i will post a solution there. Playonlinux has some commands made a bit different so i am learning a bit of scripting there and how they do it.

---

