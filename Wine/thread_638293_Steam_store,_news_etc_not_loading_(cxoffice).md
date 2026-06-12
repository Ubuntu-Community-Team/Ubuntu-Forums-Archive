---
title: "Steam store, news etc not loading (cxoffice)"
date: 2007-12-11
forum: Wine
---

### Post by Jabb3r on 2007-12-11
I did manage to get it all working before when I installed everythin as root, but thats not good practise really, but now I get the program loading fine, but just blank whiteness everywhere theres supposed to be content. I figure it's a permission problem, I've tried to chmod the .cxoffice directory to 777, but still the same.

Any ideas?

Thanks

---

### Post by cogadh on 2007-12-11
You probably need to re-install the "CrossOver HTML Engine". That is the CX component that is used to display the Steam content and if Steam is not displaying content, the engine is either not installed or screwed up in some way. Re-installing may fix that.

---

### Post by Jabb3r on 2007-12-12
Thanks for the reply, will try yu suggestion and report back.

Edit:

I reinstalled cxoffice using sh install-script.sh instead of ./install-script.sh and it seeems to have done the trick. Thanks for your help, appreciated. :)

---

