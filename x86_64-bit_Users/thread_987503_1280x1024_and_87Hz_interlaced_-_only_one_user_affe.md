---
title: "1280x1024 and 87Hz interlaced - only one user affected"
date: 2008-11-19
forum: x86 64-bit Users
---

### Post by talz13 on 2008-11-19
I set up ubuntu on my parents new pc a while back, and ran into an interesting issue...  My user account and my dad's both work fine, but my mom's account is permanently stuck with a default 87Hz interlaced refresh.  I can go in there and use the nvidia settings to change it to 85Hz (non-interlaced), and it's fine for the rest of the session, but if she logs out and logs in again, or reboots, it's back to what it was before.

I have tried the write to x server config button in nvidia settings, run nvidia settings as root and done it, but it remains the same.  The screen resolution thing in system settings doesn't even show the right refresh rates for the monitor, so I never use that one anymore.

I suppose I could solve the issue by making a new user account, moving everything over to that new account, deleting her old account, and relabelling her groups, but that sounds like more work than is necessary to fix this.  Plus I still wouldn't have any idea why it happened in the first place.

---

