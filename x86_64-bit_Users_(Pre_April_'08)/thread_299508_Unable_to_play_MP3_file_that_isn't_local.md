---
title: "Unable to play MP3 file that isn't local?"
date: 2006-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by SJI on 2006-11-14
Hello,

I've just installed edgy64 and have everything ticking along just fine, with the exception on playing MP3s on remote shares. (It may effect other media types too but i haven't checked yet).

If i copy an MP3 file from the remote share and save it as a local file it plays fine, no problems. Move it back to the remote share and totem seems to try and do something with the file but only shows "buffering" briefly, and then shows "Paused".

The remote share is an SMB share on a windows machine.

Any clues anyone?

Ste

---

### Post by lazyart on 2006-11-14
This happens because nautilus can see it even though it isnt mounted.

First you'll want to be sure that samba is installed.  It may look like it is but it's not:

```
sudo apt-get install smbfs
```

Now mount it:

```
mkdir ~/music
mount -t cifs //server/share -o  username=windows_user_name_here,password=windows_password_here
```

If there is no password to access the share, eliminate the -o and everything after it.  Look in your home directory for the music folder and your stuff will be there.

This will only work for you and only during this session.  You can auto mount it by editing /etc/fstab and make it available to everyone... but get this part working and we can go forward.

I just learned this yesterday.  The circle of giving is complete. :)

---

### Post by SJI on 2006-11-14
Thank you for that Lazyart, that works as a quick fix.

In the long term i'd like to resolve whatever the underlying problem is.

I had Dapper running MP3 audio from remote shares just fine without the need to mount the share. The upgrade to Edgy took that install out and so here I sit with a shiny fresh install.

Ste

---

### Post by lazyart on 2006-11-14
Some players work, some don't.  XMMS wouldn't play my music files unmounted but rhythmbox would.  Totem seems to be like XMMS in that regard.  Are you sure you were using Totem in Dapper?

You can put that in your startup sessions and be done with it.

---

### Post by SJI on 2006-11-14
> Are you sure you were using Totem in Dapper?

Yes, definitely using Totem.

> You can put that in your startup sessions and be done with it.

If another user on the domain gives me rights to view his/her audio too i'd need to mount their share also. I'd end up with god knows how many shares mounted after a while.

Ste

---

### Post by RAOF on 2006-11-14
I'm pretty sure that this was a bug in Edgy Totem or possibly a bug in Edgy's gnomevfssrc GStreamer element.  It's fixed in Feisty atm, so it's entirely possible the fix will be backported to Edgy.  I'd check out launchpad.net if you want to see what's happening.

---

### Post by SJI on 2006-11-15
Fingers crossed it is backported to edgy :)

---

