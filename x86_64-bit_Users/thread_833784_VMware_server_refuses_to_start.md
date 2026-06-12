---
title: "VMware server refuses to start"
date: 2008-06-18
forum: x86 64-bit Users
---

### Post by tlages on 2008-06-18
I recently installed VMware server, but whenever I click the menu item for it, it refuses to load. It displays it's "loading status" in my taskbar, but never loads.

---

### Post by Kilz on 2008-06-19
> **tlages said:**
> I recently installed VMware server, but whenever I click the menu item for it, it refuses to load. It displays it's "loading status" in my taskbar, but never loads.

Did it ever start? if so have you updated the kernel? If you have reinstall it.

---

### Post by damvcoool on 2008-06-19
you don't have to re-install you need to run 
```

sudo vmware-config.pl

```

to recompile the kernel module.

---

### Post by Kilz on 2008-06-19
> **damvcoool said:**
> you don't have to re-install you need to run 
```

sudo vmware-config.pl

```

to recompile the kernel module.

Thanks, but the reinstall basically does the same thing I think.

---

### Post by tlages on 2008-06-19
Thanks I ran sudo vmware-config.pl but it still won't load. How would I go about re-installing it?

---

### Post by grg3 on 2008-06-19
> **tlages said:**
> I recently installed VMware server, but whenever I click the menu item for it, it refuses to load. It displays it's "loading status" in my taskbar, but never loads.





Open a terminal window and try to run vmware-server-console there. You may see error messages that will help determine the issue.

---

### Post by Keith Hedger on 2008-06-19
use this brill howto [http://ubuntuforums.org/showthread.php?p=5216334#post5216334](http://ubuntuforums.org/showthread.php?p=5216334#post5216334)

---

### Post by tlages on 2008-06-19
I got it fixed. Thanks though.

---

### Post by shanefitz on 2008-09-26
I am also having this problem with the vmware server console displaying the "Loading.." message and going no further.

How did you fix this?

---

### Post by uniko on 2008-09-26
You need to install with a patched installer (usually named vmware-any-any-update-xxx). Instructions can be found on the thread mentioned earlier or from vmware forums.

---

