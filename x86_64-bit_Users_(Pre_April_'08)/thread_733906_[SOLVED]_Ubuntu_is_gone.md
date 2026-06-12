---
title: "[SOLVED] Ubuntu is gone"
date: 2008-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by reery on 2008-03-24
Hi there,

I'm working for a long time with Ubuntu 64 and I've never seen such an ungly bug:

A day ago I forced a shutdown (by pressing the power-switch) because Ubuntu was taking way too long to shutdown (over 1 minute)... and somehow I wanted to go to bed at this moment.

The next day something very ridiculous showed up:

Ubuntu won't boot anymore. The whole system was gone. This is the error:

```

modprobe: WARNING: Error inserting iwlwifi_rc80211_simple.ko lib/mod/2.6.xxx/ubuntu/wireless/iwlwifi/mac80211/iwlwifi/ 
```

There are two files in this folder (iwlwifi_rc80211_simple.ko and iwlwifi_mac80211.ko). The error message says that Ubuntu can't load them because of an "unknown symbol in module" and so on.

By pressing Crtl+Alt+Del Ubuntu will load further till the login-screen (not the one from the graphical interface). When I login I can't create any data because the system says "read only system". I can't even start gdm or anything else.

With a small workaround it is possible to write on the harddisk: remount / with rw-rights.

But the error is still there: I can start GDM now, but the desktop is not mine (looks like a completly new user), the mouse and most of the programms from Gnome don't work.

Actualy the whole system is gone just because of the forced shutdown. Why is this? Why I can't find anything to solve this problem?

Do I have to reinstall Ubuntu? I fear the bug will even occour with the reinstalled Ubuntu...

Thanks for all tips solving this problem :)

---

### Post by |2A|N on 2008-03-24
My grub is missing and now I have to switch between both my hard drives boot up sequence now in the bios to start either Ubuntu or Windows I dunno if this is related or not but wanted to shed some light on it. I am using Ubuntu Hardy Heron 8.04 x64.

---

### Post by reery on 2008-03-24
My problem's got solved.

I chatted with a nice person on the #ubuntu IRC-Chat and he told me that my harddisc may be damaged.

And it was. I ran fsck a load of times and finally I was able to boot it.

---

