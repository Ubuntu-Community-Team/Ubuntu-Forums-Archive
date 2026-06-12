---
title: "Warcraft 3 Registry editing in Wine"
date: 2008-04-25
forum: Wine
---

### Post by superbleeder12 on 2008-04-25
Does anyone know how to change registry settings in Warcraft 3 TFT so I can get 1680x1050 Resolution.

I am able to run the program in Windows in the resolution no problem (had to change registry entries)

I'm supposed to change the key at

HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III\Video

but that key isn't in the Wine Registry.

any known workarounds?

---

### Post by Toffeeapple on 2008-04-25
have you installed Warcraft III in the default wine folder or in it's own?

if you installed it in the default wine location i.e. your home folder/.wine/drive_c/Program Files/Warcraft III

if thats the case then just running 'wine regedit' in a terminal should bring up registry editor and then if the entry isn't there then just put it there, having said that though I think it should be there.

if you have installed it with it's own prefix then..

WINEPREFIX="$HOME/where ever you have installed the game" wine regedit

the above in a terminal window should bring up regedit for that particular wineprefix location.

at least I think so... But! get [PlayOnLinux]("http://www.playonlinux.com/en/") and all your wine problems will be a thing of the past : )

---

### Post by cogadh on 2008-04-25
You don't need to run "wine regedit", just typing "regedit" in a terminal launches the registry editor (it already associated with Wine by default).

How can getting PlayOnLinux make your Wine problems a thing of the past, when PlayOnLinux is just a front end for installing certain games with Wine? :-k

---

### Post by Toffeeapple on 2008-04-25
picky picky Mr cogadh : )

PlayOnLinux! it enables those of us who are not expert linux gurus to install windows software, games for example but ultimately anything and assign them their own wine versions if necessary, so you can have various setups for various games with out hassle and all easily accessible. It does away with the pain of setting everything just right for one game and then having it all fall apart when wine gets updated in some way that breaks something, or you tweak something to get another game working nicely, for example.

It lets you have different registry tweaks for different games while using different versions of wine while having independent setups within each instance of wine. Its very handy.

; )

---

### Post by superbleeder12 on 2008-04-25
Could I just export the registry in my Windows build to the Wine registry... or would it get lost in translation?

Alright, so I'm a general Ubuntu n00b. Any quick guides on how to install PlayOnLinux? I went to the site and put in the commands that they tell you to put the program in the application library but I think it error-ed out. 

One problem with running Warcraft 3 in 1680x1050 is that it stretches it out because the game doesn't support widescreen. :( but I've gotten used to running the game in widescreen in my windows partition.

Thanks a bunch.

---

### Post by cogadh on 2008-04-25
Taking your Windows registry and trying to import it into the Wine registry is really, *really* bad idea. You're better off just writing down what you need from the Windows registry and manually creating just those specific entries in Wine.

I'll leave the PlayOnLinux question for Toffeeapple, he's (?) more experienced with it than I.

EDIT - I take that back, I just tried following the instructions [here](http://www.playonlinux.com/en/download.html) and found that the steps are simple, but flawed. First you need to add the PlayOnLinux repository to your system:
```
sudo wget http://playonlinux.botux.net/playonlinux_hardy.list -O /etc/apt/sources.list.d/playonlinux.list
```
Then you should be able to get the PGP key for the repository, but I found the command they list doesn't work:
```
wget -q http://playonlinux.botux.net/pol.gpg -O- | sudo apt-key add -
```
I'm not really sure whats wrong with it. From a syntax standpoint, it appears to be correct, there just doesn't seem to actually be a PGP key to get. It doesn't really matter, after you run the install commands, you will be prompted to install the package anyway, even though it can't be authenticated. To install, just run these two separate commands:
```
sudo apt-get update
sudo apt-get install playonlinux
```
That's it, it should be installed.

EDIT2 - Of course now that I have it installed, PlayOnLinux insists that I don't have video hardware acceleration installed or enabled, which I do... I really wasn't looking for a new personal project today...

---

