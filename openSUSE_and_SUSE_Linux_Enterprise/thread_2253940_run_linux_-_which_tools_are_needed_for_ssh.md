---
title: "run linux - which tools are needed for ssh"
date: 2014-11-23
forum: openSUSE and SUSE Linux Enterprise
---

### Post by dilbert_one on 2014-11-23
hello dear linux-friends


run opensuse 13.2 - which tools are needed for ssh

can i install it via yast 

love to hear from you 

greetings

---

### Post by bashiergui on 2014-11-23
You can probably install it via yast.

You need to have an ssh server running on the computer you want to connect to. You install the ssh client on the computer you'll use to connect. In ubuntu the ssh client is installed by default.

---

### Post by coffeecat on 2014-11-23
*Thread moved to **openSUSE and SUSE Linux Enterprise**.*

---

### Post by QIII on 2014-11-23
Hello!

OpenSSH is installed by default in openSUSE, too.  

If you don't want to do the configuration via the command line and would prefer to use the YaST configuration module for ssh, you'll need to install yast2-sshd.

It's been a while since I fiddled around with ssh on openSUSE, so I don't know if I can be of much help beyond that.  

Cheers!


Edit:  I fired up an openSUSE machine and did not find yast2-sshd.  Looks like that's not the tool any longer.  Give me a bit to poke around.

Edit:  Hmmm...  Can't find it, even though it is still referred to in the [documentation.]("http://doc.opensuse.org/documentation/html/openSUSE_113/opensuse-security/cha.ssh.html#sec.ssh.impl")

---

### Post by dilbert_one on 2014-11-28
hello dear** bashierqui, bill and coffeekat, and qIII**

 
first of all - many many thanks  for the quick reply  

  

  
 well what i want to do is the following:

my friend adminstrates a server that i am having several websites on.

he installed webmin and now i need access on this webmin that is available here www2.myhost.org:6677

unfortunatley the dns does not resolve the ip adressbook

so my friend argued that we  have to port forward to the site... - in other words to tunnel my computer to the server.

i am on opensuse 13. 1 and have enabled ssh
furthermore i have installed putty.


well i  can run things from command line.

eg, run ssh for port forwarding to a server:

this command is workin;

ssh -p123 -L 2233:127.0.0.1:2233 [EMAIL="vhost@www2.myhost.org"]vhost@www2.myhost.org[/EMAIL]


but i get asked for the public key:

(ECDSA) to the list of known hosts. Permission denied (publickey).

well how to add the (public) key -

a either on command line or
b. run the above mentioned code on putty?

love to hear from you

---

