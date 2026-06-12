---
title: "Bug in getline (C stdio library)"
date: 2009-04-22
forum: x86 64-bit Users
---

### Post by Nycticorax on 2009-04-22
I think the C function getline is behaving incorrectly in our 64 bit version of Ubuntu 8.04 and 8.10. The problem involves getline writing to areas of memory that it shouldn't. I agree that on the face of it that sounds unlikely. Here's my test code:

```

#include <stdlib.h>
#include <stdio.h>

int main(int argc, char **argv) {
    int i=10, maxlinelength=0 ;
    char *line=NULL ;

    maxlinelength = 0 ;
    line = NULL ;
    
    printf("%d, %d\n", i, maxlinelength) ;
    getline(&line, &maxlinelength, stdin) ;
    printf("%d, %d\n", i, maxlinelength) ;
    
    return 0 ;
}

```

On 32 bit ubuntu 9.04 that prints what you'd expect:

```

10, 0

10, 120

```

(the blank line comes from me hitting return when it tries to read from stdin; you can redirect a file into it if you want)

However on 64 bit ubuntu 8.04 and 8.10 that prints out

```

10, 0

0, 120

```

I.e. it seems to me that getline has overwritten the memory location of the variable i.

The two machines that are producing incorrect results are

1)
```
ash:~> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
ash:~> uname -a
Linux ash 2.6.27-11-server #1 SMP Thu Jan 29 20:13:12 UTC 2009 x86_64 GNU/Linux


```
gcc 4.3.2

and 

2)
```
oak:~> uname -a
Linux oak 2.6.24-19-server #1 SMP Wed Aug 20 18:43:06 UTC 2008 x86_64 GNU/Linux
oak:~> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

```
gcc 4.2.4

Dan

---

### Post by davetv on 2009-04-22
I'm not sure that you are using getline() correctly. Firstly, your variable char *line has no memory allocated for the chars returned. Also, maxlinelength=0 which getline() would probably not cope with very well.

I found this link - [http://crasseux.com/books/ctutorial/getline.html#getline](http://crasseux.com/books/ctutorial/getline.html#getline)

---

### Post by Nycticorax on 2009-04-22
> **davetv said:**
> I'm not sure that you are using getline() correctly. Firstly, your variable char *line has no memory allocated for the chars returned. Also, maxlinelength=0 which getline() would probably not cope with very well.


Thanks, but actually that is valid use of getline. Say you do getline(buffer, buffer_size, file). It's quite clever -- if the line it encounters is longer than the buffer_size, then it allocs/reallocs the buffer, and updates buffer_size. *However* buffer_size is not an int, it is a size_t, and although those are the same size on 32 bit systems, they are not on 64 bit systems... so it was my fault, and that's the bug.
Dan

---

### Post by davetv on 2009-04-22
Thanks for that Dan. Learn something new every day.

---

### Post by Slim Odds on 2009-04-22
This is one of the reasons that I much prefer to use C++ instead of C.

---

### Post by Yellow Pasque on 2009-04-22
That was a great demonstration on how to write non-portable code.

---

### Post by moles on 2009-04-24
Your problem is not with getline, it is due to you using an int for maxlinelength instead of a size_t. These are the same length for your 32-bit case but for 64-bit sizeof(size_t) = 8 and sizeof(int) = 4, thus your i variable is overwritten by the MSB of maxlinelength when getline changes it.

---

