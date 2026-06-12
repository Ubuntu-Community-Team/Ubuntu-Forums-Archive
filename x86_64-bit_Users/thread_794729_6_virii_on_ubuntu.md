---
title: "6 virii on ubuntu"
date: 2008-05-14
forum: x86 64-bit Users
---

### Post by cyhk on 2008-05-14
Hello.

I don't know how, but ClamAV is telling me I have 6 virii on my computer.  They are:

eicar.com.txt (status says: eicar-test-signature (i quarantined it))
xfprot-1.22.1.tar.gz (status says: eicar-test-signature (i quarantined it))
Trash.virus.virus (status: files number limit exceeded)
Inbox.virus.virus (status: files number limit exceeded)
GlobalR (status: phishing.heuristics.email.spoofeddomain)
Inbox (status: phishing.heuristics.email.spoofeddomain)

I run Mozilla Thunderbird as my email client.
I installed FProt, though it didn't pick up any of them.  Any recommendations on how to clear them?

Cheers.

---

### Post by Kilz on 2008-05-14
> **cyhk said:**
> Hello.

I don't know how, but ClamAV is telling me I have 6 virii on my computer.  They are:

eicar.com.txt (status says: eicar-test-signature (i quarantined it))
xfprot-1.22.1.tar.gz (status says: eicar-test-signature (i quarantined it))
Trash.virus.virus (status: files number limit exceeded)
Inbox.virus.virus (status: files number limit exceeded)
GlobalR (status: phishing.heuristics.email.spoofeddomain)
Inbox (status: phishing.heuristics.email.spoofeddomain)

I run Mozilla Thunderbird as my email client.
I installed FProt, though it didn't pick up any of them.  Any recommendations on how to clear them?

Cheers.

Congratulations you found the [eicar test file]("http://www.eicar.org/anti_virus_test_file.htm")!

---

### Post by cyhk on 2008-05-15
True enough, the EICAR test file is there.  I'm curious though how my inbox for Mozilla Thunderbird and a specific folder (GlobalR) from my inbox is coming up.  I've cleaned it out my folder once and it's still there.

Is the test file EICAR also associated to my thunderbird inbox?  If not, how do I scan and remove that phishing heuristic?

Also, is the .virus.virus files also part of the EICAR?

Cheers.

---

### Post by jrusso2 on 2008-05-15
> **cyhk said:**
> True enough, the EICAR test file is there.  I'm curious though how my inbox for Mozilla Thunderbird and a specific folder (GlobalR) from my inbox is coming up.  I've cleaned it out my folder once and it's still there.

Is the test file EICAR also associated to my thunderbird inbox?  If not, how do I scan and remove that phishing heuristic?

Also, is the .virus.virus files also part of the EICAR?

Cheers.

it seems like it picked up the EICAR test file that was in fprot and some emails had a spoofed domain not a virus. I would think most antivirus programs are smart enough to know the EICAR test files and ignore them.

Seems like you should be able to just delete the emails and empty the trash.

---

