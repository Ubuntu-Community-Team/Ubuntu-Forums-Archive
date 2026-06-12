---
title: "Upgrade a 7.04/32 to a 8.04/64"
date: 2008-05-10
forum: x86 64-bit Users
---

### Post by lefterist on 2008-05-10
Is it possible to upgrade a 7.04/32 to a 8.04/64 by using the CD or do I have to wipe everything clean?

---

### Post by jespdj on 2008-05-10
No, you cannot upgrade from 32-bit to 64-bit without re-installing.

---

### Post by Yellow Pasque on 2008-05-10
Save your /home folder. In fact, now is probably a good time to move your personal data (music, documents, etc.) to a separate partition.

---

### Post by Sef on 2008-05-10
> Is it possible to upgrade a 7.04/32 to a 8.04/64 by using the CD or do I have to wipe everything clean?

Before you upgrade or install **back up** your files first.

---

### Post by Zorael on 2008-05-10
Opinion, but either way you're much better off doing a fresh install. Backing up your /home is the important part; reinstalling applications is easy. Troubleshooting weird upgrade-related problems is not.

---

### Post by lefterist on 2008-05-10
Thank you all, I always liked the clean install myself with a backup/restore of home folders, even though its probably more time consuming. Is there an easy way to find the modified system files? Its a pretty old install and it has been continuously upgraded. I do remember customizing a few things here and there but I can't remember all of them.

---

### Post by drumsticks on 2008-05-10
You might want to backup /etc as well. This contains a lot of configuration options, such as X11 configuration, network configuration, hdparm, cron scripts, and the like. I*recommend not restoring the entire /etc directory in the new install, but you at least have a copy of the changes you made before.

---

