---
title: "HOWTO: Realtek 81xx on Gutsy 64-bit"
date: 2007-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by CRCarl on 2007-10-28
All - 
      A lot of users seem to be having an issue with the Realtek cards in Gutsy on 64-bit. Near as I can tell the issue is with gnome-network-preferences and nm-applet. When I replaced gnome-network-preferences with wicd I was immediately able to connect to any wireless network without a problem. 

     Directions below, please let me know if it works for you. [ More information about wicd is here.]("http://wicd.sourceforge.net")

First - add the wicd repository to sources - 
```

sudo echo deb http://apt.wicd.net gutsy extras >> /etc/apt/sources.list
```

Second - update sources - 
```
sudo aptitude update
```

Third - Install wicd NOTE: Be careful with dependencies - You want to uninstall gnome-network-preferences, but DO NOT uninstall ubunutu-desktop.
```
sudo aptitude install wicd

```

Almost done - Let's start the tray applet. 
```
Alt-F2 /opt/wicd/tray.py
```

At this point you should be able to connect to a wireless network. To start the tray applet automatically go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For a command, enter "/opt/wicd/tray.py".


EDIT: After using the wireless network for a couple of days I realize that while this will get you connected, it does not address the underlying issue with the driver. It still disconnects under heavy load and is generally flaky. If the interface stops working and you can't reconnect this generally fixes it - ```

sudo rmmod rtl8187 & sleep 2 & modprobe rtl8187
```

---

