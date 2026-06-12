---
title: "Setting from adress in postfix"
date: 2006-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by jon_gunnar on 2006-02-17
I got postfix running ok.But in those cases were mail should have gone out from my local system there is some problems.

Is there a way I can control what is written before the @ in the adress?
The domain part is correct,but my user name is placed in front of the @ and that makes problems.

If anyone understand what I mean ;)  and know how I would be very grateful.

---

### Post by kmi on 2006-02-19
You can :

sudo gedit /etc/postfix/main.cf

And add (at the end of the file, for example) :

sender_canonical_maps = hash:/etc/postfix/sender_canonical

Save the file. Then :

sudo gedit /etc/postfix/sender_canonical

And add your users and their 'new identities' :

root    [email]myaddress@myisp.com[/email] #Admin (me)
my-ubuntu-user-name   [email]myaddress@myisp.com[/email] # Another me
www-data   [email]me@mydomain.org[/email] # Me...
user-to-hide   [email]user-to-show@mydomain.org[/email] # An so on

Save the file. Then (to create/update the database) :

sudo postmap /etc/postfix/sender_canonical

And I restart postfix (reload might be enough, don't know...) :

sudo /etc/init.d/postfix restart

Hope it helps... :)

---

### Post by jon_gunnar on 2006-02-19
[QUOTE=kmi]You can :

sudo gedit /etc/postfix/main.cf
And add (at the end of the file, for example) :
sender_canonical_maps = hash:/etc/postfix/sender_canonical

Save the file. Then :
sudo gedit /etc/postfix/sender_canonical

And add your users and their 'new identities' :

my-ubuntu-user-name   [email]myaddress@myisp.com[/email] # Another me

Save the file. Then (to create/update the database) :

sudo postmap /etc/postfix/sender_canonical
And I restart postfix (reload might be enough, don't know...) :

sudo /etc/init.d/postfix restart

Hope it helps... :)[/QUOTE]

It helped a lot.In fact it worked perfect:)  .Thanks a lot for this tip,have been having this problem for a while.

---

### Post by patrick295767 on 2006-03-05
Hi Hi, 

I am fighting with sending email via cmd line ... 
I did :
apt-get -f install postfix mailx

said : 
[email]patrick295767@hotmail.com[/email]
  
then, used : internet smart stuffs
  
then, 
  
used what said ...  in the conf file
  
then : 
sendmail "kljlk" [email]patrick295767@hotmail.com[/email] < message.txt
  
 or
  
sendmail "kljlk" root < message.txt
  
is giving : 


#mail
No mail for root
  
Someone could help me ??
  
Thank youvery much !!
  
Patrick

---

### Post by kmi on 2006-03-06
Sorry to ask :) but... is Sendmail installed ? It is absolutely NOT necessary for the basic job of sending mails via the command line...

With Postfix, I use :
```
mail theoneIwant2mail@hisaddress.org
```
Postfix can't send mails to "root", "root" needs to be aliased before this command
```
mail root
```

Do these commands work ?

To monitor the mail activity, you may :
```
tail -f /var/log/mail.info
```

---

### Post by patrick295767 on 2006-03-07
[QUOTE=kmi]Sorry to ask :) but... is Sendmail installed ? It is absolutely NOT necessary for the basic job of sending mails via the command line...

With Postfix, I use :
```
mail theoneIwant2mail@hisaddress.org
```
Postfix can't send mails to "root", "root" needs to be aliased before this command
```
mail root
```

Do these commands work ?

To monitor the mail activity, you may :
```
tail -f /var/log/mail.info
```[/QUOTE]
  
Thank you for the informations, I'll try tongith and try to progress with it... 
  
By the way, ```
*tu peux m'ajouter dans tes buddy msn messenger... J'aurais peut etre l'intention de te demander une ou 2 questions a propos du postfix. Merci; Chalut*
```

---

### Post by patrick295767 on 2006-03-09
Checked... 
   
I just did : 
```
mail root -subject "lkjklj " < mytext.txt
```
  
```
sudo mail
```
and no emails .... 
  
then the tail function gives:
```
# tail -f /var/log/mail.info
Mar  9 22:17:12 localhost postfix/qmgr[7901]: 57B2620173: from=<celina@patrick295767@gmail.com>, size=409, nrcpt=2 (queue active)
Mar  9 22:17:12 localhost postfix/pickup[15802]: D68CC20172: uid=1001 from=<celina>
Mar  9 22:17:13 localhost postfix/qmgr[7901]: 57B2620173: to=<kjljklj@patrick295767@gmail.com>, orig_to=<kjljklj>, relay=none, delay=2, status=deferred (delivery temporarily suspended: connect to gsmtp183.google.com[64.233.183.27]: Connection timed out)
Mar  9 22:17:13 localhost postfix/cleanup[16147]: D68CC20172: message-id=<20060309211712.D68CC20172@localhost.localdomain>
Mar  9 22:17:14 localhost postfix/qmgr[7901]: D68CC20172: from=<celina@patrick295767@gmail.com>, size=409, nrcpt=2 (queue active)
Mar  9 22:17:14 localhost postfix/qmgr[7901]: D68CC20172: to=<kjljklj@patrick295767@gmail.com>, orig_to=<kjljklj>, relay=none, delay=2, status=deferred (delivery temporarily suspended: connect to gsmtp183.google.com[64.233.183.27]: Connection timed out)
Mar  9 22:17:14 localhost postfix/pickup[15802]: BB2D920177: uid=1001 from=<celina>
Mar  9 22:17:14 localhost postfix/cleanup[16141]: BB2D920177: message-id=<20060309211714.BB2D920177@localhost.localdomain>
Mar  9 22:17:14 localhost postfix/qmgr[7901]: BB2D920177: from=<celina@patrick295767@gmail.com>, size=409, nrcpt=2 (queue active)
Mar  9 22:17:14 localhost postfix/qmgr[7901]: BB2D920177: to=<kjljklj@patrick295767@gmail.com>, orig_to=<kjljklj>, relay=none, delay=0, status=deferred (delivery temporarily suspended: connect to gsmtp183.google.com[64.233.183.27]: Connection timed out)
Mar  9 22:17:44 localhost postfix/smtp[16151]: connect to mx4.hotmail.com[65.54.190.179]: Connection timed out (port 25)
Mar  9 22:17:45 localhost postfix/smtp[16154]: connect to mx4.hotmail.com[65.54.244.232]: Connection timed out (port 25)
Mar  9 22:17:49 localhost postfix/smtp[16152]: connect to mx1.hotmail.com[65.54.245.8]: Connection timed out (port 25)
                            

[1]+  Stopped                 tail -f /var/log/mail.info

```
  
Would you konw what s wrong ??

thank u !

---

### Post by kmi on 2006-03-09
[QUOTE=patrick295767]Checked... 
   
I just did : 
```
mail root -subject "lkjklj " < mytext.txt
```  
```
sudo mail
```
and no emails .... [/QUOTE]
You should just type :
```
mail root
```
Then "Enter"
It asks for "Subject:" type yours and "Enter"
Then your message then "Enter"
To end message type just one single "." on the last line and "Enter".
It asks fo "Cc:" type yours and "Enter"

Should be better :) but I don't know for the final result yet since there might be something else to configure...
For the moment, I have no time to **try** to understand your logs, I'll come back to you as soon as I can. ;)

---

### Post by kmi on 2006-03-09
Ok.

[QUOTE=patrick295767]```
celina@patrick295767@gmail.com
```[/QUOTE]
Is wrong. Check aliases or nameserver*...

[QUOTE=patrick295767]```
orig_to=<kjljklj>, relay=none,
```[/QUOTE]
'orig_to=<kjljklj>' is because you issued a bad "mail" command (see previous post), 'relay=none' shows it's misconfigured*...

For :
[QUOTE=patrick295767]```
mx1.hotmail.com
```[/QUOTE]
Replace with your ISP's smtp in config file*.

*In /etc/postfix/main.cf (why don't you post it ? :-) )

---

### Post by patrick295767 on 2006-03-10
[QUOTE=kmi]Ok.


Is wrong. Check aliases or nameserver*...


'orig_to=<kjljklj>' is because you issued a bad "mail" command (see previous post), 'relay=none' shows it's misconfigured*...

For :

Replace with your ISP's smtp in config file*.

*In /etc/postfix/main.cf (why don't you post it ? :-) )[/QUOTE]
  
Ahhh, ... big progression !!
Once I am home with my linux box, this evening, I'll post you the config : /etc/postfix/main.cf.
  
  I didnt touch any files in the postfix config or very little
I'll go into this /etc/postfix/main.cf again
...
   
Thank you very much for your great help !!

Patrick

---

