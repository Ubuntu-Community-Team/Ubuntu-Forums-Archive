---
title: "Backup solution."
date: 2008-07-25
forum: x86 64-bit Users
---

### Post by Stele on 2008-07-25
Hi everyone! Hope everything is going well...

Let me explain the whole thing before even asking anything:
I'm currently using Ubuntu 8.04 (x64)on my office server the setup looks like this:

**sda**
[INDENT]/ <--- 30Gb
/home <--- 470Gb[/INDENT]
[B]
sdb[/B]
[INDENT]/home/backups <--- 500Gb[/INDENT]

Every employee has its own user on the server and access it from their windows workstation, all the files are stored on the server, that way they can access it from any workstation without any problem.

I've setup a cron job everyday at 7:30 pm to do a clamscan on all the files and after that, backup up everything to /home/backups. As you can see is a fairly simple setup. I've been using SimpleBackup to handle all the local backups but everytime I have to recover something is really slow.

We are now looking forward an Amazon S3 account to do offsite backups of all our files, the server will do local backup first and then upload changes to Amazon S3. Heck, we are even thinking on doing some ftp backups to our webserver.

So, after all this mumbo-jumbo you gotta be asking: What is exactly what I want since I've kinda figured out everything... Well no, I'm looking forward to replace simplebackup with something faster and easier to use/recover... I found TimeVault but since I'm running x64 the .deb wont install...

So here I am asking all of you:
Any ideas to solve my backup needs?
How would you do the backups?

Thanks in advance for all the help!

---

### Post by LoneWolfJack on 2008-07-26
I'm not sure what you are looking for, but did you try rsync?

---

