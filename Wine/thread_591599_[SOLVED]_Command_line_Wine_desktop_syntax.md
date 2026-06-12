---
title: "[SOLVED] Command line Wine desktop syntax?"
date: 2007-10-25
forum: Wine
---

### Post by karth on 2007-10-25
Hello,

I am asking for advice.

I am a real fan of the wine virtual desktop, for it has solved so many fullscreen glitches in games.

I am aware of the multiple WINEPREFIXes I can make, but I already installed several games that I would like to run under different settings, in the same Wine directory (typically, ~/.wine).

Steam for example: I'd like to be able to run the Steam app in a compiz managed window, but every single game in a Wine virtual desktop. I read that it was possible to specify a -desktop option in the command line tant lanched a game, but it seems to have been removed.

Is it possible to specify a virtual desktop and its dimensions in the command line, while the main setting in winecfg says "Virtual desktop OFF"?

Thanks in advance

---

### Post by hikaricore on 2007-10-25
```

wine **explorer /desktop=1400x1050** gta-vc.exe -- -opengl
```

Here's the launcher I use for ViceCity.  Note the bolded part.  ^_^

Hope this helps.

---

### Post by karth on 2007-10-26
Indeed, it helped a lot :)

I wonder why this was so hard to find, even in the winehq docs...

Thanks!

---

### Post by Ng Oon-Ee on 2008-12-12
> **hikaricore said:**
> ```

wine **explorer /desktop=1400x1050** gta-vc.exe -- -opengl
```

Here's the launcher I use for ViceCity.  Note the bolded part.  ^_^

Hope this helps.

Just a note (I know this is a very old thread, but it turned up in a search), based on [this site]("http://www.winehq.org/wwn/310#Major%20Changes%20to%20Desktop%20Mode"), that should actually be:-

```
wine explorer /desktop=<some_name>,1400x1050 <your_executable>
```

Basically, the suggested code did not work for me, this edited one did. The name doesn't seem too important, however if you're using compiz you can set window rules based on this name (instead of the generic explorer.exe name you get on most wine apps which do not launch directly).

---

