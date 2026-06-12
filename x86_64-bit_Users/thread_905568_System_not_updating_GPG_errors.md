---
title: "System not updating GPG errors"
date: 2008-08-30
forum: x86 64-bit Users
---

### Post by Vashthe3rd on 2008-08-30
I've noticed that my system hasn't had updates recently. I moved to a new place and my net is provided by the school, which has alot of internet protection. When I do a apt-get update, it ignores a few repos, and after a while I get a

```
W: GPG error: http://playonlinux.botux.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B1F5957DE4946268
```
and
```
W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
``` twice
and 
```
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I have no idea what to do, and it's starting to have an effect on my computer, wine crashes during launch, I'm getting other update-related errors, etc.

---

### Post by cariboo on 2008-08-30
Why not go t0 playonlinux and redownload the key file.

Jim

---

### Post by Vashthe3rd on 2008-08-31
that seems to have fixed the GPG error, but I'm still concerned that my system update is ignoring a few repos. Anything I should be worried about?

---

### Post by Vashthe3rd on 2008-08-31
anything?

---

