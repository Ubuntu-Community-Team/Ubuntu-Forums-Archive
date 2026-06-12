---
title: "Error Messages: Breezy install on G3 (blue)"
date: 2006-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by heffo_j on 2006-04-23
g'day all,

I've upgraded to Breezy on the G3 but get the following re-occuring messages each time I try to upgrade:

postfix: sub process post-installation scriptreturned error exit status 1
mailx: depenency problems leaving unconfigured
mutt: dependency problems leaving unconfigured

Any help would be apprciated.

Also, when I boot I get a "locale" error:

locale: cannot set LC_ALL (TYPE/MESSAGES)  to default locale: so such file or directory


All help is greatly appreciated. I'm setting the MAC for my daughter to use.

regards
John

---

### Post by Rxke on 2006-04-23
Did you upgrade via the terminal or synaptic?
You might try sudo atp-get install mailx mutt    ; if there are dependencies, I think apt-get will try to solve these more efficient than the synaptic
might try to retry and install postfix via the same way too (maybe uninstall it first if it doesn't do anything.

about the locale, I'm not sure, anyone else?

---

### Post by heffo_j on 2006-04-23
Thanks, I'll give it a go. 

When I installed I initially used Synaptic; git stuck halfway and saw in the synaptic "details" screen the advice to try apt-get; which I did.

Anyway here goes

cheers
John

---

### Post by heffo_j on 2006-04-23
No luck,

It tells me that mailx and mutt are already the latest versions and that postfix is not configured.

I had a look at post fix.main.cf and it made no sense to me, How is this configured? I also tried to uninstall the mailx and mutt (intending to do a fresh install)  but I can't remember the terminal command for that. Perhaps Synaptic can do it??

Help appreciated.

John

---

### Post by Rxke on 2006-04-23
Yes, synaptic can do that, but I personally won't 'officially' say you to do so (because I know too little about breaking things... Or to much, depends how one looks at it ;) ) then afterwards you'll have to re-install it and hope it goes ok

re: postfix: normally in the terminal ```
sudo dpkg-reconfigure postfix
```   For further info maybe this can help: [http://www.postfix.org/basic.html](http://www.postfix.org/basic.html)

---

### Post by heffo_j on 2006-04-23
thanks mate,

I got onto it before your reply (impatience I guess) and a complete uninstalled in synaptic of postfix, mutt and mailx and then did a reinstall. Works fine now.

Thank you for your help - it put me on the right track.

Best regards
John

---

### Post by Rxke on 2006-04-23
Glad to be of any help, even if it was in an oblique way  (shouldn't try to use difficult words, as a non-native speaker, grin)

---

