---
title: "WoW problem"
date: 2008-02-02
forum: Wine
---

### Post by simmba on 2008-02-02
My problem is after i login and select my character and then i hit "Enter world" The little blue bar gets all the way to the right and then it stops... and my fan kicks on high and my cpu gets maxed out. I have to restart x and then force kill WoW.exe to get it to stop. anyone have any suggestions? I have done the reg OpenGL fix. I have tried to run it under Metacity instead of Compiz. and i have tried it with wine windowed and full screen, help please :(

---

### Post by Sammi on 2008-02-02
Please post some info about your computer. CPU, RAM, and graphics card make and model.

And your graphics card driver version, as well as the version of Wine you are using.

---

### Post by simmba on 2008-02-05
Well i haven't had to post specs of my pc before so ill try it out just let me know if i miss something

Pentium[R] 4 CPU 3.60GHz
3.59GHz, 2.00 GB of RAM
NVIDIA GeForce 7600 GS

not too sure about the driver version of the Graphix card, as i am on windows atm. and wine was the most up to date at the time of the post (not sure if they updated again)

---

### Post by Sammi on 2008-02-05
It may be the Nvidia graphics card driver that's the problem, as the ones shipped with Gutsy Gibbon 7.10 and Feisty Fawn 7.04 are both already relatively old, and both WoW and Wine have been updated several times since Gutsy/Feisty were released - new stuff might only work in the newest Nvidia driver. Oh and if you are using anything older than Feisty 7.04, then things might be even more complicated.

You should try updating to the newest graphics card driver. Envy is the easiest way to do this: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

But keep in mind that Envy is a third party application. There is no official guaranteed and stable way to update the Nvidia driver. Ubuntu only officially supports the one in the repositories (the one you can find if you search for "nvidia" in Synaptic). Worst case scenario you might get stuck in the Ubuntu command line, unable to boot Ubuntu's graphical user interface, but Envy can also run from the command line, and in my experience it has been good at recovering from these incidents. Just use the Envy command line tool to uninstall and reinstall the Nvidia driver. Works like a charm every time for me :D

---

