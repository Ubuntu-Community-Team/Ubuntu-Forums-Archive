---
title: "wow 2.2.3 patch and wine not getting along"
date: 2007-10-10
forum: Wine
---

### Post by saltedfish on 2007-10-10
Hi. Tried posting in the WoW howto, but figured I'd try out here too, since people seem to ignore my posts.

Ever since I downloaded the 2.2.3 patch, wine complains about not having enough space to install the patch on the harddrive. What gives? Wow runs just fine, except for the not-being-patched part. Im thinking some sort of allocation error? cause its got space to spare...

please someone respond..

---

### Post by hikaricore on 2007-10-10
WoW unpacks it's mpq data files when patching sometimes and can take up double the space it normally takes.
Not sure if this will help, but how much drive space do you have exactly free?

---

### Post by saltedfish on 2007-10-10
> **hikaricore said:**
> WoW unpacks it's mpq data files when patching sometimes and can take up double the space it normally takes.
Not sure if this will help, but how much drive space do you have exactly free?

df -h yields:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              75G   32G   44G  42% /
varrun                506M  112K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  124K  506M   1% /proc/bus/usb
udev                  506M  124K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1             373G   82G  291G  22% /media/sdb1
/dev/sdc1              75G   32G   43G  43% /media/WD Passport
```

i think that means I have 58% free. I could be, and prolly am, wrong.

---

### Post by saltedfish on 2007-10-10
bump for reply... i got one reply.. maybe i can net another..

---

### Post by sunfire on 2007-10-11
Have you read / try this ? 
This is normal used to Install-error, but may work this proplem too.

-----------
Not Enough Hard Drive Space error 

If you experience this, you need to open regedit and change the following values: 
TEMP set to \ instead of the current setting. 
TMP set \ instead of the current setting. These settings can located in HKEY_CURRENT_USER\Environment.

----------------
Copy from: [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

---

