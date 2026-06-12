---
title: "Frozen throne wine/cedega help with install/optimization"
date: 2007-02-02
forum: Wine
---

### Post by thegrimgod on 2007-02-02
Hi , i am very new to linux , using ubuntu edgy, im a big w3 frozen throne gamer , and i need to install the game in ubuntu.
I already tried cedega ,but i am dissapointed with the lag...not internet lag...i have a GeForce fx 5200 128 mb of video memory , installed nvidia drivers (but i might have not optimized my xorg.conf from lack of knowledge) , amd 650 MHz and 385768 kB RAM
I need help with installing wine(again mainly i have no clue what im doing) , or help with configuring cedega (i dont know any tricks , i just install)
In any case i read forums dealing with this wine/cedega issue ,  and i will be gratefull for any help(again when u explain i just installed linux , not 3 days ago)
BTW: played this game under windows(==devil) , had no problems , and i would like to go on and play this game under this very nice os

---

### Post by pay on 2007-02-02
Try ```
cedega war3.exe -opengl
```

---

### Post by thegrimgod on 2007-02-02
ty dude , it defenitly works much better, am i missing a configuration , because when i start it from the gui of cedega it doesnt work as good, in any case i still need some more sugestions ,its still not up to the performance im used too , much better than bf tho

---

### Post by thegrimgod on 2007-02-03
Ok ,so wine is much better than cedega from what i have tested
This is basicly what i did : 
1.added to synaptic repos 
[http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
downloaded wine using synaptic -- i have version wine-0.9.30, changed in winecfg to windows xp
Now i tried to install warcraft using wine , and yes it installed , it patched and everything , but again , im new , i have no clue , where wine installed , or warcraft for that matter , i cant find the "windows" locations , and as such , when i run what i installed in wine , i presume it uses the directx  , i dont know how to make it use opengl other than added as a argument, and i cant use terminal cause i dont know path , so what i did is used the cedega installation of warcraft , which is in my home folder , in my user, and on terminal went "wine pathtofrozenthrone -opengl". went much much better than cedega , played online ladder solo , 3v3 , custom dota , everything worked...i still had some lag on dota , but i basiclly did no config
Hope it helps , so u dont waste ur money , and if someone knows where wine installs and where warcraft installs in wine ,let me know , also if u have a very nice config , i can use the tips :)

---

### Post by pay on 2007-02-04
Wine defaults to /home/<user>/.wine/drive_c/Program\ Files/ 
To change warcraft to opengl without the -opengl option, you need to edit the registry```
regedit
``````
[HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III]
"Gfx OpenGL"=dword:00000001
```

---

### Post by Nikola_ on 2007-02-07
have done all with wine, and works just fine

now i have problem connecting to Bnet, when it starts "Downloading Files" pops up window and says:

"There was an error writing to your hard drive
while trying to download file form BattleNet.
There might not be engouh free space left.
Please check your hard drive and try again."

so, thats what i get, and dont know what to do now



anyone have some ideas?

tnx

---

### Post by Jengu on 2007-02-07
Do you have enough free space? Is your warcraft3 folder _not_ read only?

---

### Post by Nikola_ on 2007-02-07
well i have 2.7 GB free disk space on that drive

and no, its not read only
it still says same thing

dunno what to do...


TFT is added to my .wine folder:   /home/user/.wine/drive_c/Program Files/Warcraft III

every thing works just fine, but that download

where is TFT trying to dl that file?

---

### Post by Nikola_ on 2007-02-07
ok, i managed to get my Dota going on Bnet
it was, in fact, that the directory was not accesible by Bnet. dunno how that happend... 
so i passed that, and now playing Dota, but i have lag during the play, and its quite anoying
its not my net lag, but wine, i can see that


got some tricks?
or cedega is better?

what should i try to do?  



tnx

---

### Post by thegrimgod on 2007-02-24
i have no tricks for u, i get the same problem ,slow load for dota , lag at hero selection, never play a dm lol, but in general i just play 1v1 tft ladder, no customs, and its goin decent, also im experiencing one more problem ,if i try to acces web ladder , to see some statistics ,i cant get back in the game with my alt+tab, weird , and i cant close the game , have to log out , and back in...

---

### Post by thegrimgod on 2007-03-01
hm , new weird thing , every time i dl a custom map inside the game ,it cant find it , does anybody know where it saves the maps? , dl dota in game , and then i have to leave , to take it from getdota.com ...

---

### Post by thegrimgod on 2007-04-20
this is really weird... i just upgraded to 0.9.35 wine and now when i run my tft in normal -opengl mode , the screen is not centered , i can still see the top bar from my gnome dekstop and further more , when i try to go right / down inside the game , the acctual frozen trhone goes left/up , and i can see my desktop.....really need help,. my first solution was to open it in window mode.....but that aint no solution..

---

### Post by I_have_seen_the_light on 2007-12-04
i was able to download frozen throne using wine to my 2 comps but the other computer wasnt able to join the host, i mean they cant see each other, can somebody  help me with this pls? thank you so much

---

### Post by thegrimgod on 2007-12-05
Srry , dont have much xp in lan games, tho first thing would be to check if the pc's can see each other(which i guess they can, it usually works out of the box), and i heard about some wine warcraft issues with lan , you might want to check which version of wine you're using too, the new ones don't let me get onto bnet , but i believe 0.9.45 does let me, in any case good luck with that , if you find the solution feel free to post , ill try maybe later to do a connection see how it works with 0.9.50

---

