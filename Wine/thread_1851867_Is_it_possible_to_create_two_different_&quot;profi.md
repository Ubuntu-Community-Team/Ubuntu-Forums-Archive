---
title: "Is it possible to create two different &quot;profiles&quot; for two different games?"
date: 2011-09-29
forum: Wine
---

### Post by Melhisedek on 2011-09-29
I have two games that I play a lot:
Guild Wars and Civ V

GW needs Use GLSL disabled and Civ V needs it enabled. And I'm tired of switching. So is it possible to have a "profile" or "ini file" that will disable GLSL when I start Guild Wars and enable it when I start Civ?

Thank you for your time!

---

### Post by ergo-proxy on 2011-09-29
Create WINEPREFIX for each of your games export WINREPREFIX=/path/where/you/want/to/store/your/wine/prefixes/
Type, winecfg and you're done (just make  sure you have correct winreprefix exported when you launch you game through the terminal)
 
example:
 
export WINEPREFIX=$HOME/.wine-wow/
winecfg
cd $WINECONFIG/drivec/Program File/Yourgame/
wine start.exe

---

### Post by IPEX-731BA5DD06 on 2011-09-30
A non command line way is;

1) Open up configure wine, should be on desktop, or just find.
2) Click on the game you want, not the default options, but the actual game in question.
3) Click on the libraries tab for the game.
4) Now you enable or disable the various options as you need.
5) Save your new configurations and they should run, when you start the game.

Wine configuration is a powerful tool, using a graphical interface for ease of use, and simplicity in understanding. :lolflag:

Sorry but command lines just confuse me, I use linux exclusively, but prefer GUI commands. :confused:

---

