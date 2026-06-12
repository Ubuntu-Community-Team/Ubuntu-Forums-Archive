---
title: "IE4Linux, WINE 0.9.53, Ubuntu x64 - No tile bar or address bar"
date: 2008-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by pm124493 on 2008-01-17
I am not sure this belongs in this forum or the Wine forum or the 3rd party apps so forgive me if I posted to the wrong forum.
I installed IE4Linux using the installer provide in these forums. It installed okay with no errors. However when launched there are only a few buttons, no FILE, EDIT or any words in the top bar and no address bar. Makes it very difficult to use. It seems to run fine though the buttons are small and the text is not very good.

Has anyone run across this problem? I have read where this is working for many people.
Also I have a INTEL DUO Core 2 E6300 with 2GB PC6400 memory and an Nvidia GeoForce 7900 GS KO card. I am running Compiz Fusion. When running IE6 (IE4LINUX) it consumes 60-90% of both processors and will not shutdown cleanly.

Thank You:confused:

---

### Post by Kilz on 2008-01-17
> **pm124493 said:**
> I am not sure this belongs in this forum or the Wine forum or the 3rd party apps so forgive me if I posted to the wrong forum.
I installed IE4Linux using the installer provide in these forums. It installed okay with no errors. However when launched there are only a few buttons, no FILE, EDIT or any words in the top bar and no address bar. Makes it very difficult to use. It seems to run fine though the buttons are small and the text is not very good.

Has anyone run across this problem? I have read where this is working for many people.
Also I have a INTEL DUO Core 2 E6300 with 2GB PC6400 memory and an Nvidia GeoForce 7900 GS KO card.** I am running Compiz Fusion**. When running IE6 (IE4LINUX) it consumes 60-90% of both processors and will not shutdown cleanly.

Thank You:confused:

Please disable desktop effects and see if the problem remains.

---

### Post by kyleabaker on 2008-01-20
I'm having the same problem. I'm running Ubuntu 8.04 x64, latest Wine and IEs4linux 2.99.0. I can't use them because they are missing buttons, etc. The elements are there, they just aren't visible. I originally had desktop effects turned off, then I disabled them all and am still having the same problem.

Here is a screenshot..
[http://img222.imageshack.us/img222/1797/screenshotcongratulatiowv8.png](http://img222.imageshack.us/img222/1797/screenshotcongratulatiowv8.png)

EDIT:
I came across this thread talking about Wine being the problem, but surely there is a fix for it now!?
[http://ubuntuforums.org/showthread.php?t=502831](http://ubuntuforums.org/showthread.php?t=502831)

---

### Post by teslarage on 2008-01-21
same issue here. but im on ubuntu 32-bit. wine 0.9.53.

---

### Post by kyleabaker on 2008-01-22
@teslarage
It must be that Wine broke something with IEs4Linux when updating Wine. I'm also using Wine 0.9.53, but for x64. I don't think x64 vs. x86 would have anything to do with it. It could sometimes, but for the most part..it won't.

Apparently Wine broke IEs4Linux somewhere around Wine 0.9.41 and haven't fixed it since.

---

### Post by jjalocha on 2008-01-22
See solutions in this thread, around post 16:

[http://ubuntuforums.org/showthread.php?t=665786&page=2](http://ubuntuforums.org/showthread.php?t=665786&page=2)

---

### Post by kyleabaker on 2008-01-22
@jjalocha
Thanks. Thank fixed IE7 here, didn't fix the others for me though.

Here are the tips from the link posted by jjalocha:
> **joeycbulk said:**
> Interface does not show clearly because of the theme used. To fix this you need to use the defaults.

```

cd ~/.ies4linux/ie6
cp user.reg ~/user.reg.old
gedit user.reg

```

In the text editor, delete [Control Panel\\Colors] and the entries under it.

```

This is the part that I deleted. I'm not sure if every one has the same.

[Control Panel\\Colors] 1200623437
"ActiveBorder"="228 228 228"
"ActiveTitle"=hex(1):
"AppWorkSpace"=hex(1):
"Background"="0 0 0"
"ButtonAlternateFace"=hex(1):
"ButtonDkShadow"=hex(1):
"ButtonFace"="228 228 228"
"ButtonHilight"=hex(1):
"ButtonLight"="228 228 228"
"ButtonShadow"=hex(1):
"ButtonText"=hex(1):
"GradientActiveTitle"=hex(1):
"GradientInactiveTitle"=hex(1):
"GrayText"=hex(1):
"Hilight"=hex(1):
"HilightText"=hex(1):
"HotTrackingColor"=hex(1):
"InactiveBorder"="228 228 228"
"InactiveTitle"=hex(1):
"InactiveTitleText"=hex(1):
"InfoText"=hex(1):
"InfoWindow"=hex(1):
"Menu"="228 228 228"
"MenuBar"=hex(1):
"MenuHilight"=hex(1):
"MenuText"=hex(1):
"Scrollbar"=hex(1):
"TitleText"=hex(1):
"Window"=hex(1):
"WindowFrame"=hex(1):
"WindowText"=hex(1):
```

Make sure to stop deleting before the next group.
```

Example: Stop deleting line before the ff.
[Control Panel\\Desktop] 1200623418
[Control Panel\\Desktop\\WindowMetrics] 1200623418
[Control Panel\\International] 1200623413

```

---

### Post by jonathanmotes on 2008-01-25
I'm having the same problem. I tried this:

> 
Code:

cd ~/ies4linux/ie6
cp user.reg ~/user.reg.old
gedit user.reg


But, after running the first line I'm getting```
bash: cd: /home/jmotes1/ies4linux/ie6: No such file or directory
``` 

I can't seem to locate where ies4linux is installed (it is installed - I'm currently running it!).

Please help!

UPDATE: I decided to install the deb and now I found the install at "/usr/share/ies4linux" but I'm having problems with it: the place where the buttons and URL bar should go is not there. All I see is the webpage. I can't even hit CTRL-L to go to a different URL. Anyone else have this problem?

UPDATE2: Thanks heatpumpcontrol for your help! I solved my above issue by removing both versions that I had installed (the deb and the one from tatanka.com) and reinstalling the deb version. On the reinstall, the location for the user.reg file changed to```
~/.ies4linux/0/ie6
```I thought that would be worth mentioning for others that might have the same issue.

---

### Post by heatpumpcontrol on 2008-01-25
> **jonathanmotes said:**
> I'm having the same problem. I tried this:


But, after running the first line I'm getting```
bash: cd: /home/jmotes1/ies4linux/ie6: No such file or directory
``` 

I can't seem to locate where ies4linux is installed (it is installed - I'm currently running it!).

Please help!

UPDATE: I decided to install the deb and now I found the install at "/usr/share/ies4linux" but I'm having problems with it: the place where the buttons and URL bar should go is not there. All I see is the webpage. I can't even hit CTRL-L to go to a different URL. Anyone else have this problem?

```
cd: /home/jmotes1/.ies4linux/ie6
``` 

the instructions are missing the "." (dot) before ies4linux/ie6 as is it a hidden directory

---

### Post by heatpumpcontrol on 2008-01-25
Worked great... thank you guys

---

