---
title: "am i getting hacked?"
date: 2009-01-27
forum: x86 64-bit Users
---

### Post by theadmira1 on 2009-01-27
im still trying to get used to using Ubuntu for my everyday needs... but i opened up system log yesterday and noticed that while i wasn't home there was a lot of login attempts and such... so i checked again this morning after getting home from doing hw... and its the same... sooo im wondering... is someone trying to drop a virtual deuce on my system? or is this kind of activity normal? thanks!

[http://tinypic.com/view.php?pic=2cifpq8&s=5](http://tinypic.com/view.php?pic=2cifpq8&s=5)

---

### Post by jerome1232 on 2009-01-27
A) do you have ssh-server installed? If not then there's no way for someone to remotly log on to your system

B) I can't read what's in that pic for the life of me. Could you post it in a text file?

This should make a file containing the log in your home directory.

```
cat /var/log/auth.log > auth.log.txt
```

---

### Post by lisati on 2009-01-27
Anyone else at home who might be trying to use your machine without your permission? 
Is your internet connection active 24/7?

There shouldn't be many login attempts beyond what you do or approve yourself - any more than that is usually a sign of someone messing with your system or some kind of problem.

---

### Post by jolx on 2009-01-27
@jerome
if you click on the pic it should show a larger version

and they're all cron sessions, not that i know the significance of that

---

### Post by jerome1232 on 2009-01-27
[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

Cron is a time based task scheduler for linux, It's how you set things to automatically be run at specific time intervals. So they are probably just cron jobs running.

---

### Post by theadmira1 on 2009-01-27
good deal... thanks... how do i look at what is set on a scheduler?

---

### Post by theadmira1 on 2009-01-27
nvm just read that wiki page... thanks guys!!

---

### Post by estyles on 2009-01-27
Yeah, it looks like all cron sessions.  Cron is a daemon that you can set up to run processes at various times.  Have you set up anything to run like every hour?

(edit)Umm... ignore me.  Was gonna respond and then got caught up with some business and didn't reload before finishing my reply to see if someone had already answered.  =)

---

### Post by Insightfill on 2009-01-27
I periodically run the following:

cat /var/log/auth.log | grep -v "CRON" | grep -v "myname"

the "-v" filters out the CRON jobs and regular logins by me.  It allows me to see who's been doing what.  

There's a good article over at debian-administration on how to use IPTABLES to block multiple attempts to access a system. [http://www.debian-administration.org/articles/187.]("http://www.debian-administration.org/articles/187")  I've used the article to block my FTP port from these silly attempts.

An additional measure of protection comes from using non-standard ports.  For example: my logs used to be FULL of people turning dictionaries loose against my SSH port.  When I moved SSH to a different (weird) port, the attacks stopped.

---

### Post by vandorjw on 2009-01-27
if you think you are getting hacked why not turn on your firewall.

```

sudo ufw start

```

I am not 100% sure, but I believe it is installed by default, just not turned on. At least, that was the case for me. Ubuntu 8.10

---

### Post by jerome1232 on 2009-01-27
That in and of itself does nothing really, if you want iptables to actually filter traffic you have got to give it some rules.

to deny all traffic, you would do this (using ufw as the frontend)

```
sudo ufw default deny
```

---

