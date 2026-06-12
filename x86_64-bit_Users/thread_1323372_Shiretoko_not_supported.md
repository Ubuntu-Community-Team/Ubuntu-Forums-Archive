---
title: "Shiretoko not supported"
date: 2009-11-11
forum: x86 64-bit Users
---

### Post by Oldhacker on 2009-11-11
Today, I attempted to access the Texas Department of Transportation website and its child links using Shiretoko 3.5.4. This site was just updated to a new interactive version. What I got was a message saying that my browser was not supported and telling me to use "Firefox" or "Internet Explorer." I tried Opera, and the site came through fine. Then, I tried it on the old Firefox 3.0.15 and that worked as well. What the incompatibility is lies beyond the scope of my knowledge. But, I hope that this is not a harbinger of more incompatibilities with this otherwise fine browser.

---

### Post by Oldhacker on 2009-11-12
I just downloaded Shiretoko 3.5.5 and the same incompatibility exists on the named site.

---

### Post by hkkea on 2009-11-12
try this:
1. open a new tab & type about:config in the address bar;
2. find an entry called 'general.useragent.extra.firefox';
3. change its value (should be 'Shiretoko/3.5.5') to 'Firefox/3.5.5'.
4. save it and try the website again........

---

### Post by Oldhacker on 2009-11-13
You did it! It works with the Texas Department of Transportation website!!!

I shall have to assume that any other sites that could not understand "Shiretoko" must be cured as well!

Thanks for your capable help

---

