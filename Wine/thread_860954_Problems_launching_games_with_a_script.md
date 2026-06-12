---
title: "Problems launching games with a script"
date: 2008-07-16
forum: Wine
---

### Post by jbsongaku on 2008-07-16
I use this script I found to launch games in another X session with wine, but I cannot get the script to pass the arguments to wine so it doesn't run properly. The game is CSS btw

```
#!/bin/sh 
#Launches a new X session on display 3. 
X :3 -ac & nvidia-settings --load-config-only 
# Goto game dir (modify as needed) 
cd "/home/BACKUP/Program Files/Counter-Strike Source/" 
# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2 
#Launches game (modify as needed) 
DISPLAY=:3 WINEDEBUG=-all wine "D:/Program Files/Counter-Strike Source/hl2.exe" -steam -game cstrike -console
```

The variables -steam -game cstrike and -console are not passed, therefore the game doesn't even start (the -game cstrike part is mandatory)

Any help you can provide?

---

### Post by jbsongaku on 2008-07-18
Bump!

---

