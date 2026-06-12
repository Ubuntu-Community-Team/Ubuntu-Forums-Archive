---
title: "vmware + likewise-open  help"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by nullness on 2008-04-25
Hello,

I upgraded to Hardy x64 yesterday and I realized that vmware will not authenticate against AD since the pam module for likewise-open is 64-bit and vmware-authd is 32-bit.  VMware uses its own PAM modules in its /usr/lib directory, I was wondering if dropping a 32-bit version of likewise-open PAM module in the vmware directory and changing its pam.d settings would work, or if anyone else had come up with a work-around for this issue?

---

