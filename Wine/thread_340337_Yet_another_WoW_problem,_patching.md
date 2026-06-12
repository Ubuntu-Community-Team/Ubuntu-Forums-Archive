---
title: "Yet another WoW problem, patching"
date: 2007-01-17
forum: Wine
---

### Post by CJNyfalt on 2007-01-17
Hi,

I have a problem installing patch 2.0.3 for World of Warcraft.
The installer hangs displaying "Waiting for files to close..."
Does anyone know how to fix this?

---

### Post by Ferrat on 2007-01-17
> **CJNyfalt said:**
> Hi,

I have a problem installing patch 2.0.3 for World of Warcraft.
The installer hangs displaying "Waiting for files to close..."
Does anyone know how to fix this?

Yes this means you have Win NT or Win 98 choosen in Wine, just switch to Win XP then the files will free up (might need a restart but don't think so.

Always use win xp when running WoW stuff =)

---

### Post by CJNyfalt on 2007-01-17
No, that's not the problem. I'm already running Wine in Win XP mode.

---

### Post by hikaricore on 2007-01-17
> **CJNyfalt said:**
> No, that's not the problem. I'm already running Wine in Win XP mode.

Hmm... do you have read/write access to the files in question?

Sometimes people run installers, even installers through wine, with sudo then files from said installer end up being owned by root and not writeable to by a normal user.  Just a thought.

Good luck.

---

### Post by kcakalinuxnub on 2007-01-17
I had this problem a few days ago when setting up WoW.  All you need to do is set your windows to Windown NT 4.0.  It should update normally and you won't get the hanging files.

---

### Post by CJNyfalt on 2007-01-18
I have tried to look for files lacking write access and directories lacking executable access, no luck. I have tried to set wine to NT 4.0, no luck.

---

### Post by robglinka on 2007-02-17
I had the exact same problem. I fixed it by changing my default wine settings to Windows XP. It didn't work for me to just change the settings for the patch executable, I had to change the whole default.

Good luck!

---

### Post by Rskennan on 2007-12-19
To anyone who finds this thread via Google like I did, If nothing else seems to work, try robglinka's idea. I was pulling my hair out all night on this issue, and his idea worked perfectly. Thanks!

---

