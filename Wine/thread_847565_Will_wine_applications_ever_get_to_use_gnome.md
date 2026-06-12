---
title: "Will wine applications ever get to use gnome?"
date: 2008-07-02
forum: Wine
---

### Post by KillaW0lf04 on 2008-07-02
Hey, sorry if this is a noobish question, but im curious whether applications that run in wine will ever make use of the gnome look in the future? Have the develepors even mentioned it? Or is impossible/not worth the work?

---

### Post by wdaniels on 2008-07-02
No, it's technically impossible. Wine is an open-source implementation of the Win32 API (and some associated stuff) which is a completely different set of interfaces to Gtk. (Well, it's not *strictly* impossible, few things are, but it would be an entirely different, difficult and complex project to put something in the middle to map the interactions of the two, and Windows applications tend to make a lot of assumptions about how the UI is going to be drawn).

However, you could probably create a Windows theme to use in Wine that looks very similar to certain popular Gtk/Metacity themes. The main problem there is that there are hundreds of different themes for various aspects of a Gnome desktop, which people mix and match to their own taste, so I don't know if anybody would bother trying to make an XP theme to fit one particular Gnome look. I don't know much about how the themes work in Windows, but I doubt you could make them dynamic to emulate the Gtk theme.

In short, there are just too many differences on all levels.

---

### Post by YokoZar on 2008-07-02
> **wdaniels said:**
> No, it's technically impossible. Wine is an open-source implementation of the Win32 API (and some associated stuff) which is a completely different set of interfaces to Gtk. (Well, it's not *strictly* impossible, few things are, but it would be an entirely different, difficult and complex project to put something in the middle to map the interactions of the two, and Windows applications tend to make a lot of assumptions about how the UI is going to be drawn).

However, you could probably create a Windows theme to use in Wine that looks very similar to certain popular Gtk/Metacity themes. The main problem there is that there are hundreds of different themes for various aspects of a Gnome desktop, which people mix and match to their own taste, so I don't know if anybody would bother trying to make an XP theme to fit one particular Gnome look. I don't know much about how the themes work in Windows, but I doubt you could make them dynamic to emulate the Gtk theme.

In short, there are just too many differences on all levels.
It's not completely impossible for Wine to take the system theme's look and feel in some ways.

Wine has the capability to load Windows themes.  Someone made a Windows version of Ubuntu's default theme a while back, however there's a nasty bug in Wine that makes it run really really slow.  That's why it's not the default theme, and instead we get ugly Windows-XP era blue stuff.

---

### Post by shad0w_walker on 2008-07-02
As far as I'm aware, you can use themes with wine to give it a more inplace feel, what would be nice is if wine automatically took a copy of the current theme and then generated a theme to use with wine apps, so they would fit in place better. Not perfect, but would be less horridly out of place.

---

### Post by KillaW0lf04 on 2008-07-02
ye thats the reason im asking, the "windows 95" look of wine really looks out of place with the beuatiful interface gnome has in Ubuntu

---

### Post by wdaniels on 2008-07-02
> **YokoZar said:**
> It's not completely impossible for Wine to take the system theme's look and feel in some ways.

Wine has the capability to load Windows themes.  Someone made a Windows version of Ubuntu's default theme a while back, however there's a nasty bug in Wine that makes it run really really slow.  That's why it's not the default theme, and instead we get ugly Windows-XP era blue stuff.

Sure, this is what I was talking about (although I didn't know anybody had ever done it for the default Human theme). My point is that this is not the same as using the native Gtk widgets so it would only really work for people who continue using the default Ubuntu theme, which I don't think many do.

But perhaps it would be quite easy to get Wine to automatically emulate just the colours of the Gtk theme and to use a Windows theme in Wine that looks more generically like Gtk widgets...at least then Wine apps wouldn't look *quite* so out of place...

---

### Post by KillaW0lf04 on 2008-07-03
Where can i get themes for wine from? And do they really decrease performance a lot? (I have a friend using linux that says they do)

---

### Post by wdaniels on 2008-07-03
> **KillaW0lf04 said:**
> Where can i get themes for wine from? And do they really decrease performance a lot? (I have a friend using linux that says they do)

You just use Windows themes with Wine (that's the point). You can install them through the "winecfg" program ("Configure Wine" option in the menu). I can well believe that this is likely to be slow in Wine, but I haven't ever used any themes myself so I don't know *how* slow it is.

---

### Post by Vadi on 2008-07-03
You never know, not even Qt4/KDE4 apps can now look like gnome ones easily ([click]("http://ubuntuforums.org/showthread.php?p=5222533")).

Someway wine will be there too :]

---

### Post by brazemcee on 2008-07-03
Install Wine-doors and select UBUNTU LOOK in the menu.
It will "try" to apply most of your apps an ubuntu look.
But I don't think this is a good idea. By now, loading themes on your winecfg makes your Wine apps run slower.
Remember to uninstall Wine-doors. I'm almost sure Wine-doors can bring damages to your Wine installation.

See you.

---

### Post by atomkarinca on 2008-07-03
> **KillaW0lf04 said:**
> Where can i get themes for wine from? And do they really decrease performance a lot? (I have a friend using linux that says they do)

You can change that default theme from winecfg, just download a windows theme and point to it. However the last time I tried (7-8 months ago) it really slowed down Wine. An alternative way is to change the colour scheme from winecfg.

---

