---
title: "libtalloc segfault"
date: 2009-07-21
forum: x86 64-bit Users
---

### Post by armstrtw on 2009-07-21
I keep seeing these in my /var/log/messages:

```
Jul 21 08:40:01 research kernel: [237932.175018] cron[6406]: segfault at 23fffffff0 ip 00007f6515757a7a sp 00007fff1ef62460 error 4 in libtalloc.so.1.2.0[7f6515752000+8000]
Jul 21 08:45:01 research kernel: [238232.213185] cron[6601]: segfault at 23fffffff0 ip 00007f6515757a7a sp 00007fff1ef62460 error 4 in libtalloc.so.1.2.0[7f6515752000+8000]
Jul 21 08:45:27 research kernel: [238258.502985] cron[6598]: segfault at 23fffffff0 ip 00007f6515757a7a sp 00007fff1ef62460 error 4 in libtalloc.so.1.2.0[7f6515752000+8000]
Jul 21 08:45:27 research kernel: [238258.518909] cron[6599]: segfault at 23fffffff0 ip 00007f6515757a7a sp 00007fff1ef62460 error 4 in libtalloc.so.1.2.0[7f6515752000+8000]
Jul 21 08:46:04 research kernel: [238294.883877] cron[6600]: segfault at 23fffffff0 ip 00007f6515757a7a sp 00007fff1ef62460 error 4 in libtalloc.so.1.2.0[7f6515752000+8000]
Jul 21 08:50:01 research kernel: [238532.135610] cron[7546]: segfault at 23fffffff0 ip 00007f6515757a7a sp 00007fff1ef62460 error 4 in libtalloc.so.1.2.0[7f6515752000+8000]
Jul 21 08:55:01 research kernel: [238832.154482] cron[7745]: segfault at 23fffffff0 ip 00007f6515757a7a sp 00007fff1ef62460 error 4 in libtalloc.so.1.2.0[7f6515752000+8000]
Jul 21 09:00:01 research kernel: [239132.187427] cron[7858]: segfault at 23fffffff0 ip 00007f6515757a7a sp 00007fff1ef62460 error 4 in libtalloc.so.1.2.0[7f6515752000+8000]
Jul 21 09:00:01 research kernel: [239132.414277] cron[7859]: segfault at 23fffffff0 ip 00007f6515757a7a sp 00007fff1ef62460 error 4 in libtalloc.so.1.2.0[7f6515752000+8000]
Jul 21 09:01:01 research kernel: [239192.448477] cron[8038]: segfault at 23fffffff0 ip 00007f6515757a7a sp 00007fff1ef62460 error 4 in libtalloc.so.1.2.0[7f6515752000+8000]
Jul 21 09:05:01 research kernel: [239432.465169] cron[8126]: segfault at 23fffffff0 ip 00007f6515757a7a sp 00007fff1ef62460 error 4 in libtalloc.so.1.2.0[7f6515752000+8000]
Jul 21 09:10:01 research kernel: [239732.716000] cron[8422]: segfault at 23fffffff0 ip 00007f6515757a7a sp 00007fff1ef62460 error 4 in libtalloc.so.1.2.0[7f6515752000+8000]

```

any ideas on what is causing this?  No ill effects are apparent on the system. It's just a bit discomforting to find those messages in the logs.

Thanks,
Whit

---

### Post by hgfischer on 2009-07-29
Hi armstrtw,

I'm having the same problem here. Did you found a way to solve this issue?

Thanks,

---

### Post by masc82 on 2009-08-08
Very same problem here. I have this on jaunty desktop and server, both running on kvm 88.

---

### Post by j3ff on 2009-10-07
Greetings,
I'm having what looks like the same problem.  My syslog is littered with entries similar to the ones in the original post.  I had a look at my logs because my system's kernel paniced overnight and I wanted clues as to why.  I'm not sure if this problem is related to my kernel panic but it might be.

Any help would be greatly appreciated.

---

