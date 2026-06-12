---
title: "No text in IE6 with ies4linux"
date: 2008-01-12
forum: Wine
---

### Post by spartan_87 on 2008-01-12
I installed ies4linux and installed IE6 because I need to use it for MathXL to do math homework. When I launch IE6 it loads and the webpage comes up and looks fine, but there is no text or address bar on the IE6 toolbar, I just see the icons and everything else is grey including the address bar, but I can still type where the address bar is supposed to be, but can't see what I am typing. I thought maybe I didn't have the correct fonts installed so I installed the arial and times fonts, but that didn't fix anything. Any ideas of how to fix this?

---

### Post by akaihola on 2008-01-13
I can confirm this on my Gutsy setup. Both IE6 and the beta installation of IE7 have no text in the toolbars and menus.

---

### Post by pernor998 on 2008-01-14
Same here. It's supricing if this is a new problem. I run xranr and multiple screens om Ubuntu 7.10 Gutsu

---

### Post by spartan_87 on 2008-01-14
Yea I don't know if it is only 7.10 because I never tried this when I had 7.04 and haven't found any post about this specific problem. Anyone know what's up with this?

---

### Post by akaihola on 2008-01-14
Just by change I tried

```
$ LANG=C ~/bin/ie6
```

and it works! My defaut locale is fi_FI.UTF-8, so apparently there's a problem with that.

---

### Post by spartan_87 on 2008-01-14
I tried the command you did and it didn't work for me. Everything is still the same, just grey where there is supposed to be text boxes and the same on the toolbar and menus. :(

---

### Post by jslmg on 2008-01-14
I'm getting this too. It's a new bug. Two weeks ago, when I first installed ies4linux, it was great.

There was a Wine update a couple of days ago. That may be the culprit. I've read somewhere that some versions of Wine work with ies4linux, others don't.

Does anyone know where to go to file a bug report? I checked the ies4linux website, but it looks like their forums are not very active.

---

### Post by jslmg on 2008-01-15
Is this what you guys are seeing? The same lack of buttons in the toolbar?

---

### Post by wizbit on 2008-01-15
That's what I'm seeing - just a few random icons dotted about the screen.

I'm using 7.04 so it's not just Gutsy thats broken, as someone else said - chances are it's wine thats at fault.

---

### Post by gururise on 2008-01-15
What version of wine are you guys using?

I'm using 0.9.53winehq on AMD64 and I'm unable to see the buttons or toolbar text.

EDIT:  I just downgraded to 0.9.46ubuntu and now the menu's work. There is some type of regression in the latest wine. Perhaps somebody should let the Wine people know about this.

---

### Post by jrusso2 on 2008-01-15
> **wizbit said:**
> That's what I'm seeing - just a few random icons dotted about the screen.

It almost looks like to me that whatever font it wants to use for the menus is not present.

 
I'm using 7.04 so it's not just Gutsy thats broken, as someone else said - chances are it's wine thats at fault.

I have forgotten which font windows uses but if there is a way to change the menu font to another one its worth a try.

---

### Post by confused57 on 2008-01-15
> **gururise said:**
> What version of wine are you guys using?

I'm using 0.9.53winehq on AMD64 and I'm unable to see the buttons or toolbar text.

EDIT:  I just downgraded to 0.9.46ubuntu and now the menu's work. There is some type of regression in the latest wine. Perhaps somebody should let the Wine people know about this.

I downgraded from 0.9.53winehq to 0.9.51winehq, which corrected the missing toolbars & text(on a 32-bit pc):
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

I thought it might be something I was doing wrong, trying to run ie6 with 0.9.53 in Feisty, cpu would spike & remain at 99-100% ...had to kill wineserver pid from terminal.  ie6 works quite well with 0.9.51.

---

### Post by jslmg on 2008-01-15
> **confused57 said:**
> I downgraded from 0.9.53winehq to 0.9.51winehq, which corrected the missing toolbars & text(on a 32-bit pc):
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)


I thought that might be the issue, and I was just about to do the downgrade, too.

---

### Post by jslmg on 2008-01-16
Well, when you remove Wine, at least in synaptic, you'll have to remove ies4linux too, unless there's a method for avoiding that.

I'm gonna go ahead and remove ies4linux, too, then start fresh... first installing the wine downgrade, then ies4linux again.

---

### Post by Matthijs van Henten on 2008-01-16
Hello, I fixed it like this:
```

$export WINEPREFIX="/home/matthijs/.ies4linux/ie7"
$winecfg

```

in winecfg, change the windows version to something else (window 98 )

Remember, the ies4linux wine files don't reside in ~/.wine but .ies4linux
So you'll have to configure each separately.

Hope this helps,

Bye

---

### Post by jslmg on 2008-01-16
> **Matthijs van Henten said:**
> Hello, I fixed it like this:
```

$export WINEPREFIX="/home/matthijs/.ies4linux/ie7"
$winecfg

```

in winecfg, change the windows version to something else (window 98 )

Remember, the ies4linux wine files don't reside in ~/.wine but .ies4linux
So you'll have to configure each separately.

Hope this helps,

Bye

Well, I went ahead and downgraded to 0.9.51, which fixed the problem fully. However, I'll always have 0.9.53 showing up in my Update Manager for eternity or until I find out there's been a fix in ies4linux. That's the caveat.

So, Matthijs's fix might be better, if it means keeping 0.9.53. So,  I may update to that, then try Matthijs's fix later.

For those of you doing the downgrade, make sure to fully remove Wine through Synaptic first, along with ies4linux. Restart the computer to purge all caches and whatevers. After reboot, proceed to [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html), and get the 0.9.51.

 After installing that, get ies4linux. Use achatwick's deb package for best results, if you haven't already--does a very efficient job, and puts IE6 right into your usr/share/applications folder. Get it at [http://ubuntuforums.org/attachment.php?attachmentid=53346&d=1197785907](http://ubuntuforums.org/attachment.php?attachmentid=53346&d=1197785907).
Read about it at [http://ubuntuforums.org/showthread.php?t=636758](http://ubuntuforums.org/showthread.php?t=636758)

---

### Post by joeycbulk on 2008-01-18
Interface does not show clearly because of the theme used. To fix this you need to use the defaults.

```

cd ~/ies4linux/ie6
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

### Post by Ludwik on 2008-01-19
> **joeycbulk said:**
> Interface does not show clearly because of the theme used. To fix this you need to use the defaults.

Works great, thanks!

---

### Post by campero on 2008-01-19
Same thing is happening to me, it was fine before and all the sudden it doesn't work any more. Same symptoms. Any suggestion on how to fix this?

---

### Post by Tyche on 2008-01-19
Thanks for your "quick and dirty" solution. Worked like a champ.  There appear to be other problems with either the installation or wine, but certainly not a fault of yours.

Thanks Again.  I've added a "Thanks" to your info on the right hand side of your header, too.

---

### Post by Ludwik on 2008-01-19
> **campero said:**
> Same thing is happening to me, it was fine before and all the sudden it doesn't work any more. Same symptoms. Any suggestion on how to fix this?

Did you try joeycbulk's suggestion above?

---

### Post by campero on 2008-01-19
> **joeycbulk said:**
> Interface does not show clearly because of the theme used. To fix this you need to use the defaults.

```

cd ~/ies4linux/ie6
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

I couldn't find the directory you mentioned (n00b) but I found it through here:
```

~/ies4linux-2.0.5/winereg$ dir
homepage.reg  ie55.reg  ie5.reg  ie6.reg  ie6.reg~

```

I then deleted what you suggested from "ie6.reg" but the same thing is still happening. Any other ideas?

---

### Post by wiesbert on 2008-01-20
[QUOTE=joeycbulk;4158076]Interface does not show clearly because of the theme used. To fix this you need to use the defaults.

```

cd ~/ies4linux/ie6
cp user.reg ~/user.reg.old
gedit user.reg

```

...


WORKED INSTANTLY without downgrading WINE, thank you !!!


kr wiesbert

---

### Post by DakoCwerf on 2008-01-26
> **joeycbulk said:**
> Interface does not show clearly because of the theme used. To fix this you need to use the defaults.

```

cd ~/ies4linux/ie6
cp user.reg ~/user.reg.old
gedit user.reg

```

In the text editor, delete [Control Panel\\Colors] and the entries under it.

```

This is the part that I deleted. I'm not sure if every one has the same.

[Control Panel\\Colors] 1200623437
"ActiveBorder"="228 228 228"
"ActiveTitle"=hex(1):
....
"WindowText"=hex(1):
```

Make sure to stop deleting before the next group.
```

Example: Stop deleting line before the ff.
[Control Panel\\Desktop] 1200623418
[Control Panel\\Desktop\\WindowMetrics] 1200623418
[Control Panel\\International] 1200623413

```

worked perfectly!!!! thx a lot

---

### Post by ReedyCreek on 2008-01-26
Just wanted to thank joeycbulk for the easy fix!! Anytime you can patch code it's better than down/up-grading and taking a chance on breaking something else! :p I have to use ies4linux for OWA access (firefox rendering is horrid!) and this was making me nuts!!

---

### Post by sirzepp on 2008-01-30
Thanks joeyc!

---

### Post by luctor on 2008-02-01
> **campero said:**
> I couldn't find the directory you mentioned (n00b) but I found it through here:
```

~/ies4linux-2.0.5/winereg$ dir
homepage.reg  ie55.reg  ie5.reg  ie6.reg  ie6.reg~

```

I then deleted what you suggested from "ie6.reg" but the same thing is still happening. Any other ideas?

On my pc the path is
```

/home/rob/**.**ies4linux/ie6
```

notice the "." before "ies4linux/ie6"

---

### Post by altonbr on 2008-02-04
I can confirm that
```
LANG=C ~/bin/ie6
```
fixes my ies4linux IE6 problem!

Thank you!

---

### Post by Jmejme on 2008-02-05
Genius!!! thanks it totally worked Props !!!
i needed it for mymathlab too

---

### Post by Zecc on 2008-02-12
> **Ludwik said:**
> Works great, thanks!

Deleting the color section in user.reg worked for me too. And I'm using Fedora on this computer. :)

Thanks DakoCwerf !

---

### Post by steve101101 on 2008-06-08
> **altonbr said:**
> i Can Confirm That
```
lang=c ~/bin/ie6
```
Fixes My Ies4linux Ie6 Problem!

Thank You!

This Is The Fix.... Thanks So Much

---

