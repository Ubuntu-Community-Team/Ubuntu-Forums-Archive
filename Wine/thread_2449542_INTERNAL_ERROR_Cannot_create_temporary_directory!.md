---
title: "INTERNAL ERROR: Cannot create temporary directory!"
date: 2020-08-28
forum: Wine
---

### Post by kingpenguin on 2020-08-28
I have installed wine from apt that comes with ubuntu and winetricks as well. I created a winebottle but running "WINEARCH=win32 WINEPREFIX=~/Wine/CustomerToolkit winetricks" and installed everything that I need for the application to run. When I try to run the application by running "WINEARCH=win32 WINEPREFIX=~/Wine/CustomerToolkit wine ~/Wine/CustomerToolkit/drive_c/users/chris/Desktop/CustomerSuccessToolkit/CustomerSuccessToolkit.exe" I get the error "INTERNAL ERROR: Cannot create temorary directory!". If I run this application as sudo it does work but I know it is not recommended to do. It seems to be trying to access something in /root/.wine but the folder does not exist. How can I force wine to use my winebottle directory that I have setup? There is not a linux equivalent to the program as it is something that my company has written. The part that frustrates me is that this works if I run it as sudo!

---

### Post by mastablasta on 2020-08-29
wine folder should be in /home/.wine

then you don't need sudo to access it. maybe a setting in wine is off, though you say you installed it from apt (repositories), and apps there are usually configured with sane defaults.

you could also give playonlinux a try.

in any case, as far as the app itself is concerned it only exists in ~/[COLOR=#ff0000]**.**[/COLOR]Wine/CustomerToolkit/drive_c/ or ~/**[COLOR=#ff0000].[/COLOR]**Playonlinux/CustomerToolkit/drive_c/ which ever is used for install. they (windows apps) are "not aware" of outside folders. particualrly of those outside of /home folder. 

maybe you missed a dot (indicating a hidden folder/file) in your launcher/shortcut?

if all fails there is also virtualbox :)

---

### Post by kingpenguin on 2020-08-29
I have tried playonlinux and I get the same error when it tries to run the application. I am trying to completely get rid of windows 10 not try to become more dependent on it.

---

### Post by CatKiller on 2020-08-29
> **kingpenguin said:**
> I get the error "INTERNAL ERROR: Cannot create temorary directory!". If I run this application as sudo it does work but I know it is not recommended to do. It seems to be trying to access something in /root/.wine but the folder does not exist... The part that frustrates me is that this works if I run it as sudo!

It's *because* you've been running things as root that you've created this problem for yourself.

> There is not a linux equivalent to the program as it is something that my company has written.

Since it's your own program you can make your own Linux-native version: not everything will run through Wine.

---

### Post by kingpenguin on 2020-08-29
Who said it being my program? I said it was one my company wrote! I only ran wine with sudo in a vm not my main machine so I am positive that is not the issue as well. Plus the issue happens with running the application with playonlinux as well. I am not trying to be rude here but if all you are wanting to post is how this will not work I have no need to hear from you! I am asking how to get this to work not empty answers that have noting to do with wine or the application.

---

### Post by mastablasta on 2020-08-29
although, were you running things as root? because wine otherwise doesn't attempt to reach outside of /home

any chance you post the output of all commands you ran to install the application? copy and paste using code tags.

have you tried adding the dot in your launcher? 

```
WINEARCH=win32 WINEPREFIX=~/[SIZE=5]**[COLOR=#ff0000].[/COLOR]**[/SIZE]Wine/CustomerToolkit wine  ~/[SIZE=5]**[COLOR=#ff0000].[/COLOR]**[/SIZE]Wine/CustomerToolkit/drive_c/users/chris/Desktop/CustomerSuccessToolkit/CustomerSuccessToolkit.exe"
```

what kind of directory should the application create? does it create on in windows? maybe you can help it and create one for it in the wine prefix.
> "INTERNAL ERROR: Cannot create temporary directory!"

are there any other errors when you run this application from the terminal?

--

wine is compatibility layer. it is tricking the applications into thinking they are running in windows using some original and some reverse engineered libraries. it is not a windows replacement. so while it works in some cases in most cases it actually doesn't work. i guess more people would move over from windows if we had a free full replacement or if everything worked in Wine.

ReactOS is such an attempt at reverse engineered windows or a drop in replacement, but i don't think they reached even WinXP level yet.

---

### Post by kingpenguin on 2020-08-29
No outside of my vm I have never tried to run wine as root. As I have told you the .wine directory is not even under /root/. It seems that this permission is a bug from wine. I was able to find a bug report on the winehq forums for another application. As to the . before wine I am not trying to use the default wine prefix and I created one for the application because I did not want to mess up my other winebottles. My ~/.wine is bare bones as it was when wine was installed. I never run an application with out creating a wine prefix.

---

