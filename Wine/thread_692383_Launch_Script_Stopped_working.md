---
title: "Launch Script Stopped working"
date: 2008-02-09
forum: Wine
---

### Post by hOmerscousin on 2008-02-09
Hey, I recently updated wine to the latest version but now the X-session launch script doesn't work. It worked prior before I updated.     

This is the script:
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :2 -ac &
#nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd ~/.wine/drive_c/Program\ Files/Starcraft

# Forces the system to have a break for 2 seconds, X doesn't launch instantly
sleep 2

# Launches game (modify as needed)
DISPLAY=:2 WINEDEBUG=-all wine ~/.wine/drive_c/Program\ Files/Starcraft

The game works if I go directly to my wine menu dropdown. The terminal reports "wine: /home/rdaltreche/.wine is not owned by you." I launch the script with Sudo sh launcher.sh. Any ideas on how I can get to work again and get rid of that error???

---

### Post by hOmerscousin on 2008-02-25
Bump... Any help would be very much so appreciated...

---

