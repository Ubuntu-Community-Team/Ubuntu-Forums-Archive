---
title: "gcc problem"
date: 2006-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by eXTerminate on 2006-02-08
me again :)

gcc is the problem now. installed it (even did the "apt-get instal build-essential" thing) and when i try to compile my test program i get this output: 

proba.cpp:5: error: ‘cout’ was not declared in this scope
proba.cpp:6: error: ‘cin’ was not declared in this scope

what did i do wrong?

---

### Post by rplantz on 2006-02-09
[QUOTE=eXTerminate]
proba.cpp:5: error: ‘cout’ was not declared in this scope
proba.cpp:6: error: ‘cin’ was not declared in this scope

what did i do wrong?[/QUOTE]

(I'm assuming that you're writing in C++ and using g++ to compile.)

Did you use the namespace directive? That is, something like:
```

#include <iostream>
using namespace std;

int main() {
   int x;
   cout << "Enter a number: ";
   cin >> x;
   cout << "You entered: " << x << endl;
   return 0;
}

```

If you use <iostream.h> you will get a warning that this has been deprecated and suggesting that you use <iostream>. But if you do this and forget the namespace directive, you get the errors you show.

---

