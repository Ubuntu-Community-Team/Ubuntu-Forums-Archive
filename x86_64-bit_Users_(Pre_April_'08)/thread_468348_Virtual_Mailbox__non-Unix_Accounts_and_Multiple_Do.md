---
title: "Virtual Mailbox / non-Unix Accounts and Multiple Domains ... help please"
date: 2007-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by franko54 on 2007-06-08
Hello All,

Well, I've been searching the Debian, Ubuntu, and postfix docs (especially the Ubuntu Community page on Virtual Mail - dovecot), and I can't seem to find a clear answer to this problem.  So, I'll illustrate (in depth as possible) here.

**Problem:**  We have a dedicated server, running ubunu 6.04 which we share among a few sites.  Recently, we have tried setup postfix to handle our emails, but we can't seem to set it up correctly.  Originally, we had postfix with TLS protected smtp and dovecot running fine.  But, we have discovered that it's not feasible to have each email account have a linux account, so we needed to setup virtual mailboxes, and that's where the problems started.

**What we are trying to do:**

*Setup postfix and dovecot, to handle email. (pop3, imap, imaps, and smtp).
*Use Postfix Virtual Mailboxes in Maildir format, with non-Unix accounts.
*Allow for TLS with SMTP.
*Allow for SMTP to listen on both ports 25 and the submission port 587
*Ideally, use sasl2, or something similar to allow for encrypted passwords, i.e. DIGEST_MD5, rather than PLAIN or LOGIN authentication mechanisms.
*Ideally setup postfix/dovecot to use a mysql database to handle username/password lookups.


**What was tried:**

We tried using sasl2, according to the postfix and ubuntu docs, but smtp would not authenticate.  We tried using saslauthd, but we could not get non unix accounts to authenticate, even though we had a plain text password list (and we did run postmap on it).  Only those with linux accounts could authenticate.  We setup virtual mailboxes, and we could receive mail for some domains, but not all.

More can be explained further.  Just ask.

**We need help**

So, I am asking if someone would mind putting together a little tutorial on how to setup what we are trying to do, in Ubuntu.  I know that it's a lot to ask, but such kindness would really put an end to this headache that several days of searching and trying have caused.

Many thanks in advance.


Regards.

franco54

---

### Post by VorDesigns on 2007-06-12
Hi,

I just set up a postfix+dovecot+amavis+mysql+(has spamassin but) installation using [Run your own virtual mail server using Ruby on Rails and...](http://ubuntuforums.org/showthread.php?t=398866).

I wanted to use TLS/SASL authentication and I think I have it working correctly although I use PLAIN Login authentication, not Digest MD-5.  I am pretty sure that the SMTP session is encrypted with clients.

It took me a while to figure it out and I know part of my main.cf is wrong.

However, based on iinstructions in the Postfix.org documentation for SASL dovecot here [Dovecot SASL configuration for the Postfix SMTP server]("http://www.postfix.org/SASL_README.html#build_dovecot"), I was able to enable TLS/SASL authentication to relay mail.

Please note that the steps I took near the end of the document as of last night 06/11/2007, are raw and I know that some of the annotations in my main.cf are probably wrong.

My next step is to see about imap because I'm considering using horde imp since I'm familiar with the framework from old Gallantry Gallantweb boxes.

Anyway, take a look at the [Run your own virtual mail server using Ruby on Rails and...](http://ubuntuforums.org/showthread.php?t=398866) see if that helps.

The primary author wasn't too sure about the smtp side and I worked on it over the last several days so most of the posts specific to smtp are by me over the last week.

Good luck and post more questions in the [Run your own virtual mail server using Ruby on Rails and...](http://ubuntuforums.org/showthread.php?t=398866) thread, I'm watching it.

---

