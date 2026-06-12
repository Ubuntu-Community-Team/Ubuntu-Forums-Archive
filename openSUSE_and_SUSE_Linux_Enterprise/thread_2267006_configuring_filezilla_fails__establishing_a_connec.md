---
title: "configuring filezilla fails :: establishing a connection with SFTP fails all the time"
date: 2015-02-26
forum: openSUSE and SUSE Linux Enterprise
---

### Post by dilbert_one on 2015-02-26
hello and good evening dear Ubuntu-experts and fans, 


well i am struggling with the set up of FileZilla. Though it runs well on two other notebooks i stuggle to configure it on the third notebook. 

what happens: now i did a fresh installation on a third notebook - 
i installed opensuse 13.2 and then filezilla: all was totally fresh installed

I added a key  - and subsequently i wanted to try the whole thing: 


i want to do a connectino via a sftp-way. 
therefore i added the pub-key. - the one that is used on the other notebooks also

but i cannot establish a connection to the server. 

afterwards i tried to run a configuration-test.   the test that finally estabishes a connection to the filezilla-server.
this faield 

why -  what can i do now!?    					 										 										 										 					 					I need your help right now

love to hear from you:mad:

---

### Post by coffeecat on 2015-02-26
Yet again - tech support request, not a Cafe thread.

> **dilbert_one said:**
> 
i installed opensuse 13.2 and then filezilla: all was totally fresh installed


*Thread moved to **openSUSE and SUSE Linux Enterprise**.*

---

### Post by Habitual on 2015-02-26
Do you have root access to the target host?

If so,
ssh to the target host in the usual manner and get root, then issue this command from c-line.
 **echo "MaxAuthTries 10" >> /etc/ssh/sshd_config; service ssh restart**.

If no root access contact the sysadmin and ask them to do it.

"Configuration Test" What's that and how does that work?

---

