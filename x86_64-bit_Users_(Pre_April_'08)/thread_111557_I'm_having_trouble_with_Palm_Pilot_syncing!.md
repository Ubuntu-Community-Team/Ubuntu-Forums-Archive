---
title: "I'm having trouble with Palm Pilot syncing!"
date: 2006-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by gdgardnerw on 2006-01-02
I have been trying to get my Tungston E synced with Gnome Evolution for about a week without success. The hotsync spits out an error: the pilot is not configured and gives me a device number. I type that number in through the GNOMEcc as indicated, and it still does not respond.

I try to get the GNOMEcc to get the information from the pilot and it doesn't respond. 

I kind of suspect I have a cradle probem and havbe the Device set to cradle /dev/pilot 57600 USB. I noticed in one section of GNOME help, it suggests I set this to /dev/usb, but that option is not on my Pilot Settings>Device tab.:confused: :confused:

---

### Post by trash on 2006-01-02
I just spent all night trying various howto's to get my brothers palm m130 working... The whole time trying I had the cradle plugged into a usb slot on the machine, just about to give up I for some reason decided to plug the cradle into the keyboard.. palm synced immediately! with /dev/ttyUSB0

dumb luck but it worked lol

---

### Post by waldorf on 2006-01-02
First. I would recommend backing up your palm someplace. I've found this process to be a bit risky the first few times and I've lost data. The other thing you can do would be to turn off all the conduits at first and then add them one synch at a time.

Second. Tell evolution to look for the palm at /dev/ttyUSB1. (i.e. the port should be set to /dev/ttyUSB1). That should do the trick

---

### Post by gdgardnerw on 2006-01-09
trash and waldorf, thank you both for your replies. I tried your suggestions to no avail. I am using a usb keyboard and optical mouse through a usb hub plugged into the lower usb socket in the iMac (333 MHz). Using /dev/ttyUSB0, nothing happens on the desktop, but the Tungstun indicates that it could not establish communication with the computer. When I change the device to /dev/ttyUSB1, I get the same error as before, i.e., 

WARNING: (gpilotd)
Unknown pilot - no pilots matches ID 2142999168. Use gnomecc to set pilot's ID.

This is the same error I received when I started this thread.

I have changed the pilot's ID to this number directly through gnomecc and I still get the same result. I have requested that gnomecc get the info from the pilot and it sets the id to 0 and then on the subsequent hotsync, it gives me the same error message state above.

I have plugged back in the old iMac keyboard and have done all of the above and get the same results, trying both /dev/ttyUSB1 and /dev/ttyUSB0

Thanks guys, for answering. Can you think of any more issues that may be involved here? Help!

---

### Post by dombleu on 2006-01-09
Ok this is not an answer to your case. But I just installed gnome-pilot-applet, follow the given instructions when running the applet for the first time and it syncs. But I have problems syncing my addressbook. But the calendar sync works fine.

It works with ttyUSB1. ( as usual )

---

### Post by chascon on 2006-01-12
I wrote a HowTo some time ago.  It a little out of date but can serve to double check a few points and perhaps find a workaround.
[http://www3.telus.net/public/lusseau/gnu-linux-ppc_docs/sync_with_Evolution.html](http://www3.telus.net/public/lusseau/gnu-linux-ppc_docs/sync_with_Evolution.html)
Chascon

---

### Post by Chriis on 2007-11-13
Here i'm using a palm Tungsten E and it sync well if i disable "TIME"  conduit,..if not it freeze   randomly at this point.

Chriis

Edit: Sorry, even with "TIME" conduit off, I've experienced freeze or connection lost at the end of sync'in, randomly.

---

### Post by alex2035 on 2007-11-13
My settings in case you find it usefull are a Palm TX synced in 7.10 , alternatively with Evolution and Jpilot. I use this configuration because I prefer Jpilot but evolution gives me a kind of nice backup and I can handle email addresses easily. When syncing to Jpilot I disable all Evolution conduits.
This Palm syncs via the usb: setting under devices perfectly. One more thing, Evolution doesnt like the EToDo sync, it will hang the process indefinitely but there is no data loss, I just disable it.

---

