---
title: "SteamInstall.msi"
date: 2007-04-01
forum: Wine
---

### Post by moot on 2007-04-01
Recently Valve changed the SteamInstall file on [Steam Powered]("http://steampowered.com/") from an *.exe file to a *.msi file, the latter of which Wine can't load.  This is a problem because all of the guides to installing Steam using Wine involve using the SteamInstall.exe file.  Should I just download the old SteamInstall.exe file and use that?  Will Steam just update itself after installation?

---

### Post by BrettW on 2007-04-01
If I'm not mistaken, Wine has an msiexec command, app that runs these .msi files. I've had to use it to install steam stuff from backups (backups made through steam, of course). Hope this helps in some way.

---

### Post by moot on 2007-04-01
> **BrettW said:**
> If I'm not mistaken, Wine has an msiexec command, app that runs these .msi files. I've had to use it to install steam stuff from backups (backups made through steam, of course). Hope this helps in some way.

Thank you, that worked just fine.  And for future reference, the command is:

```
~/Desktop msiexec /a SteamInstall.msi
```

---

### Post by Vitaminc23456 on 2007-04-03
i cant figure out the right location, i typed in exactly what was there, and all i got was 
bash: /home/joe/Desktop: is a directory

so then i tried with that /home/joe/Desktop and what i got was this
bash: /home/joe/Desktop: is a directory

so basically im pretty confused and need some help.

---

### Post by Gorthus on 2007-04-03
if thats where the installer is, then what you want to do is:

```
wine msiexec "/home/joe/desktop/steaminstall.msi"
``` keeping cautious of capital letters.

Or you could just google SteamInstall.exe and download that.

---

### Post by Yoooder on 2007-10-06
might be a newer version of wine, but I had to do:
> wine msiexec /i "/home/joe/desktop/steaminstall.msi"

---

### Post by cogadh on 2007-10-06
You can also use this command to run .msi files:
```
wine start install.msi
```

---

### Post by Everywhere_at_Once on 2007-10-07
you should use this method
```
cd /home(if that's where your .msi is located)
wine msiexec /i Steaminstall.exe
```

but beware, there are other things you need to do before installing.
i just finished getting steam running, and trust me, install tahoma before you install steam, unless you like blind guess work.

---

### Post by Sockerdrickan on 2007-10-07
> **Everywhere_at_Once said:**
> you should use this method
```
cd /home(if that's where your .msi is located)
wine msiexec /i Steaminstall.exe
```

but beware, there are other things you need to do before installing.
i just finished getting steam running, and trust me, install tahoma before you install steam, unless you like blind guess work.
Why is the
wine msiexec /i
better than
wine start
?

---

### Post by cogadh on 2007-10-07
They are not actually different at all, they do the same exact thing. Using "start" means Wine has to call upon msiexec on its own, when you use the msiexec directly, it obviously doesn't have to do that. Neither is really better than the other, but using "wine start" means slightly less typing.

---

### Post by Sockerdrickan on 2007-10-07
Yes that's what I meant, why use the long one

---

### Post by cogadh on 2007-10-07
The only reason I can see to use the msiexec method instead of "wine start" is because of msiexec's optional command switches. I honestly don't know what all those switches are (other than the "/i" one), but that is really the only thing that would make sense to me.

---

### Post by deadlydeathcone on 2007-10-07
It's a bit of shameless self promotion, but you might want to check out [my wine script]("http://ubuntuforums.org/showthread.php?t=533257"). It automatically runs .msi files and changes to an application's base directory (as Everywhere_at_Once suggested) automatically.

> **cogadh said:**
> The only reason I can see to use the msiexec method instead of "wine start" is because of msiexec's optional command switches. I honestly don't know what all those switches are (other than the "/i" one), but that is really the only thing that would make sense to me.

Agreeing with this, as "wine start" is easier. It's (sometimes) useful for other things, too, as it actually just opens Wine's default handler for the extension of the file given to it.

---

### Post by devilbar on 2011-01-30
[FONT=Lucida Sans Unicode][SIZE=3]Hey all im Mike, Well I was trying to install Steam "back" into my computer, but it says Steaminstall[1].msi and when i tryed looking for it it wasnt in my computer. ive been trying to search it for a while now but i cant find it its says i need to find it first before I can download it back into my computer? Can someone help me find that file or terminate Steam off of my computer? [/SIZE][/FONT]

---

### Post by R33D3M33R on 2011-01-31
Just redownload steam from [http://store.steampowered.com/](http://store.steampowered.com/) make it executable with

```
chmod +x Steaminstall.msi
```

and run it. It should detect and ask you if you wan't to reinstall.

BTW: you should put such questions in the Wine section of the forum.

---

### Post by Perfect Storm on 2011-01-31
[[img]http://s4.postimage.org/jbyj0j85e/Thread_Necromancer.jpg[/img]](http://www.postimage.org/)

---

