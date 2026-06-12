---
title: "Running EVE Online"
date: 2008-01-09
forum: Wine
---

### Post by Glitch10240 on 2008-01-09
Hey Guys, 
I'm new to linux, about 2 days now :D have ubuntu on the pc and laptop, basically i wanna get eve running on the pc, i have or i think i have installed the nvidia drivers (through Applications>Add/Remove>Nvidia in search>Nvidia 'new' drivers). but when i test my system with the "system tests" tool supplied with eve, i get "failed" on both OpenGL and 3D Acceleration. Anyone be able to give me a fix for this, or how to get them installed. Eve on linux runs on Cedega if that helps.

My system info:
Q6600
2Gb ram
8600GTS

Running Ubuntu 32bit (dual boot with Vista 64bit)

any help appreciated :)

---

### Post by K.Mandla on 2008-01-09
Moved to Gaming and Leisure.

---

### Post by buntunub on 2008-01-10
Im really lost as to WHY you messed with the NVIDIA drivers?? Ubuntu automatically installs them for you upon first boot when you enable them with the Restricted Driver Manager. That driver works wonderfully with the Linux Client that CCP provides. No tweaking/fixing required at all. Download, run install, done!

---

### Post by CovexEnVec on 2008-01-10
I have the same errors except that I have a ati card.

I also have the asla sound one too.

---

### Post by buntunub on 2008-01-10
:confused:

This just gets better and better! Its like that one time, at band camp.. Someone said something and I got mad!

1. For the OP, your best bet is to enable video driver via Restricted Driver Manager. Although because you screwed with the driver, that may not work without first uninstalling whatever it is you installed. Worse comes to worse, you can always get Envy and do it that way (you get the most recent drivers too).

2. $glxinfo | grep direct

You should see something about Direct Rendering being enabled. If not, you wont be able to play any 3D games.

3. Assuming #1 and #2 are done and all is well, go to CCP's official website and download the Linux Client.

4. Click on Install file and launch installer

5. Run through Installer and finish it. It will download a very large patch and the cedega wrapper.

6. Launch EVE via Applications > Games menu

7. Enjoy playing EVE online.

---

