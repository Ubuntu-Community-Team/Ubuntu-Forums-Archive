---
title: "Wine Photoshop File Associations Not Working Properly"
date: 2011-07-15
forum: Wine
---

### Post by kendoori on 2011-07-15
Am running Photoshop CS2 under Ubuntu 10.10 with Wine 1.3.23.  I would like to be able to associate various file types with Photoshop.  I'd previously used this script:


```

 #!/bin/sh
QUICKPARLOCATION="c:\\Program Files\\Adobe\\Adobe Photoshop CS2\\Photoshop.exe"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0


```If I make this script be the custom command that's tied to "Open  With," Photoshop launches, but doesn't appear to be properly passing the  file name, so that file doesn't open. I'd had this working previously  under earlier versions of Ubuntu and wine.
  

P.S. please no commentary on using GIMP or other Photoshop alternatives

---

### Post by kendoori on 2011-07-16
See here: [http://askubuntu.com/questions/53220/open-with-wine-photoshop-not-working-properly](http://askubuntu.com/questions/53220/open-with-wine-photoshop-not-working-properly)

---

