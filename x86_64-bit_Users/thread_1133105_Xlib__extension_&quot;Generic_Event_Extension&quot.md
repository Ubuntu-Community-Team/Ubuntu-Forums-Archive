---
title: "Xlib:  extension &quot;Generic Event Extension&quot; missing on display &quot;:xxxx.0&quot;."
date: 2009-04-22
forum: x86 64-bit Users
---

### Post by Bloemetjesgordijn on 2009-04-22
High Guys

I am running Jaunty, when I go to console on my AMD + ATI machine I get the following message:
Xlib:  extension "Generic Event Extension" missing on display ":1035.0".
Xlib:  extension "Generic Event Extension" missing on display ":1035.0".
Xlib:  extension "Generic Event Extension" missing on display ":1035.0".
Xlib:  extension "Generic Event Extension" missing on display ":1035.0".
Xlib:  extension "Generic Event Extension" missing on display ":1035.0".

( I get them five times, dont know why)

On my other machine intel + NVidia (also Jaunty) I get no error messages.

I have googled around, but that did not help me.

Can someone give some pointers??

cheerz

Bloemetjesgordijn

---

### Post by Yellow Pasque on 2009-04-22
See if this helps:
```
sudo apt-get install libxcb-event0
```

---

### Post by Bloemetjesgordijn on 2009-04-22
> **Temüjin said:**
> See if this helps:
```
sudo apt-get install libxcb-event0
```

Thx
I runned the command, something was downloaded and installed

Tomorrow I will check if it helped I think I need to do a restart and I am going to be now.

cheerz
Bloemetjesgordijn

---

### Post by ergosteur on 2009-04-23
This error is flooding my terminal window in the "Distribution Upgrade" GUI. I'm running on an Intel/Intel system (yes, integrated graphics...). We'll see what happens on the upgraded system.

---

### Post by pbhj on 2009-04-24
I had the ["generic extension error" warnings in my upgrade]("http://alicious.com/2009/ubuntu-upgrade-intrepid-to-jaunty/") (see the last screenshot), but they didn't stop the upgrade nor do they appear to be a problem now I'm running on Jaunty (Ubuntu 9.04) .. YMMV.

---

### Post by clovis6780 on 2009-04-30
> **Temüjin said:**
> See if this helps:
```
sudo apt-get install libxcb-event0
```

This didn't help me. I continue to see 6 such messages, for example, when I run gedit. Once when I run glxinfo, which then responds:
```
$ glxinfo
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  156 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  11
  Current serial number in output stream:  11
```This is after having installed that library you mentioned.

Edit: I just noticed that this forum is for x86 64-bit users. So I guess it's worth noting that I'm running on 32 bits.

---

