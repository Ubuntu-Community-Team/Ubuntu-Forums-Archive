---
title: "[SOLVED] Ubuntu 8.10 update checks take forever"
date: 2008-11-25
forum: x86 64-bit Users
---

### Post by ecsa0014 on 2008-11-25
I have Ubuntu 8.10 X64 installed as a Virtualbox guest inside of a Vista X64 host. When checking for new updates for this install the update manager seems to completely reload every repo file. I don't remeber 8.04 doing this as it was much, much faster when checking for updates. Normally this wouldn't be a problem but I am unfortunately stuck with dial-up as broadband is not offered in my area and having to download 6-8 megabytes every time is a pretty big deal on dial-up. Each check takes about 35mins. This does not include the time used to actually download and install the updates. This has made updating this install a very aggrivating chore. Can any other dial-up users confirm whether or not this is also a problem for them? Any suggestions?

---

### Post by C. Wizard on 2008-11-25
I can confirm.

I've recently had to start using a dialup connection and everything you say is correct.  

Checking for updates can actually take hours. Sometimes I start it and go to bed.

Downloading the upgrades it another horror story. What use to take 20 or 30 minutes on DSL now takes several nights of 10-12 hour sessions of the computer running while I'm asleep.  

You can forget trying to download anything from that ppa-.. can't remember the name, but I think it is a server in France. Total waste of time trying to download even the smallest of files...  

Given the wide, by that I mean, world wide, user base of Ubuntu and the fact that not everyone in every location has access to a broadband connection, I would think there would be more consideration for those on dialup.

---

### Post by null_pointer_us on 2008-11-27
> **ecsa0014 said:**
> I have Ubuntu 8.10 X64 installed as a Virtualbox guest inside of a Vista X64 host. When checking for new updates for this install the update manager seems to completely reload every repo file. I don't remeber 8.04 doing this as it was much, much faster when checking for updates. Normally this wouldn't be a problem but I am unfortunately stuck with dial-up as broadband is not offered in my area and having to download 6-8 megabytes every time is a pretty big deal on dial-up. Each check takes about 35mins. This does not include the time used to actually download and install the updates. This has made updating this install a very aggrivating chore. Can any other dial-up users confirm whether or not this is also a problem for them? Any suggestions?

IMO this is a problem even for broadband users. I first noticed this massive slowdown when switching from 8.04 (64-bit) to 8.10 (64-bit), via a clean install. However, the problem seems to have disappeared (for a week now, at least) when I switched my software source from the US server to the main server. You can find this option here:

System -> Administration -> Software Sources -> Ubuntu Software -> Download from: Main server

Another problem I had with the US server is that none of the updates provided descriptions about the changes. I don't know what the cause is. And the connection would frequently timeout, too. Sometimes the transfer rate would oscillate between approx. 2600 B/s and 12000 B/s. What a mess!

Now that I've switched back to the main server, I'm seeing > 700 **_K_**B/s transfer rates and update checking is nearly instantaneous (< 3s).

EDIT: The first update check after you switch servers, there's an ~8 MB download involved, but this amount dramatically decreases for subsequent update checks on the main server, whereas the US server seems to re-download the entire ~8 MB every update check.

---

### Post by ve2dmn on 2008-11-27
> **null_pointer_us said:**
> 

System -> Administration -> Software Sources -> Ubuntu Software -> Download from: Main server


An even better move is to do : System -> Administration -> Software Sources -> Ubuntu Software -> Download from: Other
and then select "Select Best Server"

Maybe NOT a good idea for anyone running dial-up, but it will definitely speed thing up for the rest of us.

---

### Post by ecsa0014 on 2008-11-28
Thanks for the replies! I switched over to the main server as suggested by null_pointer_us and it seems to have fixed this issue. I can finally enjoy using Ubuntu again as this problem was really killing the "Ubuntu Experience" for me.
Now, if I could only convince someone to run broadband out my way. Oh well, Can't have everything. Thanks again!

---

### Post by C. Wizard on 2008-11-28
The problems as I described in post 2 of this thread are with the main server, NOT the U.S. server.
This forum is not much better. Of all the various web sites I visit on a daily basis this is the slowest of them all.

---

### Post by ecsa0014 on 2008-11-28
I may have jumped the gun when marking this thread as solved. The solution does appear to fix my problem but I don't guess this problem will truly be solved until whatever is going on with the servers is fixed. This could be a huge turn-off for new Ubuntu users.

---

