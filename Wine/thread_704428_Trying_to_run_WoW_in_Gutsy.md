---
title: "Trying to run WoW in Gutsy"
date: 2008-02-22
forum: Wine
---

### Post by JackOfAllGames on 2008-02-22
Hey there! I'm a recent Ubuntu fan that's trying to get World of Warcraft set up under Gutsy. I'm not a COMPLETE Ubuntu noob, but I'm far from an expert. I'm getting comfortable with the terminal, but I still have to look up commands from time to time. =P

Anyway, I've been trying to get WoW to run with Wine. I know many people have had success with this, but I've just had one problem after another. Most recently, I have the game pretty close to running. The problem, part of the game's graphics won't load.

Looking at the login screen, the flames and glowing effects work great! They're at least as good as Windows. The problem, I can't see the gate itself. None of the background is there. I can log into the game, select a character, and then even play the game. The problem is the same there though. I can see buildings, the ground, names of players, and effects like fire or glowing weapon enchantments. I just can't see players, NPCs, enemies, or the misc. items that decorate the game.

I've looked around and have never heard of this before. Anyone know what might cause a problem like this? I thought, maybe I did something wrong in the instructions I followed. Maybe I messed up in the config.wtf file. I tried completely erasing the config file, having WoW make a new one, and editing the new one. Still no luck.

If anyone has ideas on how to fix this graphical problem, I'd really appreciate it. For now, I'm stumped.

Finally, since I'm sure it'll be asked, I have an ATI Radeon X600 graphics card (with 2.5GB ram and two 2.8Ghz processors - more than enough to run the game) and I have the ATI drivers installed. For whatever reason, the open-source drivers are no longer giving me the ability to do 3D (I probably messed something up in the configuration - I know it *used* to work).

---

### Post by nosto on 2008-02-29
The first thing you'll want to do is check out this forum post 
[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

The next thing to do is google the wow linux wiki and look into the settings for config.wtf, this will help you greatly.

Another suggested fix is a registry fix (found in that post) and also when running the command to open wow make sure you have -opengl at the end (either in terminal or the 'shortcut').

Cheers!

---

