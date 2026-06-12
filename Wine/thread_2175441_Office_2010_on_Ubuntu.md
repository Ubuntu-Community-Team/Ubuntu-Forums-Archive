---
title: "Office 2010 on Ubuntu"
date: 2013-09-19
forum: Wine
---

### Post by Jaxilian on 2013-09-19
Hi
I need some help with getting Outlook 2010 SP1 x86 to work with Ubuntu (with AD connection through Winbind). I am using Ubuntu 12.04.2 x64.
I know it's possible to set it up so no "use Evolution/Thunderbird" please

I have gotten to the point that I have Office 2010 SP1 x86 installed and it seems to work ok except Outlook which refuses me to be able to log into our Exchange server. It just throws the login window in my face at every try (I type correct password).
I can ping the exchange server just fine.

Anyone knows what to do or what I missed?

/M

---

### Post by Kirboosy on 2013-09-19
Are you putting the domain information in? (*DomainName\*username)

For whatever reason Outlook 2010 doens't work fully in Wine. Maybe you can break the trend and get it properly working.
[URL="http://askubuntu.com/questions/91176/how-to-get-office-2010-specifically-outlook-to-run"]
How to get Office 2010 to run
[/URL]

---

### Post by Mark Phelps on 2013-09-19
MS Outlook has a long reputation of NOT working with Wine.  Outlook 2010 (the 32-bit version) rates Silver at the WineHQ site:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=25161]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=25161")

My own experience in trying to use Wine with MS Office components, is that unless the rating is Gold, the lack of features in Wine rendered the Office component all but useless.

---

### Post by Jaxilian on 2013-09-21
I think I got it to work

I put in [email]username@domain.com[/email] in username and then my password in password. It worked and Outlook started OK. Cached mode doesn't work so I had to deactivate that too.

One thing that worked somewhat ok after was closing Outloook. Sometimes it said "Outlook is closing" forever and sometimes it worked ok and it actually closed after 5-10 sec.

Thanks for your posts!

---

