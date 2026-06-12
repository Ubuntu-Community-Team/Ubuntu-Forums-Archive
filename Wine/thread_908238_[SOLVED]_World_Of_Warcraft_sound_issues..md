---
title: "[SOLVED] World Of Warcraft sound issues."
date: 2008-09-02
forum: Wine
---

### Post by Indigolynx on 2008-09-02
I have already read a guide on how to get sound working on WoW on this forum, *however* it didn't work did it?

So here is my problem: I go on WoW and no sound comes out my speakers. Occasionaly it goes on and off. This is just more annoying cos I finally think I've fixed it and then it goes off.  

When I enter (in terminal) 

    sudo asoundconf list

It comes up with "Names of available soundcards: ICH6" -- just in case this info is relevant. 

I go on System, Preferences, Sound and it is set to 

**Sound events:**
Sound playback: Autodetect

**Music and movies:**
Sound playback: Autodetect

**Audio conferencing:**(this is the part I did a bit of tweaking to see if it did anything)
Sound playback: Intel ICH6
Sound capture: Intel ICH6 - MIC ADC

**Default Mixer Tracks:**
Device: Conexant id 30 (OSS Mixer)


Right so when I go on terminal-> *winecfg* I go on Audio tab and the ALSA box is checked. I dont know if this is correct or not. I have tried OSS but not with not much success.  

Does anyone know what things I should change and set please because no sound in WoW is really unnatural for me


Thanks!

---

### Post by BenAshton24 on 2008-09-06
I think that I have a simple solution that should fix your problem :D
1) type the following command in terminal:
> sudo apt-get install alsa-oss
2) Open GEdit (text editor) and type the following:
> export user=`eval whoami`
cd /home/$user/.wine/drive_c/Program\ Files/World\ of\ Warcraft
aoss wine Wow.exe
3) Save this in your home directory as wow.sh
4) Navigate to your home directory using nautilus or your favorite file manager.
5) Right click on wow.sh and click on properties, go to the permissions tab and check the "allow executing file as program" box.
6) Change your links on your Applications menu to link to wow.sh instead of wow.exe
7) Launch wow and the problem should be solved

Hope this helps :D

---

### Post by viralpolymorph on 2008-10-18
Ummm. I'm really new to Linux so this may be a silly question but I dont understand #6,

6) Change your links on your Applications menu to link to wow.sh instead of wow.exe ?

Thats the only part I'm stuck on.

---

### Post by Zagoofeek on 2008-11-22
Talking  Re: World Of Warcraft sound issues.
I think that I have a simple solution that should fix your problem
1) type the following command in terminal:
Quote:
sudo apt-get install alsa-oss
2) Open GEdit (text editor) and type the following:
Quote:
export user=`eval whoami`
cd /home/$user/.wine/drive_c/Program\ Files/World\ of\ Warcraft
aoss wine Wow.exe
3) Save this in your home directory as wow.sh
4) Navigate to your home directory using nautilus or your favorite file manager.
5) Right click on wow.sh and click on properties, go to the permissions tab and check the "allow executing file as program" box.
6) Change your links on your Applications menu to link to wow.sh instead of wow.exe
7) Launch wow and the problem should be solved

Hope this helps
__________________
Registered Linux User #476478 Register At [www.counter.li.org](www.counter.li.org)
Windows Vista, a 32 bit extensions and a graphical shell for a 16 bit patch to an 8 bit operating system by a 2 bit company that can't stand 1 bit of competition. 



[SIZE="5"]
How do you do #6? I'm a noob. :lolflag:[/SIZE]

---

