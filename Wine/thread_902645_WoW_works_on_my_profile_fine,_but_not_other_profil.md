---
title: "WoW works on my profile fine, but not other profiles!"
date: 2008-08-27
forum: Wine
---

### Post by Maelgwyn on 2008-08-27
Hi guys,

I originally had wow in my home folder [/home/nik/Apps/World of Warcraft], but when the other users on my pc tried to access it, WoW would be amazingly unresponsive and 'jerks' around in 5 second blocks...

So I tried moving it to /opt/World of Warcraft and setting a few permissions like so:
```
sudo chgrp wowplayers /opt/path/to/wow

sudo chmod g+rwx /opt/path/to/wow
```

It *still* didn't work, so I modified the users' accounts to allow them to "Administer the system" as this was pretty much the only difference in our accounts.

Now I'm stuck! Please help :(

---

### Post by Thelasko on 2008-08-28
> So I tried moving it to /opt/World of Warcraft and setting a few permissions like so:
That doesn't sound like a good idea
> It *still* didn't work, so I modified the users' accounts to allow them to "Administer the system" as this was pretty much the only difference in our accounts.
That doesn't sound like a good idea either.

Let's look how Wine works.  When you install Wine and run winecfg, it creates an artificial C: drive, complete with an entire file system, settings, and registry.  That artificial C: drive is located in your /home directory.  In your case it would be in "/home/nik/.wine".

I have never played WoW, but I'm guessing that when you installed it, you made some registry or settings changes, and those changes were saved to "/home/nik/.wine".  That folder is only accessible to username=nik.  Therefore, when other users try to play WoW, they don't have those settings.  All you should have to do is change those settings on the other users' accounts and everything should work fine.

---

### Post by Maelgwyn on 2008-08-28
I hadn't even thought of that! I guess I'll try winecfg to see if that helps ^.^

---

