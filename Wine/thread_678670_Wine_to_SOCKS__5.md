---
title: "Wine to SOCKS  5"
date: 2008-01-26
forum: Wine
---

### Post by trebor147 on 2008-01-26
Hey there,

I live at University housing and they provide me with Internet access.  Its via a proxy server that I need a username and password for, which is fine, mostly.

I have my Ubuntu 7.10 all configured for this proxy, I can do everything I need, apt-get etc.

I installed WoW with Wine and everything went ok.  However I cant connect because of the proxy sever.

I this situation what I usually do is direct the application to my local SOCKS 5 server.  This is easy enough when the application has its own settings, Firefox for example, but not so good when they dont, WoW.

I have looked into tsocks but cant seem to get it working.  I have it configured correctly, but it doesnt work when I run WoW from Wine.

So what I would like to know.  Is it possible to make Wine direct the network traffic to my SOCKS 5 server?  I assume it must be possible, this is Linux after all and everything else works with proxy servers.

Please dont suggest that I just run WoW on Windows.  I dont want to go back.

Thanks for any feedback, id love to be playing WoW again.

---

### Post by abatcher on 2009-01-08
Have you solved this problem ?

I'm behind my university NAT with a few ?hundred/thousand? others in my networksegment with the same public ip. Blizzard keeps banning this public ip because some other punk keeps misbehaving.

I got an ssh server running at home, but I can't get tsocks/socksify to work with wine/warcraft3. I read an [_article_]("http://www.macosxhints.com/article.php?story=20060831091645414") how to do it on mac os x with tsocks, so I'm thinking the problem is wine not supporting socks ?

It's hard to find information about socks and wine (in the right context)

---

