---
title: "System Sound at shutdown"
date: 2009-03-18
forum: x86 64-bit Users
---

### Post by Mazen on 2009-03-18
Hello everyone!
i'm uising Ubuntu 9.04 64-bit, and everytime i Shutdown or Restart i get a system BEEEEEP the instant i click the shutdown button...it's annoying and loud!
is there a way to disable it?
Thanks,

---

### Post by 3Miro on 2009-03-18
There should be a disable system beep in the menus somewhere, however, I am not sure if that is the problem. It is not supposed to be beeping on shutdown. (In 8.10 it is under System -> Preferences -> Sound )

---

### Post by Mazen on 2009-03-19
I tried that already! nothing!!:(

---

### Post by blacksm1th on 2009-03-19
This is a possible solution:

Open your terminal and enter:

   ```
 sudo gedit /etc/modprobe.d/blacklist
```

Then add this 2 lines to the blacklist and click save:

   ```
 #Stop PC speaker
    blacklist pcspkr
```

I think this beep is unnecessary for desktop installation but it is present unfortunately.:sad:

---

### Post by Mazen on 2009-03-21
This did not work :S

---

### Post by blacksm1th on 2009-03-22
It works for me on Intrepid. Basic idea is to stop OS using the device. Maybe there in Jaunty this blacklist is changed somehow.

---

### Post by dcstar on 2009-03-22
> **Mazen said:**
> Hello everyone!
i'm uising **Ubuntu 9.04** 64-bit, and everytime i Shutdown or Restart i get a system BEEEEEP the instant i click the shutdown button...it's annoying and loud!
is there a way to disable it?
Thanks,

Report all pre-release problems in the appropriate development forum, that is why this is **DEVELOPMENT** software.:

[http://ubuntuforums.org/showthread.php?t=1063499](http://ubuntuforums.org/showthread.php?t=1063499)

---

