---
title: "WEP, Linksys, and an EEE"
date: 2008-04-28
forum: Wisconsin Team
---

### Post by admiralfreak on 2008-04-28
I bought an Asus EEE PC 4G and love it so far.  The problem that I've had with it is getting the WEP security to work.  I have it set in the linksys control panel to "password" (just as a test) and then when I go into the network settings in ubuntu, I put that in for the password and it doesn't work.  I have tried both ASCII and Hexidecimal format.  I'm wondering if it might have something to do with the version I'm using which is 6.06, but that is the only install disk that I have available right now.

Any help?  Thanks!

---

### Post by uberushaximus on 2008-04-28
If I remember correctly, and don't quote me on this, you might have to do a little research, but I think as far as networking goes, I think network-manager doesn't play the nicest on the older distributions. Hardy is a little funny yet at times, but it's worth an upgrade or three.

After all, it does this...
[IMG]http://imgs.xkcd.com/comics/zealous_autoconfig.png[/IMG]

---

### Post by admiralfreak on 2008-04-28
> **uberushaximus said:**
> If I remember correctly, and don't quote me on this, you might have to do a little research, but I think as far as networking goes, I think network-manager doesn't play the nicest on the older distributions. Hardy is a little funny yet at times, but it's worth an upgrade or three.


I did have the regular wifi working (with no encryption) and updated ubuntu and restarted.  Wifi doesn't work at all.  I'm downloading 8.04 right now, hopefully that will help.

---

### Post by Ek0nomik on 2008-04-29
What model is the Linksys router?

What kind of wireless card do you have?  (If you are unsure, post the output of the command below and post it here)

```
lspci
```

---

### Post by admiralfreak on 2008-04-30
Well, I d/l 8.04 and installed it.  I got the wireless working with this page: [http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to_install_Ubuntu_Hardy](http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to_install_Ubuntu_Hardy)

I then got the WEP working using the HEX password.  I forget where exactly I read it, but apparently different wireless cards/router manufacturers use different encrypting sequences for WEP so using the passphrase didn't work.

---

