---
title: "&quot;WINE 1.6&quot; still says &quot;Wine 1.5.28&quot;"
date: 2013-09-05
forum: Wine
---

### Post by Mint4Ever on 2013-09-05
I upgraded wine twice, once through the terminal, and once through software update both times it said it was wine 1.6, but when I check the version I have it still says 1.5.28.  do I have a bug? or is there something else wrong? and I tried restarting already

---

### Post by ian-weisser on 2013-09-06
wine 1.4.1 seems to be the most recent version in the Ubuntu repositories.
```
$ rmadison -u ubuntu wine
      wine | 1.1.42-0ubuntu4 | lucid/universe | all
      wine | 1.2.2-0ubuntu2~lucid1 | lucid-updates/universe | all
      wine | 1.4-0ubuntu4 | precise/universe | amd64, i386
      wine | 1.4-0ubuntu4.1 | precise-updates/universe | amd64, i386
      wine | 1.4.1-0ubuntu1 | quantal/universe | amd64, i386
      wine | 1.4.1-0ubuntu5 | raring/universe | amd64, i386
      wine | 1.4.1-0ubuntu7 | saucy/universe | amd64, i386
```

Did you add a PPA or third-party repository to get wine 1.5/1.6?
If so, please link to it.

Er, do be aware that non-Ubuntu-repository software (like PPAs) is, by definition, unsupported in this forum. Though we will try....

---

