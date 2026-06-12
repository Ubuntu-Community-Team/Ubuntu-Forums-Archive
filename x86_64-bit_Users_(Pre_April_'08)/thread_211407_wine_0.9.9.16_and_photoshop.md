---
title: "wine 0.9.9.16 and photoshop"
date: 2006-07-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2006-07-08
hi manage to get wine working in amd64 cos i need dreamweaver and photoshop for work

dreamweaver is working but i can't get photoshop 7 now to work

it installs fine and even adobe imageready works! but not photoshop 7.0, can anyone help please - it worked no problemos in 32bit on my old system.

thanks for any help.

---

### Post by jonah1980 on 2006-07-09
went in wine irc room and got it working with some help by using this command:

WINEDLLOVERRIDES=wintab32=n wine "C:\Program Files\Adobe\Photoshop 7.0\Photoshop.exe"

---

### Post by struess on 2006-07-22
perfect!

i was having the exact same problem, and was just about to post about it...couldn't figure out why imageready was working while photoshop wasn't.  is there a sneaky way to not have to enter that command every time you fire up photoshop from the terminal?

edit:  thanks for posting the solution, too.  should be a requirement if you make a post asking a question :P

---

### Post by neorf on 2006-09-14
I've installed Photoshop 7 on kubuntu via wine, all ok. I try to start it with : "WINEDLLOVERRIDES=wintab32=n wine “C:\Program Files\AdobePhotoshop 7.0\Photoshop.exe”" but i've the following error:

wine: could not load L"c:\\windows\\system32\\\201cC:Program.exe": Module not found

Why? what can i do?
Thanks

neorf

---

### Post by kuja on 2006-09-14
Hmm, also  makes me wonder though, why such an old version of wine? (0.9.20 is out afterall)

---

### Post by coastdweller on 2006-09-19
.19 is in the repos though

---

### Post by kuja on 2006-09-20
Ahem, nothing is in the 64-bit repos.

---

