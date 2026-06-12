---
title: "WebMin v1.441 and upload CRASH SERVER!"
date: 2008-11-05
forum: x86 64-bit Users
---

### Post by cenwesi on 2008-11-05
It seems anytime i upload a file over 350meg through webmin to the server, it crashes the server! I have tried this in a VMware and got the same result for 32/64bit Intrepid ibex. Files lower than that is fine.

Any one else noticed this yet?

---

### Post by cenwesi on 2008-11-10
i guess no one is having this problem..
bump

---

### Post by cariboo on 2008-11-10
It might be worth submitting a bug to the webmin people. I not sure many people use webmin as there are so many other ways to transfer files. For 1 or 2 files I use sftp, for Several gigabytes of files I usually use Filezilla and ftp.

Jim

---

### Post by cenwesi on 2008-11-13
i was able to solve this problem by increasing my swap size. I have 4gigs of ram and my swap size was 1.6g. I guess the rule for doubling the swap size still holds. I increased my swap size to 9gig and sure enough i was able to upload a 700meg file and webmin and the server didn't crash anymore.

PS, i tested in VM before applying it to the production server.

---

