---
title: "New Wine documentation: WineServer"
date: 2008-07-17
forum: Wine
---

### Post by nebid on 2008-07-17
Hi,

I've just added some Wine documentation to [https://help.ubuntu.com/community/WineServer](https://help.ubuntu.com/community/WineServer)

The intention of the WineServer is to run Windows services or applications on boot without a user needing to login. 

I needed this as I run a headless Ubuntu server and I wanted to automatically start a couple of Windows services when I rebooted.

One thing I haven't been able to work out is how to return the virtual terminal that is displayed back to a login terminal eg. Ctrl+Alt+1 or Ctrl+Alt+7. The command chvt doesn't seem to work when the script is started during the boot process, but it does work after the server is booted.

Any thoughts?

---

### Post by YokoZar on 2008-07-17
This reminded me that it would be a nice addition to have a configurable option to run wineboot at login as part of the gnome startup scripts - that way, a user who configured programs to "run at Windows startup" could have them start right away.

---

