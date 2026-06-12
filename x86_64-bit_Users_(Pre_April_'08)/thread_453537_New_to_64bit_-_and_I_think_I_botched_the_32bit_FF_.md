---
title: "New to 64bit - and I think I botched the 32bit FF install..."
date: 2007-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by T'sora on 2007-05-24
Hi guys! I've been using Ubuntu for about 9 months or so now, but have been at a bit of a status quo for a while, so I seem to have lost a lot of what I learned in the beginning. So I'm back to being a newbie. ;) 

Anyway, just yesterday I upgraded my system to a Core2Duo, so I figured I'd give 64bit a whirl. I read Kilz's Howto on installing 32bit Firefox and ran the script - and then I messed it up. When it asked me if I wanted to install the Flash plugin, I instinctively hit "y" instead of "1" for yes. From all appearances then, it skipped that part of the install. 

So I tried to follow the separate steps from the same howto to install flash on its own, and that doesn't seem to be working, either. I didn't get any errors using the manual walkthrough until I entered:

```
chown -R <username>:users /home/<username>/.macromedia
```
which gave me 
```
chown: cannot access `/home/myusernamehere/.macromedia': No such file or directory
```

I figured, well, worse comes to worse, sound won't work yet, but I can at least test flash. To test it, I went to youtube and it's telling me "Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player." So apparently I really botched the Flash somewhere, and I'm stumped.

Any outputs I can post that would help, just let me know! Help? Comments? Suggestions? :confused:

---

### Post by Kilz on 2007-05-24
> **T'sora said:**
> Hi guys! I've been using Ubuntu for about 9 months or so now, but have been at a bit of a status quo for a while, so I seem to have lost a lot of what I learned in the beginning. So I'm back to being a newbie. ;) 

Anyway, just yesterday I upgraded my system to a Core2Duo, so I figured I'd give 64bit a whirl. I read Kilz's Howto on installing 32bit Firefox and ran the script - and then I messed it up. When it asked me if I wanted to install the Flash plugin, I instinctively hit "y" instead of "1" for yes. From all appearances then, it skipped that part of the install. 

So I tried to follow the separate steps from the same howto to install flash on its own, and that doesn't seem to be working, either. I didn't get any errors using the manual walkthrough until I entered:

```
chown -R <username>:users /home/<username>/.macromedia
```
which gave me 
```
chown: cannot access `/home/myusernamehere/.macromedia': No such file or directory
```

I figured, well, worse comes to worse, sound won't work yet, but I can at least test flash. To test it, I went to youtube and it's telling me "Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player." So apparently I really botched the Flash somewhere, and I'm stumped.

Any outputs I can post that would help, just let me know! Help? Comments? Suggestions? :confused:

Rerun the script, it will just write over what was installed before.

---

### Post by T'sora on 2007-05-24
> **Kilz said:**
> Rerun the script, it will just write over what was installed before.

Ok, I just tried that, and still no luck with flash/java. I checked the about:plugins page, and it's not listing anything installed for Firefox. :confused: I checked through the howto, but I'm not getting any errors, just a lack of working flash. Is there a way to determine if the trouble is with flash or java, or both?

---

### Post by T'sora on 2007-05-24
Ok, I tried installing with Simple64, and that seems to have worked. Plugins page is now showing java and flash installed. Not sure if sound is working yet, as I've yet to hook up my speakers to the new system. I'll try that shortly.

Thanks for the great howtos, both Kilz and kuja!

---

