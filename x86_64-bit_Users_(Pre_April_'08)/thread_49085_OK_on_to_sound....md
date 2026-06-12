---
title: "OK on to sound..."
date: 2005-07-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Boggles3 on 2005-07-15
alright i have alsa-oss and all that dandy stuff and ive gone in #alsamixer to make sure i dont have things muted ..

at first i didnt have sound at all then i heard something about digital/analog switching for my sound card wich is audigy 2 (everyone seems to have problems with these)

so i fiddles with how i plugged the speakers into the comp and i got sound finally but its all fuzzy.. like really fuzzy..
any one able to help i dunno what to do anymore..???

---

### Post by Boggles3 on 2005-07-15
ok update time

i have come across some interesting this while poking around with sound and i dunno maybe it will ring bells to some of you more avid linux people :) 

ok first thing that i noticed..
if i go into volume control and enter prefs and it ses select device and track to control..
i have device choice of sound blasteraudigy 2 (alsa mixer) or SigmaTel STA9721/23(oss mixer)

anyone know what the second one is and why i have two devices both outputing sound... cant i have oss using audigy 2

i was thinking that the sigmaTEl thing was my onboard  sound .. but dont i want oss and also both using the same device cuz if they werent wouldnt that caus a conflict..

and in the alsa mixer.. the one wit audigy 2 it has alot more tracks plus it has a bunch of them that are called emu10k1 pcm then a numbe counting up intil it hits 32 than more that are emu10k pcm send then a number counting up to 32 then a bunch emu10k pcm send routing then a number counting up to 32..??
whats that all about

next thing.. while i was searching how to solve sound some stuff about digital analog jacks came up.. so i switched my speakers to the tha jack and now i have sound but its really fuzzy.. like to the point that it drowns out most sounds..

the instructions that i found sed to open volume control and go into edit and enter into prefs... brings me into volume control preffs with little check boxes to select so they will be visable in volume control...

they sed to find the one called audigy analog/digital output jack and make that show so you can then mut it.. then apperently according to them your regular jack will be working just fine..(so i geuss they were saying there is interference from the sound output to the anlog/dig jack..

so when i check the box so that this track will be visable .. instead of that happening the windows crash.. alsa doesnt alsa stays running but the prefs window and the volume control window just disappear.. and when i open the volume control window again the digital/analog jack track is not added. so i go into prefs again and look for it and it is checked as though it were added but its not there.????
whats that all about..

i tried going into the volume control in console but that doesnt have any digi/analog jack toggle iether..

anyone able to help.. 
could it be conflicting hardware
something more in depth or something just plain stupid that im doing..

thanx for your time in advance..
all input is very appriciated \\:D/

---

### Post by Boggles3 on 2005-07-15
ya finally got my sound working.. im so happy.... it was the analog thing..

thanx guys even though nobody posted i did notice people looking so thanx for at least stopin in and checkin on me  \\:D/

---

### Post by Boggles3 on 2005-07-15
oh guys.. lol just to make sure i restarted and ya .. there was no sound again.. i fiddled with the analog stuff but thats not it..

i dloaded the drivers when i installed the alsa- lib,utils,driverand oss but i put them in a randome file on my desktop that i named alsa....
lol i think thats why my sound doesnt work.. i think they are sapposed to be in /usr/src/alsa  file... but i cant move them over because i dont have permision.. to write to that file..

how do i give myself permision.. i know its through console but i dont remember the commands..

or even better is there a way from root console that i can just grab a file from one folder and put it to another... like a move command or something????

cuz then i dont need permision right because ill me in as root...

anyone able to help.. i was so close .. lol ](*,)

---

