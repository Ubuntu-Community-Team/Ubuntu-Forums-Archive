---
title: "My new Ubuntu build"
date: 2006-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by j0eb0b on 2006-09-08
I just fired up a new system with the following specs:
Ubuntu 6.06 OS
DFI Lanparty nF4 Ultra MB
AMD FX 55 CPU
2x512 twinMOS Speed Premium DR400 memory
WD 320G SATA HD
Liteon DVD/CD reader writer
Antec Tru-power 550 PS
Logitech z 640 5.1 speakers

I loaded the 64 bit version of Ubuntu and it runs but produces no sound.  i am using the onboard sound connections on the MB  To make sure it wasn't a 64 bit problem, I created a new partition and loaded 32 bit Ubuntu and installed and ran Automatix.  Still no sound of any type.

Question is this.  I can't run the DFI chipset install CD because it is written for Windows.  Is my problem that i have no sound driver loaded?  If yes, how and where can I find a driver that is nF4 compatible?  If I load a new driver after the fact a(after I have loaded Ubuntu) am I likely to break the kernal?

Thanks,
Joe

---

### Post by kuja on 2006-09-08
Open a terminal.
```
lsmod | grep snd
```

Post the output here... this'll let us know if the drivers are being loaded or not.

---

### Post by jamesford on 2006-09-08
it works on my dfi mboard, but iirc its disabled in bios by default.

---

### Post by j0eb0b on 2006-09-08
it works on my dfi mboard, but iirc its disabled in bios by default.

The new 64 machine is offline and the old  DFI nF2 unit is what I am using now (and works great).  Not sure what you told me, quoted above.  What irc is disabled by default?

Thanks, 
Joe

---

### Post by a-musing amazon on 2006-09-09
Don't have a DFI motherboard, but on mine (AsRock 939S56-M) there is an option in the bios to enable or disable onboard sound. The suggestion is to check that it is enabled (and if it isn't to enable it) otherwise you would not get any sound using the onboard chipset.

Otherwise you /can/ get problems with new motherboards if they also use new chipsets, since the kernel driver may not recognize the chipset (essentially it doesn't have a driver for it yet).

Initially I had this problem on my motherboard. Usually linux are pretty quick at creating kernel drivers (so I have no problems with Dapper, but would have had with Breezy).

---

### Post by j0eb0b on 2006-09-09
Here are teh drivers loaded to my MB.  I don't know wht I should be seeing here.

j0eb0b@j0eb0b-desktop:~$ lsmod | grep snd
snd_intel8x0           33692  1
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
j0eb0b@j0eb0b-desktop:~$

---

### Post by j0eb0b on 2006-09-09
Can you read the $lsmod output and tell me what you think?

Thanks,
Joe

---

### Post by kuja on 2006-09-09
Well, it's loading the sound drivers (snd_intel8x0), so the problem lies elsewhere. Double-check that the sound isn't muted in the software mixer (this used to be a really common problem).

---

### Post by j0eb0b on 2006-09-10
Where should I look to make sure soundmixer is not muted?  I see nothing I can change in the application>sound panel panel or System>preferences>sound.

Thanks,
Joe

---

### Post by j0eb0b on 2006-09-11
i found alsamixer and in fact, most of the options were grayed out.  Enabling these has changed nothing and there is still not a whisper of sound out of this machine.  I still bellieve it is a sound driver problem in spite of the fact that Intel 8x0 is reported to load. 

Question:  Sound card is detected as an nVidia 804 but the only option in the bios is AC.  Is this a problem?

I went on Alsa source to try and find and install a proper driver but nothing listed comes close.  What do nF4 users us with onboard sound?

Is it time to bag it and get an external card?  If yes, what works without a vast investment in OJT?

Thanks,
Joe

(PS Yes, I worked through the Sound sticky in the 64 forum)

---

### Post by kuja on 2006-09-11
It should use the Intel8x0 driver. I have a comparable nforce4 motherboard myself. Alsamixer was more or less where I was hoping you would look. Make sure the AC'97 audio or whatnot IS enabled in your bios... disabling it would disable your sound for certain.

---

### Post by j0eb0b on 2006-09-12
I'm going to keep plugging away since i don't want to take the path of least resistance and fall back to XP.

thanks for your help.  I'll post the fix once I figure it out.

---

### Post by kuja on 2006-09-12
Well, I can think of one other thing that might be worth checking. Veryify that your user is a member of the "audio" group.

To do so pull up a terminal and type "groups". It'll print a list of all the groups your user is a member of. If you're not a member of the audio group, do this: "adduser yourusername audio". Then log out, and log back in.

---

### Post by j0eb0b on 2006-09-13
I fixed all of my problems by buying XP Pro, installing it and loading the various drivers on the DFI CD. Now I have a functional machine albeit slower and less responsive in many ways than the Ubuntu system.  I haven't given up on Ubuntu/Linux but as Clint Eastwood said in "Dirty Harry Magnum Force" "a man's gotta understand his own limitations". How can I help or what should i do with this experience to foster Ubuntu?

Joe

---

### Post by kuja on 2006-09-13
Well, I'm sorry to hear that you went that far. It probably would have been cheaper to get a cheap sound card known to work and used it instead :P

---

