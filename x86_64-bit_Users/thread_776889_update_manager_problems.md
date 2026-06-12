---
title: "update manager problems"
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by Grone1985 on 2008-05-01
Hi,
So my Ubuntu doesn't seem to be updating automatically anymore and when I try to make it check for new updates I get this errors.
The medibuntu ones were from yesterday and the ubuntu ones are from just now. Any ideas anyone?

Thanks in advance!

```
W: Failed to fetch http://packages.medibuntu.org/dists/hardy/Release.gpg  Could not connect to packages.medibuntu.org:80 (87.98.242.10). - connect (111 Connection refused)

W: Failed to fetch http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2  Could not connect to packages.medibuntu.org:80 (87.98.242.10). - connect (111 Connection refused)

W: Failed to fetch http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2  Could not connect to packages.medibuntu.org:80 (87.98.242.10). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.



W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Grone1985 on 2008-05-02
Does anyone else have the same problem?

---

### Post by bferd on 2008-06-04
I have the same problem.

Anyone found a solution?

---

### Post by theodorekon on 2008-06-09
I also have the same problem. I get the following message:

[PHP]W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not resolve 'fr.archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/PHP]

Any ideas??

---

### Post by hardawayd on 2008-06-17
i have the same problem also. What is the cure?

---

### Post by Kilz on 2008-06-17
Click System > Administration > Software Sources
Click the Download From menu and choose other
Click the Select Best Server button and wait till it finds one.
Click Choose Server
Run the update manager again.

---

### Post by eznet on 2008-07-14
> **Kilz said:**
> Click System > Administration > Software Sources
Click the Download From menu and choose other
Click the Select Best Server button and wait till it finds one.
Click Choose Server
Run the update manager again.

That doesn't seem to be the problem.  It seems that medibuntu.org is down
```
ping packages.medibuntu.org 
ping: unknown host packages.medibuntu.org

ping medibuntu.org
ping: unknown host medibuntu.org

```

their webpage is down as well... Maybe it will come back up... I was attempting to reinstall Skype and ran into this problem, which is what lead me here...  Don't know if it applies, as the thread was started over a month ago, but as of July 14,2008 that seems to be the case... we shall see.

---

### Post by eznet on 2008-07-14
[https://bugs.launchpad.net/medibuntu/+bug/248316]("https://bugs.launchpad.net/medibuntu/+bug/248316")

Yup... Down.

---

### Post by andhraandroid on 2008-07-14
I seem to have gotten it working. I had the same problem, so what i did was comment out the medibuntu repos in sources.list and then i followed the instructions on [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to re add the medibuntu repositories. it seemed to have worked.

---

### Post by nycste on 2008-07-14
> **andhraandroid said:**
> I seem to have gotten it working. I had the same problem, so what i did was comment out the medibuntu repos in sources.list and then i followed the instructions on [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to re add the medibuntu repositories. it seemed to have worked.

i removed the 2 older versions i had in repos and then added

```
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
```

from the terminal and just updated no errors

---

### Post by eznet on 2008-07-16
Perhaps where you all removed the old ones and re added them did something or it may be coincidence coinciding with the Medibuntu servers coming back on line.  There is documentation floating around on Launchpad and Medibuntu forums that the servers were in fact down.

I didn't do anything to my sources, tried again a little later and everything worked perfectly... Who knows... at least it is up now and I am back on Skype :)

---

### Post by tech9 on 2008-12-31
I had this problem too after updating 8.10 with over 200 updates.

Apparently, one of the updates stripped out my domain from the server.cfg under ntlmaps...

after I put my domain name back, it worked! :)

I hope this helps someone else out there using ntlmaps for ntlm authentication.

T9

---

