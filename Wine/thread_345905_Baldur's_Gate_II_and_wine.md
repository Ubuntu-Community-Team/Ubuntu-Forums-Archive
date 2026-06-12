---
title: "Baldur's Gate II and wine"
date: 2007-01-24
forum: Wine
---

### Post by sloggerkhan on 2007-01-24
I have installed Baldur's gate II with wine.

In order to set up game options successfully, I run:

$sudo wine /home/****/.wine/drive_c/Program\ Files/Black\ Isle/BGII\ -\ SoA/BGConfig.exe 

which works. 

Note that all directories must have user write permissions or saving games won't work.

---

### Post by sloggerkhan on 2007-01-24
solved

---

### Post by RomeReactor on 2007-01-25
Try locating the folder in which you have Baldur's Gate installed (like "/home/user/.wine/drive_c/Program Files/baldursgate") on the terminal. For example:

```
cd /home/user/.wine/drive_c/Program Files/baldursgate
```

and then try:

```
sudo chmod 777 -R
```

to change permissions. Try launching the game **without** sudo then and see if you can change and save settings then.

---

### Post by sloggerkhan on 2007-01-25
Thanks, that seemed to work. Runs now, though sound is a little glitchy.
:)

---

### Post by astrocreep on 2008-01-18
when i try to start the game, it just freezes up. im using ubuntu w/ virtual box for mac. any suggestions?

---

### Post by sloggerkhan on 2008-01-18
I think that's very different from running with wine. For example, a mac copy is probably for powerpc mac, I'd guess.

---

### Post by astrocreep on 2008-01-20
i think you misunderstood me. im trying to run BG2 through wine, but im running wine though ubuntu, which is being run through virtual box on a  macbook.

---

### Post by Ferrat on 2008-01-20
> **astrocreep said:**
> i think you misunderstood me. im trying to run BG2 through wine, but im running wine though ubuntu, which is being run through virtual box on a  macbook.

Not sure but it could be a problem with the fact that virtual boxes doesn't give you grafic acc. support, specially not as well as the real thing and I belive that BG2 uses opengl for somethings

---

### Post by astrocreep on 2008-01-20
on startup? i dont even get through the opening videos. in fact, i dont even start them.

---

### Post by RevNomad on 2008-05-09
Slightly different issue, my son's have been unable to convince Baldur's Gate to run under Wine. We are using the latest Ubuntu and Wine releases. 

Is someone able to guide us through successfully installing and operating?:confused:

---

### Post by phoenix81000 on 2009-04-22
RevNomad

I installed Baldurs Gate II from iso images, which went fine. Installed a NOCD patch. Game works perfect.. i even did a wide screen support mod. Online should work but getting a game with a mate of mine through TCP/IP can be a real hassle.

I can help you in more detail, odds are iam not going to look at this thread again. If you need me make a post @ [www.orangeswarm.com](www.orangeswarm.com) 

H.



UPDATE 23/4/09!
I finally got the multiplayer working. I installed additional DLL files for DirectPlay and added some stuff to the registry as discusted in the WineHQ page for DirectPlay. What made it work in the end was the VPN client Hamachi :D

---

### Post by jokei on 2010-03-23
This seemed like the right place to put this.

I'm running Xubuntu (latest version), successfully installed and run Baldur's Gate and TOTSC - but am having trouble running SOA.

Do I need to install the patch?

I'm running the dvd/4-in-1 pack.

---

### Post by Toffeeapple on 2010-03-23
What sort of trouble would you be having?

---

### Post by jokei on 2010-03-23
Ok, what I am doing is mounting the cd/dvd BG2:SOA...  Then right click on Baldur.exe and open with Wine.

There is no Autorun.exe - only an Autorun.ini or .inf

The load screen comes up play/settings/configure etc

The configuration seems to be ok, did this on the install and the graphics - 3 different coloured squares thing is all ok.

Laptop freezes, my desktop background enlarges, as do the icons, then nothing, I can switch between sessions using alt-tab, but it wont actually execute any of these commands and have to power it off.

:(

Sarevok is dead, but I need to defeat more Bhalspawn.

---

### Post by Toffeeapple on 2010-03-23
HI,

If you installed it wasn't an icon to launch it put in the wine menu somewhere, or on your desktop even?

Either way this command should start Baldurs gate, providing it's been installed in the default location on a default installation of wine..

```
wine "/home/YOUR USER NAME/.wine/drive_c/Program Files/Black Isle/BGII - SoA/BGMain.exe"
```

Do that in a terminal and see if it says anything.

Did you set the resolution to one that your laptop can do during install?

Unselected the 3d acceleration bit and the opengl bit in the config program, see if that makes a difference. Set it to 800x600 as that's what BG1 (seeing as it works for you) uses if I remember correctly.

Install the patch anyway, can't make it worse can it.

---

### Post by jokei on 2010-03-24
Hey, thanks for the reply.

There was no icon installed on the desktop, nor is there one under the XFCE drop-down menu.

3d acceleration is unselected.

I tried the command you gave, which yielded this:

wine: cannot find '/home/benjohnson/.wine/drive_c/Program Files/Black Isle/BGII - SoA/BGMain.exe'

I've just installed the patch - will try that first and see if it works, will update this if it works/crashes my laptop.

Fingers crossed.

Ok - that crashed it.  :(

---

### Post by Toffeeapple on 2010-03-24
> **jokei said:**
> wine: cannot find '/home/benjohnson/.wine/drive_c/Program Files/Black Isle/BGII - SoA/BGMain.exe'

That means that isn't where BGMain.exe is, or something is miss spelt or wrong case.

Sorry can't think of anything else as it works perfectly OK here for me.

---

### Post by ZarathustraDK on 2010-03-24
I had problems running BGII too. Seems like wine screws up with all the spaces in the path or something.

In the end I installed BG1, TotSC, BG2 and ToB with Easututu. It has some nice benefits. Made a Howto for it here [http://ubuntuforums.org/showthread.php?t=1437195](http://ubuntuforums.org/showthread.php?t=1437195)

---

