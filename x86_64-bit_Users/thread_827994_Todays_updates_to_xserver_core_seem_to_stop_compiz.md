---
title: "Todays updates to xserver core seem to stop compiz from working"
date: 2008-06-13
forum: x86 64-bit Users
---

### Post by dpstyles on 2008-06-13
Todays updates to xserver core seem to stop compiz from working .... for me anyhow.  The problem started after I updated and I removed a second monitor then rebooted.  Nvidia graphics card.  Now I can only use metacity :-(  Any ideas guys?  Please don't suggest re-install of Nvidia as it is a pain to do ....

Thanks

---

### Post by Kilz on 2008-06-13
> **dpstyles said:**
> Todays updates to xserver core seem to stop compiz from working .... for me anyhow.  The problem started after I updated and I removed a second monitor then rebooted.  Nvidia graphics card.  Now I can only use metacity :-(  Any ideas guys?  Please don't suggest re-install of Nvidia as it is a pain to do ....

Thanks

I installed the same xserver update and still have compiz. It is more likely that your removing the monitor. I think you already know what most people will recommend by your last sentence. Reinstalling the nvidia drivers would be the first step.

---

### Post by philinux on 2008-06-13
Instead of reinstalling nvidia someone suggested this, following a kernel update. i haven't tried it yet.

sudo nvidia-installer --update

---

### Post by dpstyles on 2008-06-13
Thanks guys, I did the nvidia re-install and things came back to life.  I'm sorry I didn't try philinux suggestion first - but i'll try it if it happens again.

Is there a known issue with nvidia and unplugging a second screen?  I'm running ax XPS m1330.

Thanks for all your help

Duncan

---

