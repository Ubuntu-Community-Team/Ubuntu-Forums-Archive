---
title: "wine - paste problem in powerpoint 2003"
date: 2008-05-19
forum: Wine
---

### Post by pietro2580 on 2008-05-19
Dear all,

When I try to paste pictures in Powerpoint 2003, I got the error: 
"The server application, source file, or item can't be found, or returned an
unknown error.  You may need to reinstall the server application."
However, pasting pictures in Word does not give any problem. Does anyone have an idea what is going wrong?

ubuntu 8.04
wine 1.0-rc1
MS Office Professional 2003

Thanx!

---

### Post by kalyp on 2008-07-23
Hello Pietro,

I'm having exactly the same problem, and cannot find the way to correct it which is kind of annoying...
Did you figure out something?????
thanks!

---

### Post by RealG187 on 2008-07-24
How did you even get MS Office to work?

---

### Post by kalyp on 2008-07-24
> **RealG187 said:**
> How did you even get MS Office to work?

I didn't have any problem with that, and word and excel work perfectly fine for instance, for now at least. I know that office XP crashes though (impossible to install it, that's said on the official wine website) but Office 2003 is OK. The main startup.exe of the CD didn't make it (it couldn't find the one in the directory OFFICE) but launching directly the startup.exe in that folder works out.

---

### Post by pietro2580 on 2008-07-24
Hi Kalyp,

I didn't find a solution. I found on the web that it might be due to the clip board (the "server" mentioned in the error message) that is not performing well, however I couldn't solve the problem. Even a full re-installation of wine and office 2003 didn't do solve the problem.
Maybe report this as a bug?

---

### Post by balak on 2008-09-24
Did you report this as a bug? Can you send me the bug number.

I am facing the same issue. powerpoint w/o copy/paste is useless for me..

---

### Post by kalyp on 2008-09-24
Hi,
no I'm sorry... if you have time for that that would be great :)

---

### Post by kaspar_silas on 2008-11-10
Did anyone find a solution to this problem?

---

### Post by LepeKaname on 2008-12-12
Same problem here with:
Ubuntu 8.10 and Xubuntu 8.10
I installed the trial version of Crossover (Codewave) and the problem persist.
I downloaded Office 2003 SP3 patch and it didn't solve the problem...

If someone find a way to make it work, please post it here.

Thank you.

---

### Post by balak on 2009-01-28
Here's the bug report:
[http://bugs.winehq.org/show_bug.cgi?id=15401](http://bugs.winehq.org/show_bug.cgi?id=15401)

Please add your comments so that we can get the bug resolved sooner.

Thanks!

---

### Post by LepeKaname on 2009-05-26
I tested this issue in wine svn version 1.1.21 and finally was solved. No more copy-paste problems within PowerPoint...however still some minor problems between applications (from PowerPoint to Word, etc...).

---

### Post by LepeKaname on 2009-05-26
Do we mark this as solved?

---

### Post by pietro2580 on 2009-05-27
Indeed,
I can confirm that with wine 1.1.22 (and apparently also 1.1.21) this issue is solved.
I will also report this on the bugs-site of wine.
Thanks all for your input.

---

