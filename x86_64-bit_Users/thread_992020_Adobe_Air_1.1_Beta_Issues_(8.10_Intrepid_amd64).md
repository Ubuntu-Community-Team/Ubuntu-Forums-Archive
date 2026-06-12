---
title: "Adobe Air 1.1 Beta Issues (8.10 Intrepid amd64)"
date: 2008-11-24
forum: x86 64-bit Users
---

### Post by SpikedEffect on 2008-11-24
Hi all,

I was wondering if anyone else is having issues with the Adobe Air 1.1 Beta and programs like Twhirl and TweetDeck on Ubuntu Intrepid 8.10 amd64?

Seems it's having issues connecting using secure methods in these programs.

At first it complained about a missing shared library libgnome-keyring.so which I found out it was looking for in /usr/lib32/.

After having used getlibs to get the missing libraries, it just seems it can't connect / authorise properly.

Has anyone got either of these apps working on a Ubuntu Intrepid 8.10 amd64 set-up?

I'd really like to somehow get them working.

Thanks in advance,

SE

---

### Post by SpikedEffect on 2008-11-26
:Bump: Anyone?

---

### Post by ve2dmn on 2008-11-27
I've had the same issue and I managed to get twhirl working with Identi.ca (because your own timeline seems to be public)

The ssl issue seems to have to do with the fact that these files aren't installed :
/usr/lib/libnss3.so.0d (provided by libnss3-0d package)
and
/usr/lib/libnspr4.so.1d (not provided by any package I could find on amd64) 
. These should probably be the ia32 version, but Adobe Air uses symlinks nested in /opt/Adobe AIR/Versions/1.0/Resources/nss3 that point to the /usr/lib directory... So the actually issue might be a bit more complicated...

I've since switched to jabber for identi.ca update but I'm not sure what to do about twitter... I kinda loved twhirl

---

### Post by gmoctav on 2009-01-26
I've got the same problem on 8.10 , X64 . No idea of a fix , unfortunately. Try Twitux instead.

---

### Post by Triptol on 2009-02-18
Adobe has some excellent information for us AMD64 users:

[http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084&sliceId=1)

After following those steps, I now have tweetdeck working (although I had to install file-roler and the ln commands at the end didn't work for me)

---

