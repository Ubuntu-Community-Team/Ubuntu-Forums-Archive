---
title: "BAIDU on Wine (Can't believe!)"
date: 2014-05-16
forum: Wine
---

### Post by fernandojosecabral on 2014-05-16
Some how the plague know as Baidu managed to take wine over. Its logo is flashing on the application panel. 
When I run ps -ef I see it there: **user   886     1  7 20:19 ?        00:00:00 /usr/bin/wine64-preloader C:\Program Files (x86)\Baidu Security\Baidu Antivirus\bavhm.exe**                
But, no matter what I do, it keeps running. I killed with every kind of signal and it is immediately lunched again.

Any hints on how to get rid of this thing (I though I would never see this again after quiting Windows....)

Thanks

- fernando

---

### Post by TheFu on 2014-05-16
[B]rm -rf ~/.wine/
[/B]
But you probably won't like the side effects. This will remove your WINE installed programs, settings, data - ALL OF THEM.

---

### Post by fernandojosecabral on 2014-05-17
I ran 'find / -name "*[Bb][Aa][iI][Dd][uU]*" -print' and removed all files and directories found. That took good care of it.
Then I found I had also won another gift called Hao123. Did the same as above. So now they are gone. Nevertheless,
their names are still hanging on wine's "add/remove programs". But, I just can't remove them from their. Any hints
on wich files wine keeps those names?

(I am impressed on how agressive this Baidu people are. They are everywhere, using every kind of trick to contraband their
virus into your system, and making it harder and harder to remove them).

- fernando

---

### Post by TheFu on 2014-05-17
may want to review **find -iname** for next time. ;)
Glad you found a less abusive solution!

I've been blocking all Baidu subnets (especially their web crawlers) for years. They don't honor robots.txt, which makes them my enemy.

---

### Post by Wolfsblood on 2014-05-18
How do you block them? I'm new to Ubuntu and Linux in general. I've never heard of baidu, either in my dealings with windows or here.  What do I need to look out for and how can I best avoid it?

---

### Post by TheFu on 2014-05-21
You can find a list of subnets they use with google, then setup DROP rules in iptables. Simple.

Baidu is the worlds larges search engine (Chinese).  I started blocking them because their servers were using 95% of a webserver's bandwidth use, but I wasn't getting ANY referrals.  Even Bing sends "some" referrals. Google uses the most bandwidth of any webcrawler on that webserver now, but sends over 90% of all referrals - seems like a good trade to me.

I've never had any issues with Baidu on a desktop. I can only guess it is like the old Yahoo-search toolbar that was installed as crapware with many programs.  On Windows, I use free programs from ninite.com (closest thing to APT), Microsoft, and a few commercial programs for video editing stuff (paid them money).  Everything else is Ubuntu from repos.

---

### Post by SuperFreak on 2014-05-21
> **TheFu said:**
> You can find a list of subnets they use with google, then setup DROP rules in iptables. Simple.

Baidu is the worlds larges search engine (Chinese).  I started blocking them because their servers were using 95% of a webserver's bandwidth use, but I wasn't getting ANY referrals.  Even Bing sends "some" referrals. Google uses the most bandwidth of any webcrawler on that webserver now, but sends over 90% of all referrals - seems like a good trade to me.

I've never had any issues with Baidu on a desktop. I can only guess it is like the old Yahoo-search toolbar that was installed as crapware with many programs.  On Windows, I use free programs from ninite.com (closest thing to APT), Microsoft, and a few commercial programs for video editing stuff (paid them money).  Everything else is Ubuntu from repos.

I am unsure how to use this infromation. Searching the web I found this
```


iptables -p tcp -I INPUT -j DROP -s 119.63.192.0/21
iptables -p tcp -I INPUT -j DROP -s 123.125.64.0/18
iptables -p tcp -I INPUT -j DROP -s 180.76.0.0/16
iptables -p tcp -I INPUT -j DROP -s 220.181.0.0/16
```
[http://www.theperfectarts.com/2012/09/block-baiduspider-server-wide/]("http://www.theperfectarts.com/2012/09/block-baiduspider-server-wide/")
Would entering the above code into terminal using sudo priviledges block Baidu? And is this necessary only for a dedicated server or would it be useful for a desktop?
Thanks
[SIZE=4]
EDIT: I see this problem is affecting web servers not desktops as you said in an earlier post so presumably my concern was unwarranted[/SIZE]

---

### Post by TheFu on 2014-05-25
If baidu is causing issues (server or desktops), then I'd block all their subnets and domains, period.

* I wouldn't just block tcp.
* I wouldn't type anything into a terminal
* I would script it - either in rc.local or in a specific firewall startup script added to /etc/init.d/ - there are lots and lots of examples on how to do that.
* I would follow scripting best practices. This stuff is important.
* I would put these rules into my router(s) and every portable device I have.

---

