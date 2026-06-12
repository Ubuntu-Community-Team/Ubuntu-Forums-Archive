---
title: "Dovecot complaining:  Couldn't init INBOX: Mailbox isn't a valid mbox file"
date: 2009-02-13
forum: x86 64-bit Users
---

### Post by javahollic on 2009-02-13
Platform Intrepid, x86_64.
> ii  dovecot-common                             1:1.1.4-0ubuntu1.2                                   secure mail server that supports mbox and ma
ii  dovecot-imapd                              1:1.1.4-0ubuntu1.2                                   secure IMAP server that supports mbox and ma
ii  dovecot-pop3d                              1:1.1.4-0ubuntu1.2                                   secure POP3 server that supports mbox and ma

I post this under x86_64 as I get the problem on my current machine, it works fine on 32bit (and anoyingly, on an additional x86_64 machine).

If I start with an empty vmailbox folder, postfix happily dumps inbound mail from localhost to the virtual mailbox file 'inbox', dandy.  Now, I connect with Dovecot (forget the client, I even tried telnet), but every time I connect - and dovecot creates the .imap folder tree, it then complains:

> 
[email]root@drift:/var/mail/vhosts/xx.myco.net[/email]/shared# lFeb 13 20:27:06 drift dovecot: pop3-login: Login: user=<shared@xx.myco.net>, method=PLAIN, rip=192.168.1.24, lip=192.168.1.20
Feb 13 20:27:06 drift dovecot: POP3(shared@xx.myco.net): Couldn't init INBOX: Mailbox isn't a valid mbox file
Feb 13 20:27:06 drift dovecot: POP3(shared@xx.myco.net): Mailbox init failed top=0/0, retr=0/0, del=0/0, size=0


what gives?  Dovecot creates the file, yet can't read it.  Smells like a bug, open to suggestions :confused:

---

### Post by dcstar on 2009-02-14
> **javahollic said:**
> Platform Intrepid, x86_64.


I post this under x86_64 as I get the problem on my current machine, it works fine on 32bit (and anoyingly, on an additional x86_64 machine).

If I start with an empty vmailbox folder, postfix happily dumps inbound mail from localhost to the virtual mailbox file 'inbox', dandy.  Now, I connect with Dovecot (forget the client, I even tried telnet), but every time I connect - and dovecot creates the .imap folder tree, it then complains:



what gives?  Dovecot creates the file, yet can't read it.  Smells like a bug, open to suggestions :confused:

Check **all** the permissions on the tree/files - compare them with your working 32 bit system.

---

