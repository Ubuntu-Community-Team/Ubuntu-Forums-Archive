---
title: "[SOLVED] Help with writing a script for WoW"
date: 2008-07-25
forum: Wine
---

### Post by Beanmonster on 2008-07-25
I'm running a dual boot machine with XP and Hardy.
I have to say I don't feel the need to go back to Windows. I've had an awesome Ubuntu experience.

I currently run World of Warcraft on both, I only need to use windows because of a multichat client running in the background when I need to voicechat, otherwise I play under ubuntu.

Problem is... I need to copy/paste/rename the config.wtf file every time I swap over in order to get it running properly.

Now what I want to do is maybe write a batch/script file that will automatically:

1)Rename config.wtf to WINconfig.wtf
2)Then rename UBUconfig.wtf to config.wtf
3)RUN wow.exe
4)AFTER closing wow.exe, rename config.wtf to UBUconfig.wtf
5)and finally rename WINconfig.wtf to config.wtf

I've googled and searched but haven't really found any easy nor specific answers. I know my way around PC's but I'm not a scripting guru.

Any help/advice or even other suggestions are GREATLY appreciated
Thanking you in advance):P

---

### Post by LinuxRocks713 on 2008-07-28
> **Beanmonster said:**
> <snip size="medium"></snip>

1)Rename config.wtf to WINconfig.wtf
2)Then rename UBUconfig.wtf to config.wtf
3)RUN wow.exe
4)AFTER closing wow.exe, rename config.wtf to UBUconfig.wtf
5)and finally rename WINconfig.wtf to config.wtf

I've googled and searched but haven't really found any easy nor specific answers. I know my way around PC's but I'm not a scripting guru.

Any help/advice or even other suggestions are GREATLY appreciated
Thanking you in advance):P

Change the path the WoW, then save as wowstart.sh:
```

#!/bin/bash
cd */path/to/world/of/wolfcrash/path*
mv config.wtf WINconfig.wtf
mv UBUconfig.wtf config.wtf
wine wow.exe
mv config.wtf UBUconfig.wtf
mv WINconfig.wtf config.wtf

```

and don't forget to chmod +x wowstart.sh

The corresponding Win32 batch file, save as win32wow.bat:
```

cd *Path\To\WORLD\OF\WOLFCRASH\*
wow.exe

```

---

### Post by Beanmonster on 2008-07-28
You have just blinded me with your **AWESOMENESS!!!**

\\:D/\\:D/\\:D/

Thank you very, very, very much

---

### Post by Spydr4590 on 2008-07-28
You do know you could use opengl in windows too :D

---

### Post by Beanmonster on 2008-08-02
I know :) but other configurations are enabled/disabled i.e. death effects, resolution settings etc. thanks anyway ;)

---

