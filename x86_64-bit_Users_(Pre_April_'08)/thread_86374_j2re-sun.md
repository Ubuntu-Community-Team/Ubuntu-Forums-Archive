---
title: "j2re-sun"
date: 2005-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by mr.p on 2005-11-05
Everytime I try to make a .deb package I get this error...

```
nathan@greed:~/Downloads$ fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXFZhajF
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

```

How can I fix this? I have java-common, etc...

---

### Post by riggsd on 2005-11-05
You're posting in the AMD64 forum, yet that command line is for the i586 (32 bit) JRE. Is this a mistake or are you posting in the wrong forum?

It looks like it *should* work, as the file name matches the regex in [COLOR="DarkRed"]/usr/share/java-package/sun-j2re.sh[/COLOR]: "[COLOR="Red"]jre-1_5_0_"[0-9][0-9]"-linux-i586.bin[/COLOR]". If you really are using the AMD64 distribution, your JRE download should match this regex: "[COLOR="Red"]jre-1_5_0_"[0-9][0-9]"-linux-amd64.bin[/COLOR]".

If nothing else, I know the J2SDK builds properly with make-jpkg, perhaps download and try it - it includes the JRE as well as the dev environment.

---

