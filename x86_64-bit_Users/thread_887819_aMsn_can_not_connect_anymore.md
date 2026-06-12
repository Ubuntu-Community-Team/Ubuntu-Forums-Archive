---
title: "aMsn can not connect anymore"
date: 2008-08-12
forum: x86 64-bit Users
---

### Post by whoop on 2008-08-12
All of a sudden my aMsn will not connect to my account anymore.It starts up normally then when I connect it says "Logging In...", after a while "Error Connecting to server", then it goes back to "Logging In...". It does not log in anymore. I tried removing my .amsn directory in my home directory and I tried uninstalling and reinstalling aMsn itself.
The account connects fine with pidgin or windows live messenger (in windows)
I am using hardy heron 64 bit with the default aMsn installation (0.97 12/25/2007).

Hope anybody can help me out. Cheers.

---

### Post by Usufruct on 2008-08-12
Doesn't really seem like this is an x86-64 issue, but could you post the status log if you can?

---

### Post by Samw13 on 2008-08-12
You need to install the latest version of AMSN (0.97.2) however this isn't in the repositories for Hardy - but is available for Intrepid - I downloaded the packages from the Ubuntu packages site - here's a quick step by step:

1. Download tcl-tls from [here](http://packages.ubuntu.com/intrepid/amd64/tcl-tls/download)
Then install using your preferred method (shell+dpkg/synaptic/etc)

2. Download amsn-data from [here](http://packages.ubuntu.com/intrepid/all/amsn-data/download) and install as above

3. Download amsn 0.97.2 from [here](http://packages.ubuntu.com/intrepid/amd64/amsn/download). When installing you will get a message telling you an older, and therefore supported (!) version is available in a software channel etc etc - just ignore this.

All other dependencies should be met from Hardy repositories - if not post here and I'll try to help! You do this at your own risk - I'm not taking responsibility if things go wrong - however, it worked for me and have been chatting on it for the last 8 hours!

Hope This Helps
SW

---

### Post by whoop on 2008-08-12
Where do I find this status log?

---

### Post by whoop on 2008-08-12
Wow, so you mean this won't be fixed in hardy?

---

### Post by Adri2000 on 2008-08-12
This is [https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722) and it's fixed already in hardy-proposed, and should be in hardy-updates very soon.

---

### Post by joffa82 on 2008-08-13
I had the same problem. I found a thread on here that suggested the following:

Go into System -> Administration -> Software Sources.

In the updates tab, select 'Pre-released updates (Hardy-Proposed)'

Then close it and open a terminal and type in 'sudo apt-get install amsn'

It should ask if you'd like to update, say yes and let it update. Then go back into software sources and uncheck pre-released updates.

I did this on my system and it's worked flawlessly since.

---

### Post by Arwen on 2008-08-13
Thank source it's a bug!
I initially freaked out as I've just connected my new router(I used to have a simple dsl modem) and thought it was driving amsn mad.
Thanx joffa82,it worked flawlessly for me too.

---

### Post by toocer on 2008-08-13
> **joffa82 said:**
> I did this on my system and it's worked flawlessly since.

Well i did this to, and guess what it worked flawlessly for me to :D

---

### Post by kamonn on 2008-08-13
> **joffa82 said:**
> I had the same problem. I found a thread on here that suggested the following:

Go into System -> Administration -> Software Sources.

In the updates tab, select 'Pre-released updates (Hardy-Proposed)'

Then close it and open a terminal and type in 'sudo apt-get install amsn'

It should ask if you'd like to update, say yes and let it update. Then go back into software sources and uncheck pre-released updates.

I did this on my system and it's worked flawlessly since.
Works!! Thank you

---

### Post by tuxxy on 2008-08-13
MSN updated their protocol, you need to update your aMSN to the new 0.97.2 version to access the network, download the 32/64bit update package here; [http://www.getdeb.net/app/aMSN](http://www.getdeb.net/app/aMSN)

---

