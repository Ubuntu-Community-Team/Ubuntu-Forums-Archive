---
title: "Wine - Small fonts are ugly"
date: 2008-07-15
forum: Wine
---

### Post by kdorf on 2008-07-15
All of my Wine apps have ugly fonts in certain places -- examples are the console in Half-Life 2, and tabs on the Photoshop CS2 tool windows.

I've installed msttcorefonts and symlinked the wine prefix C:\windows\Fonts folder to the folder where my MS fonts are installed (/usr/share/fonts/truetype/msttcorefonts if I remember right) and I even dumped the remaining missing Windows fonts from my install to that directory.

I've looked at other peoples' screenshots and they do not seem to have ugly fonts where mine are.

Any ideas? It's kind of annoying because in some places (HL2 console is a really good example) it makes the font completely unreadable.

---

### Post by smoothness on 2008-07-25
I also am having the same/similar issue. For example, in Steam the majority of the fonts appear fine, however the smaller ones (such as the text in the Steam Friends box) appears poorly scaled.

Here is an example:

[img]http://img26.picoodle.com/img/img26/4/7/25/f_SteamScreenm_73fa9b2.png[/img]

Cheers, Arite.

---

### Post by kdorf on 2008-07-25
That's pretty much exactly what it looks like for me, too, smoothness.

Anybody have a solution?

---

### Post by KillaW0lf04 on 2008-07-27
same problem applies here........do we have to install new microsoft fonts or something?

---

### Post by kdorf on 2008-07-27
Installing the MS fonts never helped me at all.

---

### Post by kdorf on 2008-08-02
Bump. Still haven't found a solution. Not that it would necessarily help, but I have a few screenshots from Warhammer40k. As you can see, the text is just plain unacceptable. It's readable at that size, but if it gets any smaller readability is 0.

I've been messing around in gnome-appearance-properties and changing font sizes, default fonts, etc. but nothing helps.

Anybody? =(

Quick recap:
-Installing msttcorefonts did not help
-Symlinking my wineprefix's C:\windows\fonts directory to /usr/share/fonts/truetype/msttcorefonts did not help
-Changing font settings in gnome-appearance-properties did not help
-Using a new wine prefix does not help (it occurs in all of them)
-Does not happen in native Linux applications, only in Windows apps and 99% of the time it is only when the fonts are really small (menus in DoW are an exception it seems)

---

### Post by KillaW0lf04 on 2008-08-03
that doesnt have to do with wine, i used to have it in my windows variant as well. Just turn up the anti-aliasing settings manually from nvidia-settings and it should get better. Do you play often online? Add me sgtward08

---

### Post by kdorf on 2008-08-03
> **KillaW0lf04 said:**
> that doesnt have to do with wine, i used to have it in my windows variant as well. Just turn up the anti-aliasing settings manually from nvidia-settings and it should get better. Do you play often online? Add me sgtward08

While this has helped the problem, it hasn't fixed it -- programs that don't use 3D acceleration aren't affected at all. That's not to mention that it's complete rubbish that I should have to use 8x antialiasing to see better text (which still isn't perfect.)

I tried a multitude of different settings -- any other ideas?

---

### Post by kdorf on 2008-08-03
Okay - new update. Turns out I'm somewhat of an idiot. =)

When I had tried symlinking my wineprefix's C:\windows\Fonts directory, the link was fonts, not Fonts. Things now look good in applications like Photoshop and Steam.

Step by step - here's what I did:
-Copied all Windows fonts from the Windows partition into /usr/share/fonts/truetype/msttcorefonts/
-Symlinked my wineprefix's C:\windows\Fonts to /usr/share/fonts/truetype/msttcorefonts/

However, a few more questions. First, I use different wineprefixes for each program. I have to symlink for each prefix before things will work - is there another default directory wine looks in that I can copy those fonts to? EDIT: strike that. share/wine/fonts/. Having different versions compiled makes this a little more work, but oh well. 

Secondly, DoW's font still looks like major suck. While KillaW0lf04's idea did help, it is still painful on the eyes. Any ideas?

Thanks!

---

### Post by KillaW0lf04 on 2008-08-03
do you have any idea where i can download these microsoft fonts? I dont have a windows partition on this computer so i cant copy the fonts like you did.

As for dow, i use 2x AA and the font seems quite ok for me. Its far from perfect but its deffinatly readable. What resolution are you running it at?

---

### Post by kdorf on 2008-08-03
I'm running @ 1920x1200. What I actually did was manually hacked my DPI lower in the wine registry so the letters were bigger (why lower DPI = bigger letters in Dawn of War, no idea). It's much more readable now, though still far from perfect.

It seems like anything less than 8x AA doesn't make any difference. If you want to get (some) of the microsoft fonts, you can run
```
sudo apt-get install msttcorefonts
```

And that will get you the basic ones.

---

### Post by smoothness on 2008-08-04
> **kdorf said:**
> Okay - new update. Turns out I'm somewhat of an idiot. =)

When I had tried symlinking my wineprefix's C:\windows\Fonts directory, the link was fonts, not Fonts. Things now look good in applications like Photoshop and Steam.

Step by step - here's what I did:
-Copied all Windows fonts from the Windows partition into /usr/share/fonts/truetype/msttcorefonts/
-Symlinked my wineprefix's C:\windows\Fonts to /usr/share/fonts/truetype/msttcorefonts/
Thanks - that helped. In the end I decided to just copy and replace the contents of WINDOWS/Fonts in my Windows partition into ~/.wine/drive_c/windows/Fonts and small fonts now render correctly.

In actual fact copying all of the fonts isn't entirely necessary, for Steam anyway, since the issue is to do with only tahoma.ttf. As described in the Wine AppDB Steam page [here]("http://appdb.winehq.org/appview.php?iVersionId=1554") as of 0.9.47 and later there is a replacement for tahoma.ttf which works - however doesn't render well at small resolutions, hence to solve the issue use the Windows tahoma.tff. Either get it from a Windows partition or nter e.g. "filetype:ttf inurl:tahoma" into Google and looks for a non-wine version (Wine version is 83.2kB, Windows version is 374.2kB for XP) on then place it into ~/.wine/drive_c/windows/Fonts (or where ever Wine Fonts are located) and hopefully it should render small fonts correctly.

> **KillaW0lf04 said:**
> do you have any idea where i can download these microsoft fonts? I dont have a windows partition on this computer so i cant copy the fonts like you did.
No since they are copyrighted fonts. As kdorf said msttcorefonts might help.

Cheers, Arite.

---

### Post by sisslack on 2008-11-24
This kinda worked for me.  I found that it made the fonts smaller but more readable.

```
wget http://download.microsoft.com/download/office97pro/fonts/1/w95/en-us/tahoma32.exe
wine tahoma32.exe

```

Follow the wizard.

---

### Post by SnakeHips on 2008-12-16
Lucida-Console.ttf is the font that works correctly in the HL2 developer's console. 

copy/paste into
drive_c/windows/fonts

---

### Post by nerdking on 2008-12-16
i had this problem easy way to fix it is to install winetricks.
i dont know the exact download location but i think it is the first thing that shows up if you google it.

---

### Post by handy on 2008-12-16
Thanks for the winetricks tip.

---

### Post by patsissons on 2009-02-19
nice, i have been wondering about this one for a while.  My guess is that if you install hl2 through wine then you get this font with that install, but since i always just copy the steam dir from my windows partition i never get it.

```

wget -O Lucida-Console.ttf http://www.webpagepublicity.com/free-fonts/l/Lucida%20Console.ttf

```

---

### Post by NightMKoder on 2009-02-20
Consider experimenting with 

[http://ubuntuforums.org/showthread.php?t=1050920](http://ubuntuforums.org/showthread.php?t=1050920)

---

### Post by Petengy on 2009-03-14
> **sisslack said:**
> This kinda worked for me.  I found that it made the fonts smaller but more readable.

```
wget http://download.microsoft.com/download/office97pro/fonts/1/w95/en-us/tahoma32.exe
wine tahoma32.exe

```

Follow the wizard.

TnX a lot
That's worked for me too

By Pet

---

### Post by Tobine on 2009-04-17
> **sisslack said:**
> This kinda worked for me.  I found that it made the fonts smaller but more readable.

```
wget http://download.microsoft.com/download/office97pro/fonts/1/w95/en-us/tahoma32.exe
wine tahoma32.exe

```

Follow the wizard.

This did the job on my Dreamweaver CS3 fonts!

Thanks!

---

### Post by zami on 2009-04-17
For WineTricks, from terminal it's

```
wget -nv http://www.kegel.com/wine/winetricks
```

then

```
chmod 700 ./winetricks
```

then to run it,

```
./winetricks
```

a menu will pop up.  There are a several options related to fonts in there, including core fonts, Tahoma, a few entries listed as font fixes.

Hope that helps.

-zami

---

### Post by hydrox24 on 2011-04-28
> **kdorf said:**
> Okay - new update. Turns out I'm somewhat of an idiot. =)

When I had tried symlinking my wineprefix's C:\windows\Fonts directory, the link was fonts, not Fonts. Things now look good in applications like Photoshop and Steam.

Step by step - here's what I did:
-Copied all Windows fonts from the Windows partition into /usr/share/fonts/truetype/msttcorefonts/
-Symlinked my wineprefix's C:\windows\Fonts to /usr/share/fonts/truetype/msttcorefonts/

However, a few more questions. First, I use different wineprefixes for each program. I have to symlink for each prefix before things will work - is there another default directory wine looks in that I can copy those fonts to? EDIT: strike that. share/wine/fonts/. Having different versions compiled makes this a little more work, but oh well. 

Secondly, DoW's font still looks like major suck. While KillaW0lf04's idea did help, it is still painful on the eyes. Any ideas?

Thanks!
This post was a Godsend for me, I had been looking for a way to fix the dead ugly UI on all my office apps running under WINE for ages and this is just fantastic. Thanks to all those that contributed to this solution.

---

