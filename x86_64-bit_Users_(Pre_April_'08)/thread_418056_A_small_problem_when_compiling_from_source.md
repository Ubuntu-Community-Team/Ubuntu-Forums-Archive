---
title: "A small problem when compiling from source"
date: 2007-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by rks_i1_13 on 2007-04-22
I have Pentium Core 2 Duo processor running Ubuntu-7.04 (Fiesty) along with win32(XP). When I compile certain sources, **make** complains that a file included :-**<gnu/stubs-32.h>** doesn't exist. Indeed it **does not** exist, actually it is**<gnu/stubs-64.h>** that **actually exists** in /usr/include/gnu.

On checking the actual source of error i found the following in stubs.h :-
```

#include <bits/wordsize.h>

#if __WORDSIZE == 32
# include <gnu/stubs-32.h>
#elif __WORDSIZE == 64
# include <gnu/stubs-64.h>
#else
# error "unexpected value for __WORDSIZE macro"
#endif

```


On checking <bits/wordsize.h>, I found the following :-
```

#if defined __x86_64__
# define __WORDSIZE	64
# define __WORDSIZE_COMPAT32	1
#else
# define __WORDSIZE	32
#endif

```

My problem is:- should I manually define __x86_64__, or do anything else ?

Thanks in advance :)

---

### Post by Rui Pais on 2007-04-22
Hi,
sorry, don't know about your question.

Just want to point that you probabily get more answers if you ask on the [Programming section of the forum]("http://ubuntuforums.org/forumdisplay.php?f=39").
Here is for 64 bit **users** that in most don't know much about programming or C specific issues.

Good luck. 

(Maybe a mod can move your thread.)

---

### Post by rks_i1_13 on 2007-04-22
Yeah, sorry for this, i should have noticed that earlier :oops: , i have reposted it [_here_]("http://ubuntuforums.org/showthread.php?p=2506540#post2506540").

---

