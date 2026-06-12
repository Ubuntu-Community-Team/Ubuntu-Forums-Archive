---
title: "Still having &quot;Error while storing 'Inbox' &quot; error in evolution."
date: 2009-08-05
forum: x86 64-bit Users
---

### Post by scho on 2009-08-05
Hi,

To resolve this issue I followed all the tricks posted in the forum, but I couldn't resolve. In the .evolution/mail/local, I removed '*.ev-summary' and 'ibex.index(.data)' files, and launched evolution again, but am still having it.
Any suggestions for the problem ? Looks like, I am having this problem after I upgrade it to 9.04.

Thanks,
--

---

### Post by dcstar on 2009-08-07
> **scho said:**
> Hi,

To resolve this issue I followed all the tricks posted in the forum, but I couldn't resolve. In the .evolution/mail/local, I removed '*.ev-summary' and 'ibex.index(.data)' files, and launched evolution again, but am still having it.
Any suggestions for the problem ? Looks like, I am having this problem after I upgrade it to 9.04.

Thanks,
--

[LIST=1]
[*]Check the permissions
[*]Check you have sufficient disk space
[*]If all else fails, rename the .evolution folder and then copy the relevant files into the freshly created folder after you restart Evolution
[/LIST]

---

