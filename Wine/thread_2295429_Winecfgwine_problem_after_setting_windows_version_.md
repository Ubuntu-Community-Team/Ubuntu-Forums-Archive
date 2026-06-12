---
title: "Winecfg/wine problem after setting windows version to Win95 or similar old version"
date: 2015-09-18
forum: Wine
---

### Post by gargl on 2015-09-18
Short problem description.
OS: 12.04 (k)ubuntu

I am a heavy wine user and so far everything was working out almost flawlessly
until I made a change in the winecfg dialog switching windows from like Win7 to Win95.

After that I couldn't start the winecfg dialog nor any of my games.
As an error I recieved i.a.:
modify_ldt: Invalid argument

Without going into details, this is a known problem. For others, with other
solutions as well please have a look at:
[http://askubuntu.com/questions/483058/wine-stopped-working-how-do-i-re-install-w-o-losing-data](http://askubuntu.com/questions/483058/wine-stopped-working-how-do-i-re-install-w-o-losing-data)
[https://bbs.archlinux.org/viewtopic.php?id=182020](https://bbs.archlinux.org/viewtopic.php?id=182020)


My solution was given in (although it did has a different error message):
[http://ubuntuforums.org/showthread.php?t=163279](http://ubuntuforums.org/showthread.php?t=163279)

As stated there, go to ~/.wine/user.reg and add
```

[Software\\Wine] 
"Version"="****"

```

For Windows 7, which actually allowed my to start my
winecfg dialog again is: "win7".

If however the entry "[Software\\Wine]" does not exist,
create a backup file of your user.reg and simply add it.

It might be removed after the next winecfg start but
will still allow you to start it!

Thanks to the other authors and DoktorSeven as well!


(I hope it is ok, that I post this here as my idea was/is to allow other
users with probably the same problem access to my solution).

---

