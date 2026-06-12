---
title: "Pointer c"
date: 2008-10-09
forum: x86 64-bit Users
---

### Post by Vishnu V on 2008-10-09
I have problem for ponter c compiler

i just tried to execute the following code 
#include<stdio.h>
main()
{
int *a,*b;
scanf("%d%d",a,b);
}              

and i entered a no:
eg: 5
 and i got the error message "Segmentation fault"

in our college we are using REDHAT linux and it has the same problem 
pls suggest me a solution

---

### Post by jespdj on 2008-10-09
This belongs in the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forum, not in the 64-bit forum.

You get a segmentation fault because the pointers a and b are not initialized. In other words, they point to a random location in memory. Then you're telling the scanf function to read some data and write it to the random locations that a and b point to. The result is a segmentation fault. It's not a proble with Ubuntu or Red Hat; your program is faulty.

Try doing something like this:
```
#include<stdio.h>
main()
{
int a,b;
scanf("%d%d",&a,&b);
} 
```
What this does: You create two integers a and b, and pass their addresses to scanf, to let scanf know where those two integers are in memory, so that it can write whatever it reads to the two integers.

---

