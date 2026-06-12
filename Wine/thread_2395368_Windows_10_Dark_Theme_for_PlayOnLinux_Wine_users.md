---
title: "Windows 10 Dark Theme for PlayOnLinux Wine users"
date: 2018-06-30
forum: Wine
---

### Post by ardouronerous on 2018-06-30
[ATTACH=CONFIG]280262[/ATTACH]

My system is Lubuntu and my system theme is Windows 10 Dark, which you can download here: [https://b00merang.weebly.com/windows-10.html](https://b00merang.weebly.com/windows-10.html)

[IMG]https://i.stack.imgur.com/kWCRw.png[/IMG]

Now because "Enable GTK3 Theming" is unavailable in PlayOnLinux, I've created this theme so my PlayOnLinux applications matches my system's Windows 10 Dark theme.

Instructions:

Open user.reg in a text editor and find the line that says [FONT=courier new][Control Panel\\Colors][/FONT] and add these values:
```
"ActiveBorder"="31 31 31"
"ActiveTitle"="31 31 31"
"AppWorkSpace"="60 64 72"
"Background"="31 31 31"
"ButtonAlternativeFace"="23 23 23"
"ButtonDkShadow"="23 23 23"
"ButtonFace"="31 31 31"
"ButtonHilight"="31 31 31"
"ButtonLight"="23 23 23"
"ButtonShadow"="23 23 23"
"ButtonText"="201 201 201"
"GradientActiveTitle"="31 31 31"
"GradientInactiveTitle"="31 31 31"
"GrayText"="201 201 201"
"Hilight"="0 77 140"
"HilightText"="201 201 201"
"InactiveBorder"="31 31 31"
"InactiveTitle"="31 31 31"
"InactiveTitleText"="201 201 201"
"InfoText"="201 201 201"
"InfoWindow"="31 31 31"
"Menu"="31 31 31"
"MenuBar"="31 31 31"
"MenuHilight"="31 31 31"
"MenuText"="201 201 201"
"Scrollbar"="31 31 31"
"TitleText"="201 201 201"
"Window"="0 0 0"
"WindowFrame"="31 31 31"
"WindowText"="201 201 201"
```

Assuming you created a PlayOnLinux virtual drive with the name "user", user.reg should be in [FONT=courier new]~/.PlayOnLinux/wineprefix/user[/FONT] or [FONT=courier new]~/PlayOnLinux's virtual drives/user[/FONT]

---

