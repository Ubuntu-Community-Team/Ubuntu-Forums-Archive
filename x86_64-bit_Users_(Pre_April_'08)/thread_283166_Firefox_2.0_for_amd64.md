---
title: "Firefox 2.0 for amd64"
date: 2006-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kilz on 2006-10-23
For those people who use my 32bit Firefox debs. [2.0 is on the howto]("http://www.ubuntuforums.org/showthread.php?p=1174435") thanks to [this article]("http://www.macworld.com/news/2006/10/23/firefox/index.php"). Since I redid the script a week or so ago, if you havent installed with the new setup you will have to rerun the install script. This is not a release candidate or beta, but the release of 2.0.

---

### Post by floydwaferfield on 2006-10-24
Awesome. I was just wondering though, how did you go about converting the .tar.gz to a .deb file? Just so I would know how to do something like that.

---

### Post by Kilz on 2006-10-24
> **floydwaferfield said:**
> Awesome. I was just wondering though, how did you go about converting the .tar.gz to a .deb file? Just so I would know how to do something like that.

You cant just convert it. You have to extract the files, then create a binary .deb file manualy.

---

### Post by kleeman on 2006-10-24
Thanks kilz! BTW the new script link in the howto is not up at present.

---

### Post by Kilz on 2006-10-24
> **kleeman said:**
> Thanks kilz! BTW the new script link in the howto is not up at present.

Thanks , it was a stupid typo. Its up now.

---

### Post by rogeriovinhal on 2006-10-24
Hey Kilz, the .deb 2.0 package is not installing here. It gives this error:

```

dpkg-deb (subprocesso): leitura curta em buffer_copy (não foi possível gravar para o pipe na cópia)
dpkg-deb: subprocesso paste retornou código de saída de error 2
dpkg: erro processando firefox32-2.0-ubuntu-amd64.deb (--install):
 leitura curta em buffer_copy (backend dpkg-deb durante `./usr/local/firefox32/firefox-bin')

```

It is in portuguese, but basically it is complaining about something like "short read in buffer_copy (not possible to record to the pipe in the copy)"

EDIT: Nevermind, corrupted download.

---

### Post by tomdkat on 2006-10-24
Any ideas on when 64-bit Firefox 2.0 will be available?

Peace...

---

### Post by Kilz on 2006-10-25
> **tomdkat said:**
> Any ideas on when 64-bit Firefox 2.0 will be available?

Peace...

Well that depends. If you are talking about the 64bit package that Ubuntu compiles from the 32bit Firefox code it shouldnt be a week or 2. If you are asking when there will be a 64bit code base that is compiled into a true 64bit application. I have no idea because the 64bit code doesnt exist.

---

### Post by tomdkat on 2006-10-25
> **Kilz said:**
> Well that depends. If you are talking about the 64bit package that Ubuntu compiles from the 32bit Firefox code it shouldnt be a week or 2. If you are asking when there will be a 64bit code base that is compiled into a true 64bit application. I have no idea because the 64bit code doesnt exist.Thanks!  I was referring to the former (Ubuntu 64-bit package).  :)

Peace...

---

### Post by JAPrufrock on 2006-10-25
Thanks for the howto- smooth install.  Oops... what happened to my colorful tabs?  And Fasterfox?  Looks like it's not compatible with Firefox 2.0.  Oh well- have to wait I guess.  My other add-ons worked, including del.icio.us (thank god). Even with the non-compatibility issue I still prefer Firefox 2.0.

---

### Post by Hendikins on 2006-10-25
> **Kilz said:**
> Well that depends. If you are talking about the 64bit package that Ubuntu compiles from the 32bit Firefox code it shouldnt be a week or 2. If you are asking when there will be a 64bit code base that is compiled into a true 64bit application. I have no idea because the 64bit code doesnt exist.

Hate to split hairs, but it is the same codebase, regardless of architecture. I've got a 64bit build waiting to land in Mozilla's /contrib/ right now...

For anyone wondering about extensions, the review queue for addons.mozilla.org is somewhere close to 200 right now, so be patient, the reviewers are working flat out :)

/me crawls back under his rock and gets back to work on the x86_64 section of PluginDoc...

---

### Post by Kilz on 2006-10-25
> **Hendikins said:**
> Hate to split hairs, but it is the same codebase, regardless of architecture. I've got a 64bit build waiting to land in Mozilla's /contrib/ right now...

For anyone wondering about extensions, the review queue for addons.mozilla.org is somewhere close to 200 right now, so be patient, the reviewers are working flat out :)

/me crawls back under his rock and gets back to work on the x86_64 section of PluginDoc...

That is kind of what I was saying. But the code as it is right now is optimised to 32bit. It can be built to run on a 64bit system. But isnt that different than code that is specificly written to take advantage of the 64bit processor? Wouldnt there have to be changes to the code?

---

### Post by Hendikins on 2006-10-25
> **Kilz said:**
> That is kind of what I was saying. But the code as it is right now is optimised to 32bit. It can be built to run on a 64bit system. But isnt that different than code that is specificly written to take advantage of the 64bit processor? Wouldnt there have to be changes to the code?

There has been some 64bit-specific work done, but there are still outstanding 64bit issues. There are only a few things that would get any real speed boost out of 64bit-specific code anyway.

---

### Post by kopilo on 2006-11-14
Any signs of that 64 bit package?

---

