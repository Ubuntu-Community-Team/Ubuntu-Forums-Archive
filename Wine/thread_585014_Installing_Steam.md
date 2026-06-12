---
title: "Installing Steam"
date: 2007-10-21
forum: Wine
---

### Post by surferkid993 on 2007-10-21
I've seen posts and posts about the steam 26% bug. And they say that typing this into the terminal fixes it:
```
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
but when I type that in I get this:
```
wine: could not load L"c:\\windows\\system32\\SteamTmp.exe": Module not found
```
so I did more research and it said to use this instead:
```
 wine "C:\Program Files\Steam\SteamTmp.exe" SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
this ran the steam update but it still stopped at 26% and said I can't run steam more than once.

---

### Post by cogadh on 2007-10-21
Run this instead:
```
nice -n 19 wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
If that doesn't work, then run this:
```
nice -n 19 Steam.exe
```

---

### Post by surferkid993 on 2007-10-21
nope neither worked this is what I get:
```
justin@justin-desktop:~$ nice -n 19 wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
wine: could not load L"c:\\windows\\system32\\SteamTmp.exe": Module not found
justin@justin-desktop:~$ nice -n 19 Steam.exe
nice: Steam.exe: No such file or directory

```

---

### Post by Sockerdrickan on 2007-10-21
Dude... You should do it with the actual file adress afaik. I'm taking it your steam.exe is not on your desktop

get the latest msi install from [www.steamgames.com](www.steamgames.com) and do wine start SteamInstall.msi

---

### Post by pwrstick on 2007-10-21
Hello,

I was having the same problem. When any commands are entered you may wish to navigate to the steam directory:

/home/YOURNAME/.wine/drive_c/Program Files/Steam/

I found running commands in here worked "better", but I was still having error messages like you.

Oddly, after running the 'nice' commands, which then errored out, I happened to re run the steam installation, did a repair, and now it works.

Don't forget to install the Tahoma font or you wont be able to see any text.

---

### Post by cogadh on 2007-10-21
> **surferkid993 said:**
> nope neither worked this is what I get:
```
justin@justin-desktop:~$ nice -n 19 wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
wine: could not load L"c:\\windows\\system32\\SteamTmp.exe": Module not found
justin@justin-desktop:~$ nice -n 19 Steam.exe
nice: Steam.exe: No such file or directory

```
Sorry, I should have specified that you need to "cd" to Steam's install directory before running either one of those. In fact, before you run anything in Wine, you should change to its install directory.

---

### Post by wennermark on 2008-03-16
Have anybody solved this problem yet?

---

### Post by rickatnight11 on 2008-03-19
Yes.  I had these issues and this line worked great:

> nice -n 19 wine Steam.exe

Just make sure you are in the ...Program Files/Steam directory.

---

