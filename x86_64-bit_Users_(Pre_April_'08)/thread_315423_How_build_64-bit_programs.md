---
title: "How build 64-bit programs?"
date: 2006-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mildew on 2006-12-09
I made a small test program:

```
#include <iostream>
using namespace std;

int main()
{
  int tmp = 33554432;
  for (int i = 0; i < 10; i++) {
    tmp *= 2;
    cout << tmp << endl;
  }
}

```

The output I get is:

```
67108864
134217728
268435456
536870912
1073741824
-2147483648
0
0
0
0

```

I was sort of expecting the numbers to get a bit higher... :???: 
How do I compile 64-bit programs?

I was told to get the gnu compiler from the build-essential package.
gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)

Sorry if this is a duplicate post, just send me to the right place. :)

---

### Post by jedld on 2006-12-09
ints are still 32 bit in length by default, this was done in order to save memory. Pointers however are now in 64 bit.

---

