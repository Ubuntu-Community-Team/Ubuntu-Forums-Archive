---
title: "gam_server with samba on dapper64 server?"
date: 2006-08-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by h0g on 2006-08-05
Pardon my potential mis-filing of this post...

I've got an AMD64 system acting as a file server for several XFS file systems for users on my LAN via samba.  My only complaint is that without famd available, the directories don't update very quickly to show changes in the file structures for the clients.

After reading the gamin documentation, I see one of the main "features" that differentiate it from famd is that gam_server is intended to be launched "per user", but the nature of smbd seems to make this difficult.

Does anyone out-there in ubuntu-server land have any suggestions as what might be done here?  I'd suspect that people running IMAP servers might want some similar functionality -- or have you simply hard wired a hook into gam_server for your imap-daemon's user?

---

