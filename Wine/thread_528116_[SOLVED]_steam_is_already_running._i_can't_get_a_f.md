---
title: "[SOLVED] steam is already running. i can't get a full update."
date: 2007-08-17
forum: Wine
---

### Post by opendevlite on 2007-08-17
i'm stuck with 26% of updating process, i tried this code:

wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14

but still doesn't work, can anyone help me?

---

### Post by cogadh on 2007-08-17
Try this:
```
nice -19 wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```

---

### Post by scribbles on 2007-08-25
That took care of the issue! Can anyone explain WHY that command works, what it does etc?

---

### Post by cogadh on 2007-08-25
I'm not sure why it works, but the "nice" command changes the scheduling priority of a running app. That command is supposed to increase the scheduling priority of the running Wine app, however when I run it on my system, it actually appears to *decrease* the scheduling priority. Either way, it works for some reason.

Technically, you can't increase the scheduling priority without using sudo or root and the correct syntax to do that would be like this:
```
sudo nice -n -19 wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
But using sudo or root to run Wine is really bad, so don't do it.

---

### Post by DoktorSeven on 2007-08-25
Actually I did it by DEcreasing the scheduling priority of Steam.exe with 

nice -n 19 Steam.exe

and it worked as well, and it doesn't require sudo which is a bad idea for running Wine programs.

---

### Post by juamez. on 2007-11-01
> **cogadh said:**
> Try this:
```
nice -19 wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```

DEAR GOD, this did it for me. I owe you a thousand internets, kind sir!

---

### Post by jhmvrNow on 2007-12-01
Hey, where i write/put that code?? please tell me

and i put:

nice -19 wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14

all of this?

---

### Post by cogadh on 2007-12-01
You need to use the terminal to enter the command. First you should change directories to where you installed Steam, then run the command, like this:
```
cd .wine/drive_c/Program\ Files/Steam
nice -19 wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```

---

### Post by jbaerbock on 2008-03-03
How would I do this with Crossover Office? Have steam installed but get the same error, gets to 27% and blingo says another steam is already running which aint true of course. What would the command be with cxoffice?

---

### Post by jbaerbock on 2008-03-03
Something like this perhaps?

nice -19 cxoffice/bin/steam SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14

---

### Post by jbaerbock on 2008-03-03
Nvm this is what worked:  nice -19 cxoffice/bin/steam 14

---

### Post by Roryking on 2008-03-03
From the "nice" man page: "Nicenesses  range from -20 (most favorable scheduling) to 19 (least favorable)."

Think of a vertical scale, with -20 at the **top** and 19 at the **bottom**. That is why setting it to 19 decreases the priority. From what I understand Steam has some sort of disk cache issue that hasn't yet been addressed completely in Wine, so it will sometimes create the 26% error, as well as sometimes causing a "registry in use" error when launching some games.

Hope this clears things up!

---

### Post by knepig on 2008-03-14
> **jbaerbock said:**
> Something like this perhaps?

nice -19 cxoffice/bin/steam SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14


i just started using ubuntu 2 days ago. i did't think that it was possible to play cs condition zero in linux, after i finaly installed ubuntu and installed crossover the steamupdate stoped at 26 % and i almost ¥@£#"¤& !!

thank you so much for solving the problem!!


all beeing so helpful in linux forums, I'm a 2-day-noob today, see you tomorrow ](*,)



------------------------------------

// Knepig

---

### Post by opendevlite on 2008-05-22
Wine 0.9.59 solve this problem

Installing Steam through wine
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554)

---

### Post by swd40 on 2008-07-19
> **cogadh said:**
> You need to use the terminal to enter the command. First you should change directories to where you installed Steam, then run the command, like this:
```
cd .wine/drive_c/Program\ Files/Steam
nice -19 wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```

When you say "terminal" your not refer to Hyper Terminal? If I get more information on how to enter these codes in that would great. By the way, my OS is Windows Vista Home Edition

Please reply

---

### Post by CnlPepper on 2008-07-26
Err... this is a linux support forum for the Ubuntu linux distribution. This is not a forum for Windows Vista. The command you are quoting won't do anything in Windows Vista. If you are having general problems with steam on Windows you'll find more help on the steam forums: [http://www.steampowered.com/v/index.php?area=forum&cc=GB](http://www.steampowered.com/v/index.php?area=forum&cc=GB)

---

