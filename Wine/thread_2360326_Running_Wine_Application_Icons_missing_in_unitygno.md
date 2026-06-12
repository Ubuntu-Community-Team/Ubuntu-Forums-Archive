---
title: "Running Wine Application Icons missing in unity/gnome"
date: 2017-05-03
forum: Wine
---

### Post by Jumbs on 2017-05-03
Ubuntu 17.04
Wine 2.0.1

[B]I recently upgraded Ubuntu and i've noticed that the Icons in the running program list have vanished for Wine applications, replaced with a generic icon.
[/B]This is not the booting link icon, that is there.

In gnome 3, it is just a generic icon.
[IMG]http://i.imgur.com/JmppzqJ.png[/IMG]

In Unity, it shows the correct icon briefly when booting it, then it switches to the generic. 
[IMG]http://i.imgur.com/QhRNKv5.png[/IMG]

I have checked the .desktop files, and they correctly reference files in .local/.../apps/...

Additionally the running program is called Wine Windows Program Loader, not the actual application.  If i run 2 wine apps, it collapses them into the one missing icon.
I have checked the .desktop files, and they correctly reference files in .local/.../apps/...

Additionally the running program is called Wine Windows Program Loader, not the actual application.  If i run 2 wine apps, it collapses them into the one missing icon.

---

### Post by kostkon on 2017-05-03
This should be easy to fix.

For each of those wine apps you need to do the following:

open the app, then in a terminal do:
```
xprop WM_CLASS
```
when your cursor changes to a crosshair cursor, click on the wine app's window and xprop should give you the wm_class of the window. If there are more than one values, then you need to keep the one that more likely references the name of the .exe, e.g. ie.exe. Then, open the app's .desktop file and add a new property called StartupWMClass, like this:
```
StartupWMClass=ie.exe
```
That should solve the icon problem and if your app creates more that one window it will even group them under the same icon, the same way Unity and Gnome Shell do for other apps.

Hope that helps.

---

### Post by Jumbs on 2017-05-04
Thanks for the help! It definitely put me on the right track.

However it's still not operating as it should.

First, it did what you said, and put the StartupWMClass in the .desktop file. That didn't seem to help. I then found a script that did similar and ran it.
[https://gist.github.com/iuridiniz/85403545d0fd7e4a0000](https://gist.github.com/iuridiniz/85403545d0fd7e4a0000)
And then rebooted. It suddenly started working for some of the wine applications. I am not sure if the reboot helped the first or second try, but no matter.
[B]
Now everything works in unity (too bad i use gnome) and some items work in gnome[/B]

Both the working and non working icons return the double WM_CLASS(STRING) = "*.exe", "Wine" when xprop is ran. It says this no matter what i set in the desktop file, even gibberish. 

When comparing the .desktops of the working and non working, i cannot find a legit difference.

```
[Desktop Entry]
Name=mIRC
StartupWMClass=mirc.exe
Exec=env WINEPREFIX="~/.wine" wine C:\\\\windows\\\\command\\\\start.exe /Unix ~/.wine/dosdevices/c:/users/Public/Start\\ Menu/Programs/mIRC/mIRC.lnk
Type=Application
StartupNotify=true
Path=~/.wine/dosdevices/c:/Program Files (x86)/mIRC
Icon=7A88_mirc.0

```
Works, while all others does not, like this one:

```
[Desktop Entry]
StartupWMClass=readme.txt
StartupNotify=true
Exec=env WINEPREFIX="~/.wine" wine C:\\\\windows\\\\command\\\\start.exe /Unix ~/.wine/dosdevices/c:/users/Public/Start\\ Menu/Programs/mIRC/Readme.txt.lnk
Path=~/.wine/dosdevices/c:/Program Files (x86)/mIRC
Name=Readme.txt
Type=Application
Icon=C6D9_readme.0

```

On top of that, if i remove StartupWMClass from the one that works, it still works.

Now i am super confused!

---

