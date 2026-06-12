---
title: "Forward emails to Exchange Server"
date: 2008-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by remedix on 2008-01-02
Hello All,

I just finished setting up a server with ubuntu 7.10 and also installed Sendmail when asked.

I will setup a php system there (custom made) that will send some emails messages to real (external) email addresses. 

For example the system will manage some users and these users will have their real email address stored in the database (mysql)

The problem now is that this system will co exist on a local domain controller along with an Exchange Server. I do not have access to either of them.

My question is:

How can I send emails efficiently without them leaving the Local Network and rerouting them back to the exchange? Do I have to use something else except sendmail? I don't want to have pop3 or smtp on that server, just forward the emails to the exchange and let that server handle them.

Any ideas?

---

### Post by dcstar on 2008-01-03
> **remedix said:**
> Hello All,

I just finished setting up a server with ubuntu 7.10 and also installed Sendmail when asked.

I will setup a php system there (custom made) that will send some emails messages to real (external) email addresses. 

For example the system will manage some users and these users will have their real email address stored in the database (mysql)

The problem now is that this system will co exist on a local domain controller along with an Exchange Server. I do not have access to either of them.

My question is:

How can I send emails efficiently without them leaving the Local Network and rerouting them back to the exchange? Do I have to use something else except sendmail? I don't want to have pop3 or smtp on that server, just forward the emails to the exchange and let that server handle them.

Any ideas?

I assume sendmail has a setting for an external relay, just use that.

---

### Post by remedix on 2008-01-09
Well, I am using postfix. I can send emails to gmail hosts but not on other hosts located in the network. 

For example the company has the domain xyz.com. I can send using postfix to any other address except mails to the xyz.com domain.  I have the 'relayhost' setting in postfix pointing to the exchange server. Is there anything else that i must do ?

Thank you

---

### Post by dcstar on 2008-01-09
> **remedix said:**
> Well, I am using postfix. I can send emails to gmail hosts but not on other hosts located in the network. 

For example the company has the domain xyz.com. I can send using postfix to any other address except mails to the xyz.com domain.  I have the 'relayhost' setting in postfix pointing to the exchange server. Is there anything else that i must do ?

Thank you

Well, you should be forwarding ALL mail to whatever system processes your mail, then it should take care of everything.

If you have made the mistake of setting your Ubuntu machine's domain name to the same as your main domain, then it may try to deliver them locally (to itself).

---

