---
title: "32-bit version of libX11.a"
date: 2008-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by matrim33 on 2008-02-18
Hi, I'm hoping that someone will be able to help me with a problem I am having. I am trying to install HTK on my 64-bit Feisty Fawn Ubuntu, but i am running into a problem.

When I ran the Make scripts (after running ./configure) I received these two errors:

/usr/bin/ld: skipping incompatible /usr/lib/libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/libX11.a when searching for -lX11

After doing some research, I found that the reason I was getting these errors was because HTK was attempting to use the 64-bit versions of libX11.so and libX11.a (HTK is a 32-bit program, so this was causing a problem). I was able to get past the first error by creating a symbolic link in /usr/lib/ linking to the libX11.so located in /usr/lib32/

My problem is this: it appears that I do not have a 32-bit version of libX11.a - i have run a locate on libX11.a and the only thing that comes up is the 64-bit version - there is no libX11.a in /usr/lib32/. I have done extensive googling on this problem, but have yet to come up with a solution.

Does anybody have an idea on how i can get past this problem? Is there a package that I am missing? Is there any way that I can compile a 32-bit version of libX11.a on my own?

Any help would be very much appreciated. Thanks in advance.

-Matrim

---

### Post by Kilz on 2008-02-18
The answer can be found by reading the stickies and doing a search for 32bit libs
[Getlibs.]("http://ubuntuforums.org/showthread.php?t=474790&highlight=skype")

---

### Post by matrim33 on 2008-02-25
Thanks for your very quick reply Kilz.  I have been bogged down at work, so this is the first time I've had a chance to try your suggestion.  I have installed getlibs and attempted to get the files I need.  Here is the command I ran to do this:

$getlibs -l libX11.a

Here is the output I get:

No match for libX11.a
No packages to install


I also tried: $getlibs -l libX11   but I get the same error. (i also tried "getlibs -l libX11.so" but this didn't find a package either)

I read through the postings for getlibs, but did not find an immediate answer.  I have to run now, but I will look at getlibs some more tonight or tomorrow morning to see if I can figure this out.  In the mean time, do you have any ideas as to why getlibs isn't finding libX11.a?  should I be using getlibs on a different file?

I will post any progress that i make.

Thanks again for your help.

-Matrim

---

### Post by Cappy on 2008-02-25
Both are in package libx11-dev which can be installed:
```

sudo getlibs -p libx11-dev

```

Getlibs isn't working because of a change to the ubuntu package interface. You haven't done anything wrong.

---

### Post by matrim33 on 2008-02-25
Awesome.  Thanks for your help guys.  Cappy, I have to agree with everyone else - your script works great.

Thanks again.

---

