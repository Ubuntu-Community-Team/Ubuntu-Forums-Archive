---
title: "Ho to preserve your repositories downloads."
date: 2006-08-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ausus on 2006-08-10
Hi All,

When you do upgrades on your software via repositories.
Question 1:
Ok my question when I have to re-install again.
Is their some means where I can prevent to download again, and rather patch from my backup.
Question 2:
Speaking of backups.
How is done.

So their are two question ask, within this post.

Reagards

---

### Post by louis_nichols on 2006-08-10
All packages downloaded for update are stored by defult in /var/cache/apt (I think I remember well - I am not at my ubuntu box right now). They are only deleted when you run "sudo apt-get clean". So the thing to do is to regularly backup that folder.

As for backing up the whole system, I would recommend [partimage]("http://www.partimage.org/").

---

### Post by Ausus on 2006-08-10
Hi louis_nichols,

Tnx for reply.

What I'm looking for; if HD packs-up.
How easy is to reinstall ubuntu without the many downloads you have to do.

What folders do you net to backup etc.
Basicly i'm looking for a guide.
I browsed through out the forms, but have not found any information.

Regards

---

### Post by louis_nichols on 2006-08-10
Maybe [this article]("https://help.ubuntu.com/community/BackupYourSystem") on the wiki is what you're looking for.

basically, backing up always depends on what exactly you want to... well, to backup. Many would just take care of backing up the home folder, where the personal data lies. The system can be re-installed at any time. Of course, this is not what you want if you need al the latest packages you've already downloaded and installed.

If you want to backup your whole system, to sort of freeze an image of it in time, then you can follow the instructions on the wiki or use partimage, which is a pretty good tool and relieves you of having to worry about what folders to backup. Instructions about what partimage is, what it does and how to use it are all found on their homepage.

---

### Post by Ausus on 2006-08-10
Hi louis_nichols,

I will be looking at this guide.
Tnx for the reply.

---

