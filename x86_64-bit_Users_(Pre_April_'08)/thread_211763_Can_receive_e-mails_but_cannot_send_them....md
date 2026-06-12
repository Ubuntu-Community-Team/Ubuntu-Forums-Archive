---
title: "Can receive e-mails but cannot send them..."
date: 2006-07-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by cshylton on 2006-07-08
After upgrading to Drapper I no longer can send e-mails. I can receive them and surf the internet but not send them. I have configured my machine several times and I always get the error: Helo command failed..connection reset by peer. When I try to send an e-mail, instead of sending it, it immediately is sent to my outbox folder. In the account editor and in the senting e-mail folder, I have the server as SMTP and the server config. as SMTP.and my e-mail address. Does anyone know what triggers this error?

---

### Post by hajk on 2006-07-09
> **cshylton said:**
> After upgrading to Drapper I no longer can send e-mails. I can receive them and surf the internet but not send them. I have configured my machine several times and I always get the error: Helo command failed..connection reset by peer. When I try to send an e-mail, instead of sending it, it immediately is sent to my outbox folder. In the account editor and in the senting e-mail folder, I have the server as SMTP and the server config. as SMTP.and my e-mail address. Does anyone know what triggers this error?

There must be an SMTP server somewhere, like "smtp.your.isp", where you have sending priveleges (perhaps even password protected). Your email address is not a correct SMTP server. Just ask your ISP what the name is of their SMTP server. 

The SMTP server is just the counterpart of the POP server (probably something like pop.your.isp or mail.your.isp).

---

### Post by cshylton on 2006-07-09
My mistake. Its not my e-mail address. It is my server name which is smtp.frontiernet.net and this is correct according to my provider. They do require authentication by password so I chose login since password isn't listed under sending e-mail. It is however listed under receiving mail. 
Any help to resolve this would be much appreciated.

---

### Post by Phil196949 on 2006-07-16
I am having the same problems as well. Can't send emails.

---

