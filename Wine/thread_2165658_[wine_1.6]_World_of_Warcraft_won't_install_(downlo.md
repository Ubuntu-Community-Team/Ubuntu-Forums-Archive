---
title: "[wine 1.6] World of Warcraft won't install (download)"
date: 2013-08-05
forum: Wine
---

### Post by peter16 on 2013-08-05
Hello!

I'm trying to install World of Warcraft through the online installer provided by Blizzard; this is how it looks.

```
Response: 200
{
    "playable" : false,
    "progress" : 0.000000,
    "playable_progress" : 0.000014,
    "download_rate" : 0.000000,
    "download_remaining" : 0.000000,
    "time_playable" : 30016.000000,
    "time_complete" : 1330016.000000,
    "state" : 1002.000000
}
Request Issued: GET /install/wow_engb

Response: 200
{
    "playable" : false,
    "progress" : 0.000000,
    "playable_progress" : 0.000014,
    "download_rate" : 0.000000,
    "download_remaining" : 0.000000,
    "time_playable" : 30016.000000,
    "time_complete" : 1330016.000000,
    "state" : 1002.000000
}
Request Issued: GET /install/wow_engb

```

I choose install, I read and accept the agreement, choose location, etc. And this just keeps looping. Anyone know how to fix this?

It's stuck at 0% and I can't change any settings or anything in the client (those are greyed out).

Thanks in advance.

---

### Post by GwL3eNC on 2013-08-05
Hi,

you should first visit 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922)

and read the marks about your version of the game. Often there is some
info given how to get it run.

---

### Post by peter16 on 2013-08-05
Of course I've read the feedback and comments; there should be no problems with WoW and Wine 1.6.

Thank you for your reponse.

---

### Post by GwL3eNC on 2013-08-05
I founf an old thread about 
[h=2]How To: Wine Programs Cannot Access Internet[/h]It's here [http://ubuntuforums.org/showthread.php?t=768021](http://ubuntuforums.org/showthread.php?t=768021)
Hopefully it helps.

---

### Post by peter16 on 2013-08-05
> **GwL3eNC said:**
> I founf an old thread about 
**How To: Wine Programs Cannot Access Internet**

It's here [http://ubuntuforums.org/showthread.php?t=768021](http://ubuntuforums.org/showthread.php?t=768021)
Hopefully it helps.

Thank you for your reponse.

I run 32 bit Ubuntu 12.04, and libnss-mdns is already installed and updated. Unfortunately, that link didn't help.

---

### Post by Doomspark on 2013-08-05
Have you tried using PlayOnLinux to do the WoW install?

---

### Post by peter16 on 2013-08-05
> **Ilaraxys said:**
> Have you tried using PlayOnLinux to do the WoW install?

Yeah, it didn't work.

---

### Post by GwL3eNC on 2013-08-06
Hi,

i've surfd a bit. Possibley it can help. Found it here

[http://www.mmomeltingpot.com/2012/09/running-world-of-warcraft-under-linux-wine-fixing-agent-exe-failed-and-other-update-errors/](http://www.mmomeltingpot.com/2012/09/running-world-of-warcraft-under-linux-wine-fixing-agent-exe-failed-and-other-update-errors/)

Try it, the interresting thing could be step 4 and 5. But you should read it from start.

Do you got a firewall enabled? If so open your port 3724.

Also i found on a german site:

**Hängt beim Login mit "Downloading"**

 Als Lösung genügt es, WoW einmal nicht mit dem Argument **-opengl**, sondern mit **-d3d9** zu starten (und ggf. in der **config.wtf**  gxapi "opengl" rauszunehmen). Dann kann die Dialogbox, dass Systeminfos  an Blizzard übertragen werden, angezeigt werden. Danach läuft die  OpenGL-Version auch wieder.

it' shurly not exact your probelm, but it's worth try. It say it' hangs on login with "Downloading"
Given solution is to start wow once without -opengl. Replace it with -d3d9. Evtl you have to take out gxapi or "opengl" out of the config.wtf. Then
the Dialog can show up.

---

