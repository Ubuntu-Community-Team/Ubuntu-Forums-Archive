---
title: "Notepad++ 8.3.2 fails to start and has this error: wine: cannot find L&quot;/home/&lt;UserNam"
date: 2022-05-09
forum: Wine
---

### Post by nectarinebandit on 2022-05-09
This week (May 9, 2022), Notepad++ stopped working for me. Running ```
notepad-plus-plus
``` in the terminal produces this error.

```

<UserName>@<MachineName:~$ notepad-plus-plus 
Installing application.. 
Running hook '/snap/notepad-plus-plus/363/sommelier/hooks/pre-install' 
Starting application.. 
wine: cannot find L"/home/<UserName>/snap/notepad-plus-plus/common/.wine/dosdevices
/z:/home/<UserName>/snap/notepad-plus-plus/363/notepad-plus-plus/notepad-plus-plus.exe"

```

After some digging, see reference 1, it seems the latest Notepad++ 8.3.2 made available through an Ubuntu Software update had a signfiicant defect. The solution is to revert to an older version of Notepad++. This command reverts you to an older version of Notepad++ and resolved the error for me.

```
snap refresh --beta notepad-plus-plus --devmode
```

Alternatively, you can check any old versions available on your system with this command.

```

(base) apricot@apollo:~/Downloads$ snap list notepad-plus-plus --all
Name               Version  Rev  Tracking     Publisher  Notes
notepad-plus-plus  8.3.2    363  latest/beta  mmtrt      disabled,devmode
notepad-plus-plus  8.1.9.3  334  latest/beta  mmtrt      devmode

```

To downgrade, you can use this command.

```

sudo snap revert notepad-plus-plus --revision 334

```

Unfortunately, if you use already used this command to completely remove Notepad++, *snap revert* will not work, but *snap refresh* should work.

```
snap remove --purge notepad-plus-plus
```

Hopefully in a few days or weeks, a newer version of Notepad++ is available which fixes the initial issue. For now, dowgrading gets me through my days.

References

1. [https://notepad-plus-plus.org/downloads/v8.3.2/ ]("https://notepad-plus-plus.org/downloads/v8.3.2/")"Due to a critical regressions found in 8.3.2 release, please download v8.3.3 in which the critical issues have been fixed."

---

### Post by pstuwx on 2022-05-10
thank you so so much for this solution.God send

---

### Post by nectarinebandit on 2022-05-14
The Ubuntu Software center now makes Notepad++ 8.4.1 available and works just fine, i.e the issue no longer exists and Notepad++ opens just fine. If you downgraded to a beta version via "snap refresh --beta notepad-plus-plus --devmode," you may now just install Notepad++ 8.4.1 through the Ubuntu Software center.

---

### Post by TheFu on 2022-05-14
I can't imagine using an editor for another OS on any Unix, since there are so many fantastic native editors.  Have you looked at **Atom** or **Geany**? These are light, but have a plugin capability to extend for any needs you might have.

Of course, the hardcore Linux/Unix people would choose an editor based on vi or emacs which have been around since the 1970s, but those take a little time to learn. OTOH, once even 10% of vim is mastered, you'll know there's no need to any other editor. In the hands of an expert, no editor can compete with vim. None.

But, geany is nice too for people who use Notepad++ on that *other OS*. ;)  Geany is cross-platform, so you don't need to leave it behind regardless of the OS you happen to be using. Not as cross-platform as vim, but still all the major platforms.  I've never seen a router with anything other than a stripped down vi/vim as the only editor available.

Try native tools before reverting to WINE. You'll thank me.
And if you need to compare and merge files, check out **meld**. It is the best comparison tool on any platform, anywhere.

---

### Post by Holger_Gehrke on 2022-05-16
To add to the comment by TheFu: If you are absolutely bent on having something that looks and behaves as much as possible like Notepad++ on Ubuntu, there's always notepadqq. It's in the repositories and since it's not a snap and doesn't need two wine-platform snaps of about 700MB together it's smaller and faster to start.

Holger

---

