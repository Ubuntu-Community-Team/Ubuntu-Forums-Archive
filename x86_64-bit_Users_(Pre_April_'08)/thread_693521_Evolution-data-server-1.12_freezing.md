---
title: "Evolution-data-server-1.12 freezing"
date: 2008-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Freek07 on 2008-02-11
I don't know if it's related to x64 od evolution but it's really annoying - gaim (pidgin) sometimes freezes and to make it freeze it's enough just to change to another tab. Evolution also freezes at that moment.

When killing evolution-data-server-1.12 (I guess it respawns) everything starts to work, again.

Is there a known workaround?

---

### Post by someonestolemyname on 2008-02-11
I'm also having the problem with evolution-data-server-1.12. It freezes when I hit certain buttons, such as reply, prefs, etc.

Killing every process starting with 'evolution' then opening it again works to get it going again.

I'm using 32-bit, so presumably it isn't x64 specific.

I'm trying some things, will update if I find anything.

---

### Post by someonestolemyname on 2008-02-11
Reinstalling all of the components doesn't help.

Just saying so no one else goes through the trouble for no reason.

---

### Post by someonestolemyname on 2008-02-11
Ok, I think I found the problem. Do you have evolution syncing your contacts with Pidgin? It's in the options. I noticed it while running from the command line that it said it was syncing when it froze.

Since preferences wouldn't open, open 'gconf-editor', go to 'apps > evolution > autocontacts'. Uncheck 'auto_sync_gaim'. It *should work fine now*. This likely has to do with the fact I have like 2000 people in my buddy list, but it could be the same problem for you.

Good luck,

Daniel

---

### Post by techstop on 2008-02-13
I have the same problem on 32-bit gutsy, but do not have auto-syncing of contact with pidgin. Any other tips?

EDIT: I was using the junk filter with bogofilter plugin. I disabled the plugin and unticked the option to filter junk on each of my IMAP accounts and it seems the problem is fixed.

---

