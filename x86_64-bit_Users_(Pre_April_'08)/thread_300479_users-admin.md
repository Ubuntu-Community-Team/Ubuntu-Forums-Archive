---
title: "users-admin"
date: 2006-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by dimis on 2006-11-15
First of all,
my regards to this beautiful community once again.
Now, on topic. I have strange behaviour in my system with 'users-admin'.
Regarding my pc:
```
$ uname -a
Linux crag-hack 2.6.15-27-amd64-generic #1 SMP PREEMPT Sat Sep 16 01:50:50 UTC 2006 x86_64 GNU/Linux
```
Suppose you want to create a new user-account on your machine and moreover add this user account to one of the groups you belong; or ideally (and this is suggested to do for verification in your PCs) add this new user and yourself on a new group.
Re-open users-admin and delete the user you just created (not yourself! :p).
Finally, re-open users-admin and check out if you belong in the group you used to belong 2 steps above. Surprise! You are NOT there!

Actually, I believe this is a general problem and not only on my 64bit (6.06-all updates) pc. A similar situation occurred in my office where a friend of mine had installed a 32-bit ubuntu. I had an account on his machine with administration privileges. Somehow, I ended up irritating him and he removed me from the admin group. But this way, he was removed as well! And this was confusing next time he wanted to update his machine. He couldn't because no-one had admin privileges. Anyway, we solved the problem by booting a live linux CD, edited the passwords file to NULL for root and managed to get by.

What do you think about this? Have you similar results in your machines?
Btw, can someone tell me what is the default behaviour for users-admin tool when deleting a user? I mean, does it delete user's home directory or not?

Thank you in advance for any thoughts and feedback,
- dimis -

---

### Post by dimis on 2006-11-18
I am confused with everyone's silence. :confused: 
Do you have the same problem and remain silent or no-one else can confirm what I write and does not know what to suggest?
Moreover, what is the case on the *server* edition? My report above was on Dapper Desktop.

Looking forward to hearing from you soon,
Regards,
- Dimitris -

---

