---
title: "WoW Error"
date: 2008-03-14
forum: Wine
---

### Post by X3zh on 2008-03-14
Hello.

When I am changing video settings in WoW it crashes and leaves an error message who looks like this:

- This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception.
Program: c:\spel\World of Warcraft\Wow.exe
Exception: 0xC0000005 (ACCESS_VIOLATION) at 0073:7DD38B79

The instruction at "0x7DD38B79" referenced memory at "0x000008F4".
The memory could not be "written".

Press OK to terminate the application.


Does anyone know how to fix this? I'd appreciate it. Thanks.

---

### Post by Shmifty on 2008-05-18
I'm having the exact same problem.

```
ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00822F60

The instruction at "0x00822F60" referenced memory at "0x3F800000".
The memory could not be "read".
```

---

### Post by Trance56k on 2008-05-18
Did you try changing the resolution from the WoW WTF config file?

---

### Post by igster on 2008-05-19
There is a Linux-specific addon for WoW called "Apply to Forehead" that supposedly fixes your problem.  You can get a copy from [http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html](http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html)

Also, WoWWiki has a great Linux/Wine section.  Might be worth your while to look it over.

[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

---

### Post by Shmifty on 2008-05-27
I get this error when just playing, not even trying to adjust video. Any idea why?

---

### Post by jack handy on 2008-05-27
> **igster said:**
> There is a Linux-specific addon for WoW called "Apply to Forehead" that supposedly fixes your problem.  You can get a copy from [http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html](http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html)

Also, WoWWiki has a great Linux/Wine section.  Might be worth your while to look it over.

[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

 

that add-on is outdated and does not seem to work anymore

---

### Post by toleraen on 2008-05-27
I'm getting this error as soon as I do a wine Wow.exe, never gets into the game.

---

### Post by match002001 on 2008-07-23
I had that error after the cinema played it went straight to it. 

all I did was went into the config.wtf file with gedit and added

```
SET gxApi "opengl"
```

then it works like a charm after that :)

---

