---
title: "Cannot install HoMM3 HD"
date: 2018-04-06
forum: Wine
---

### Post by dassadar on 2018-04-06
[COLOR=#333333][FONT=Roboto]Hello,[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]I have installed Heroes of Might and Magic 3 Complete using PlayOnLinux on my Mint environment, via GOG games.[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]However, game is quite unstable.[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]As the HD version fixes things, I tried to install it but this does not work. Here is how I am proceeding:[/FONT][/COLOR]
[LIST]
[*]From PlayOnLinux: select GOG.com - Heroes of Might and Magic 3 HD mod
[*]Then Launch from saved file "HoMM3 HD Latest.exe"
[*]Select the C:\GOG Games\HoMM3 Complete directory to apply on
[/LIST]
[COLOR=#333333][FONT=Roboto]Then I am getting the error that directory does not contain HoMM3?? (see here: [http://upload.playonlinux.com/5ac31b65635a4.png](http://upload.playonlinux.com/5ac31b65635a4.png) )

Same thing happens if I am installing directly with Wine.[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]Can you please help?[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]Thanks in advance, [/FONT][/COLOR][COLOR=#333333][FONT=Roboto]David[/FONT][/COLOR]

---

### Post by schtufbox on 2018-04-06
You could try to use innoextract to extract the files from the HoMM3 HD Latest.exe and copy them manually to the HoMM3 folder.

---

### Post by dassadar on 2018-04-07
Hello,
I managed to launch it finally.
However even though I am setting Full screen mode in the launcher, the HoMM3 window is a 800x600 frame within the full screen... any idea?
Options in the launcher are:
- 32-bit True (stretchable) GDI
- 1920x1080
- UltraSaI + Bilinear SharperX2

Thanks!
David

---

### Post by schtufbox on 2018-04-08
Can't help there I'm afraid.  I only thought about extracting the files and copying after googling the HD patch and seeing that it doesn't overwrite and just adds to it, so figured you could try just extract and copy :D
I don't own HoMM3 so can't test.

---

### Post by schtufbox on 2018-04-30
Also, this might be of interest...not Wine, but an opensource engine for HoMM3 [https://vcmi.eu/](https://vcmi.eu/)

---

### Post by Perfect Storm on 2018-06-07
Have you tried CrossOver [https://www.codeweavers.com/products/crossover-linux](https://www.codeweavers.com/products/crossover-linux) there's a free trial to test it out.

---

### Post by itroitz on 2019-03-23
For me it worked perfectly.
1. Launch heroses by typing: "wine HD_Launcher.exe"
2. Click "Create HD exe"
3. Set source size to: 1180x664
4. Click play :)

---

