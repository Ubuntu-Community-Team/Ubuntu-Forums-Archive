---
title: "[SOLVED] Evolution 2.22.3.1 just stopped sending"
date: 2008-09-18
forum: x86 64-bit Users
---

### Post by smoothcne on 2008-09-18
Last Sunday, Evo just quit sending outguing messages. I've uninstalled, reinstalled, blew away the hidden directory in my home folder.

Hell I even installed Thunderbird and it wont send either.

Provider is Comcast, of course they are clueless...

Is anyone else having trouble?

Thanks,

JJ
:confused:

---

### Post by Thelasko on 2008-09-18
Your email provider is Comcast?  Did they suddenly start using encryption on their email accounts?  Lot's of providers are going that way.

---

### Post by smoothcne on 2008-09-19
Well, I found out that Comcast changed the SMTP port number to 537.

Never notified a soul.

---

### Post by Thelasko on 2008-09-22
Do you mean 587?  That's the standard port for encrypted SMTP, not 537.

Most providers have about a 6 month switch over period.  For every email you send on the incorrect port, you get a message to change your ports.  I'm surprised they didn't notify you.  Perhaps it was blocked by a SPAM filter.

---

### Post by asmiller-ke6seh on 2008-10-19
My ISP is Comcast (yeah, it sucks) and all of a sudden, I could no longer send email from my system, and my wife's system. Yeah, they changed to Port 587 ... that's the port used for encrypted email for better anti-spam security.

Here's how I did it:
EDIT menu, select PREFERENCES. From the PREFERENCES dialog, click the EDIT button. Click on the SENDING MAIL option tab. Under SERVER CONFIGURATION click on the selection box "Server requires authentication" and in the SERVER edit box, where the Comcast SMTP server address is listed (mine says "smtp.comcast.net") at the end type :587 so that it might read:

smtp.comcast.net:587

Click OK, and then CLOSE, and all should be fine - send that test email back to yourself, and see if this works for you.

---

### Post by Baloofalo on 2008-10-21
> **asmiller-ke6seh said:**
> 
Here's how I did it:


Solution worked like a charm for me, thanks. 

Just COMPLETELY switched from Win to Ubuntu, so far this issue was my only regret.

---

### Post by dcstar on 2008-10-21
> **smoothcne said:**
> Last Sunday, Evo just quit sending outguing messages. I've uninstalled, reinstalled, blew away the hidden directory in my home folder.

Hell I even installed Thunderbird and it wont send either.
.........

You already have a solution, but for anyone else who comes across this thread the first step for **any** e-mail sending problems is to open a terminal and:

**telnet *smtp-server-address* 25**

If you get a response then you know the path to Port 25 from your system is ok and you can start looking at your own software as the problem. If it does not connect then you have a basic networking issue (like the wrong port) and you can then head down that path.

---

### Post by smoothcne on 2008-10-25
Thanks for that great advise, I never thought about checking it that way!
Smooth

---

