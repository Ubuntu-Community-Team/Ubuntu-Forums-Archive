---
title: "Is the Wine repository down for anyone else?"
date: 2007-12-20
forum: Wine
---

### Post by CarpKing on 2007-12-20
For the past several days, I've been trying to get Wine to update.  Everytime I try apt-get update, the Wine repository connection times out.  Is anyone else having this problem?

---

### Post by cogadh on 2007-12-20
Nope, its up right now and has been for the past few days (as far as I can tell). Are you sure you have the repository added to you lists correctly?

---

### Post by CarpKing on 2007-12-20
I have:
```
deb http://wine.budgetdedicated.com/apt gutsy main
deb-src http://wine.budgetdedicated.com/apt gutsy main
```

I can't see anything wrong with that, unless there's some terrible spelling mistake that I'm missing.  I copied and pasted it from the sticky here.  Is apt-get subject to DNS cache issues?  I don't know much about any of that, but I've seen it given as an explanation when websites appear to be down for some but not others.

---

### Post by DM was on fire! on 2007-12-20
Try adding the keys to it, according to the instructions on WineHQ.org.

> wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

And then...

> sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

---

### Post by yabbadabbadont on 2007-12-20
Can you successfully visit the following URL with your browser?

[http://wine.budgetdedicated.com/apt/dists/gutsy/](http://wine.budgetdedicated.com/apt/dists/gutsy/)

Edit: I can, by the way.

---

### Post by CarpKing on 2007-12-20
> **DM was on fire! said:**
> Try adding the keys to it, according to the instructions on WineHQ.org.

That command just sits there without doing anything; I'm guessing if I let it go long enough I'd probably get a timeout error.  

> **yabbadabbadont said:**
> Can you successfully visit the following URL with your browser?

[http://wine.budgetdedicated.com/apt/dists/gutsy/](http://wine.budgetdedicated.com/apt/dists/gutsy/)

Edit: I can, by the way.

For me, it loads for a long time and then gives me:

> “wine.budgetdedicated.com” is not responding.

The connection was lost because the server took too long to respond. The server may be busy or you may have a network connection problem. Try again later.

There may be an old version of the page you wanted:


    * in the Google Cache

    * in the Internet Archive

---

### Post by yabbadabbadont on 2007-12-20
I would guess that it is a DNS or proxy issue.

---

### Post by wretchedmage on 2007-12-20
I'm having the same problem. Can't connect.

---

### Post by yabbadabbadont on 2007-12-20
I just clicked the link that I posted and browsed through the different directories...  Try putting the raw IP address in the address bar of your browser and see if the site comes up then.  This is the address for wine.budgetdedicated.com:  81.171.111.184

---

### Post by wretchedmage on 2007-12-20
Taking too long to respond and times out.  Do the wine repository servers get hammered all the time?

---

### Post by yabbadabbadont on 2007-12-20
It is quite snappy for me.  I wonder if there is a network outage somewhere between you and the wine servers?

---

### Post by cogadh on 2007-12-20
That was my thought too. The Wine repositories are on some pretty hefty servers, so I doubt the problem is due to heavy traffic. Its more likely that there is some kind of network outage. It does look like there are main routers offline in Germany and in Wisconsin right now, that could be the cause, depending on your location:
[http://www.internettrafficreport.com/](http://www.internettrafficreport.com/)

---

### Post by CarpKing on 2007-12-22
Everything seems to be back in order.  The update was successful.  Thank you all for the information!

---

### Post by t_echtenkamp on 2007-12-28
I still have this problem, I tried on the 23rd to follow the instructions on winehq.com but wine.budgetdedicated.com always times out.

The command

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

finally connected after it timed out about 6 times and I was able to download and install the key, but now the command 

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

continually times out. After 20 tries it gives up. I gave it a couple days and it's still not working. Any ideas?

Tim E.

---

### Post by Makurosu on 2007-12-28
Tim, I'm having the same problem.  It has been down for several days for me too.

---

### Post by Rahu on 2007-12-28
I've also had this for a while now. Though I'm in Wisconsin, which does seem to be having some internet issues :(

There happen to be a mirror of the builds there anywhere?

---

### Post by forbin on 2007-12-28
I'm in southeast Wisconsin and cannot connect (or even PING) the repository by Domain name or IP address.

---

### Post by c0rdawg on 2007-12-29
I have not been able to connect to it either in the past day. I'm from New York...

---

### Post by Flatline-kun on 2007-12-30
I am from New York too and cannot get to it from my local machine...however if I ssh into a machine I have in Colorado, I can get to it no problem. Weird.

Flatline-kun

---

### Post by forbin on 2007-12-30
It's been 4 days now and I still can't connect to it from SE Wisconsin. A traceroute hangs at 1-1.r1.lo.hwng.net [69.16.191.50]
Does anyone know of a mirror site?

---

### Post by tonyshangrila on 2007-12-30
Been having the same problem (again, in Milwaukee) for almost 2 weeks now as of 12/30/07.

Wish I knew what else to do about it.. ??

---

### Post by forbin on 2007-12-30
FYI, finally got through this afternoon at 5:00pm CST. Yessss! :)

---

### Post by Flatline-kun on 2007-12-30
I got through here in New York as well...the problem seemed to be with some place called Pure Gig (hwng.net). That's where the route stopped, but it gets through now.

Flatline-kun

---

### Post by t_echtenkamp on 2007-12-30
That's encouraging to hear. I'm out of the States right now (In Ireland for New Years, woot!) and so I'll be away from my desktop for about a week. But I'll try again when I get back.

---

### Post by YokoZar on 2007-12-31
Hi, I run the repository.

The server, while it has a ton of bandwidth, *is* rate limited.  Generally it only hits this limit on release days, and this past Friday I ended up releasing 0.9.52 for every version all at once.  The server can push over 2 terrabytes a month, but it gets pretty expensive to try and do that to everyone all at once on release day.

I'm referring this thread to budgetdedicated.com's support.  If anyone is still having connection issues, please post.


If the instructions on the website aren't working due to traffic issues, we might want to look into more specific rate-limiting, such as prioritizing traffic that is just downloading the key.

---

### Post by BudgetDedicated on 2007-12-31
Hi all,

We host the wine repo on one of the servers in our [budgetdedicated.com]("http://www.budgetdedicated.com") domain. I can tell you that there have not been any problems with the server itself and the traffic stats indicate that people have been able to get the packages. 
Also there was a post before that the server was rate limited, but it has not been in a long time. The server is on a gigabit uplink and theoretically could use the full speed of that line.

That said, there were some routing problems on the web because of misconfigured routers in America. Some of those have been solved now but it is very hard to get a grip on problems that occur in routers on the other side of the world. If people that are having problems could send us traceroutes or supply us with their IPs we might be able to locate and solve the problems.

Regards,
BudgetDedicated

---

### Post by YokoZar on 2007-12-31
> **BudgetDedicated said:**
> We host the wine repo on one of the servers in our [budgetdedicated.com]("http://www.budgetdedicated.com") domain. I can tell you that there have not been any problems with the server itself and the traffic stats indicate that people have been able to get the packages. 
Also there was a post before that the server was rate limited, but it has not been in a long time. The server is on a gigabit uplink and theoretically could use the full speed of that line.
Oh really? Thanks!

---

### Post by mutzinet on 2008-01-12
Strange. I also had some problems a few days ago. And now, 0.9.53 is out but apt-get upgrade says: 
```
Err http://wine.budgetdedicated.com gutsy/main wine 0.9.53~winehq0~ubuntu~7.10-1
  404 Not Found
Failed to fetch http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.53~winehq0~ubuntu~7.10-1_i386.deb  404 Not Found
```

And through my browser I can access [http://wine.budgetdedicated.com/apt/pool/main/w/wine/](http://wine.budgetdedicated.com/apt/pool/main/w/wine/), but there only 0.9.52 seems to be available.
Any ideas what's happening there?

---

### Post by hikaricore on 2008-01-12
I'm guessing at the time of your post 0.9.53 wasn't currently packaged and the apt server was pointing at non-existance packages while it was being uploaded.
It seems to now be up and able to be downloaded.

Usually it takes a day or two for the new packages to be built, keep this in mind and have patience.

---

### Post by mutzinet on 2008-01-13
> **hikaricore said:**
> I'm guessing at the time of your post 0.9.53 wasn't currently packaged and the apt server was pointing at non-existance packages while it was being uploaded.
It seems to now be up and able to be downloaded.

Usually it takes a day or two for the new packages to be built, keep this in mind and have patience.

Thanks for your answer hikaricore. I certainly don't meant to be pushy. I thought that my problem yesterday was linked to the problem mentionned in this thread (and that I also encountered by then), because most of the time when there is an update, apt finds it straight away, I'll keep in mind that there might be some time before the package becomes actually available.

Download and install worked like a charm now. :)

---

### Post by kostkon on 2008-01-13
It went OK for me, I got the update one hour ago, no problems whatsoever.

---

### Post by skisunday on 2008-02-06
I am trying to get wine for the first time and it won't let me in terminal the code it gives me is this:

> neal@neal-laptop:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
gpg: no valid OpenPGP data found.
neal@neal-laptop:~$ sudo wget [http://wine.budgetdedicated.com/apt/...t.d/gutsy.list](http://wine.budgetdedicated.com/apt/...t.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.


---

### Post by yabbadabbadont on 2008-02-06
> **skisunday said:**
> I am trying to get wine for the first time and it won't let me in terminal the code it gives me is this:

That last error message seems to indicate that you are using a proxy.  Disable it and try again.

---

### Post by skisunday on 2008-02-06
how do I disable the proxy?

---

### Post by skisunday on 2008-02-06
could my wifi card be used as a proxy?

---

### Post by yabbadabbadont on 2008-02-06
If you didn't install a proxy, and you also didn't configure your machine to use one, then I would guess that whoever is providing your net connection is doing it.  Contact their tech support and ask if there is a way to disable it.

---

### Post by skisunday on 2008-02-06
thank you but is there another way I can just download a file?

---

### Post by yabbadabbadont on 2008-02-06
[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

Direct download links.

---

### Post by skisunday on 2008-02-06
thank you so much

---

