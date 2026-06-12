---
title: "Getting Huawei usb modem to work. Need help!"
date: 2008-10-06
forum: x86 64-bit Users
---

### Post by khelben1979 on 2008-10-06
How do I setup a Huawei usb modem (model E220 HSDPA) together with Ubuntu 8.0.4? The modem is supposed to be able to use a 3G connection.

Platform: 64bit version of Ubuntu.

Fast help appreciated.

---

### Post by GeorgeVita on 2008-10-09
Hi,
there are many ways to "connect" using this modem (wvdial, network manager, other specific s/w as betavine). Have you try anything?

You can find a lot of info at "Huawei e220 USB modem for beginners"
[http://ubuntuforums.org/showthread.php?t=843973](http://ubuntuforums.org/showthread.php?t=843973)

or try configuring (and using) the wvdial:
post#2 at [http://ubuntuforums.org/showthread.php?t=909936](http://ubuntuforums.org/showthread.php?t=909936)
howto at: [http://forum.huawei.com/jive4/thread.jspa?threadID=322982](http://forum.huawei.com/jive4/thread.jspa?threadID=322982)

Post any questions or 'error' messages to follow up.
Regards
George

---

### Post by khelben1979 on 2008-10-09
I have followed the guide.

So far the Ubuntu system can connect with the modem in the way that I see that the light on the modem is not flashing, which is, according to my brother showing that it has access to the modem.

My next step will be to install a Network manager in accordance with this link: [http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059)

It remains to been seen if he has the patience to wait for this solution.

I also noted down that I might haveto edit all instances in the /etc/dbus-1/system.d/nm-* and NetworkManager.conf to allow instead of deny to get this to work correctly.

If you or anyone has any more tips I'll be interested. I hope to be able to test this in a few days.

---

### Post by costre on 2008-10-09
Just wanted to say that I tried to configure a friend's laptop today to run ubuntu, using his Huawei e220 modem for Internet through a Tele2 3G-connection. 

There had been tons of preparation, since I heard it could be a hassle to get the modem to work, and without Internet, it's even worse, but I digress ...

After installing Ubuntu and installing all important updates through synaptic, I plugged the modem in, and voila! It autodetected, autoinstalled, all i had to do was put in a phoney username ("Username"), and password ("password"), configure the PIN, and I was in! 

Now all I have to do is get his wine to manage his printer, after that he can leave Windows behind! :)

---

### Post by GeorgeVita on 2008-10-09
Hi costre,
can you give some details? The version of Ubuntu is 8.04? Did you download Network Manager 0.7? The connection was via network manager and finally the Firefox starts Online automatically?

Also a note for khelben1979: Steady led at the modem means "connected" to the internet in HSPA when color is light blue, 3G when it is blue and 2G (GPRS) when it is green.

---

### Post by costre on 2008-10-10
Sorry, I guess I forgot to mention I downloaded the beta of Intrepid for x86. So far, a really, really nice upgrade! (So, Compiz appearantly bugs a bit, but who cares .. cosmetics :) )

---

