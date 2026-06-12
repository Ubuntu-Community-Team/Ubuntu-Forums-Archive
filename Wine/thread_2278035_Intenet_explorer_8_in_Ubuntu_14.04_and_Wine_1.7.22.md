---
title: "Intenet explorer 8 in Ubuntu 14.04 and Wine 1.7.22"
date: 2015-05-13
forum: Wine
---

### Post by sergio-stateri on 2015-05-13
Hi,

I'm getting problems when trying to use Internet Explorer 8 on PlayOnLinux (Wine 1.7.22) when any site tries to use iframes. The following error is reported when a iframe is called: HTTP 501/HTTP 505. The link to iframe is: res://ieframe.dll/http_501.htm#[http://10.10.10.162/...and](http://10.10.10.162/...and) so on. This is the address that is shown when I check the properties of the page that can't be shown.

Thanks for any help.

Sergio Stateri Junior
[email]sergio.stateri@globo.com[/email]

---

### Post by dino99 on 2015-05-13
IE8 is one of the worst choice  [https://appdb.winehq.org/objectManager.php?sClass=version&iId=16041](https://appdb.winehq.org/objectManager.php?sClass=version&iId=16041)

---

### Post by sergio-stateri on 2015-05-13
dino99, I have tried with IE 7 and the same error is happing, I can't call a iframe in IE 7 too.
Does anyone know if is there any way to use iframes in IE7 or IE8 over wine / ubuntu? I can't change the system code because it's big legacy system, then I'd like a solution to work with iframes.

Thanks in advance,

Sergio Stateri Junior
[email]sergio.stateri@globo.com[/email]

---

### Post by Mark Phelps on 2015-05-13
Sorry, but there are a few MS apps that work poorly, if at all, in Wine -- and Internet Explorer is one of the most well known of them.

If you really need to use IE on a daily basis, you need to consider installing Windows in a VM -- and then, using a current version like IE 10, or even better, IE 11.

---

### Post by oldos2er on 2015-05-13
Moved to Wine.

---

