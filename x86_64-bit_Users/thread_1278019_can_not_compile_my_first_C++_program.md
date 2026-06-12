---
title: "can not compile my first C++ program"
date: 2009-09-29
forum: x86 64-bit Users
---

### Post by zardosht on 2009-09-29
Hi guys,

Im trying to learn C++, but when i try to compile my "Hello World" program I got error.

OS: ubuntu 9.04 64 bit

> program name: 1stprog.cpp written in vim 

>installed already:

apt-get install gcc
apt-get install build-essential
apt-get install g++

apt-get install libstdc++5
apt-get install ia32-libs
apt-get install lib32stdc++6
apt-get install libc6-dev-i386
apt-get install gcc-multilib
apt-get install g++-multilib


> source:

#include <iostream>
int main()
{
cout << "Hello World!";
return 0;
}


> errors:

1stprog.cpp: In function ‘int main()’:
1stprog.cpp:5: error: ‘cout’ was not declared in this scope

--------------------------------------------------

any idea?
thanx in advance.

---

### Post by mhh91 on 2009-09-29
try adding "void" after "int" and removing the "return 0;" line

---

### Post by wojox on 2009-09-29
```
#include <iostream>

using namespace std;

int main()
{
    cout << "Hello World!" << endl;
    return 0;
}
```

Then in the terminal:

```
g++ 1stprog.c -o 1stprog
```

Then:

```
./1stprog
```

---

### Post by jediborger on 2009-09-29
I know your frustration. You are doing everything right, except that your cout command comes from the std (standard) library. So it should look like this:
```
include <iostream>

int main() {
std::cout << "Hello World!" << std::endl;
return 0;
}
```
I added the std::endl so that this is printed on its own line. Go ahead and try it without the second part, you will see what I mean. Your main method should always return and int, 0 for success, this is standard posix practice and any other number means an error, but anyways . . . To compile just issue:
```
g++ file.cpp -o hello
```
Change the filename and output to suit your needs.

Now if in the future you see yourself typing std:: a lot then you can use a namespace to specify that all methods in your code are from the std library, so your code would look like this:
```
include <iostream>

using namespace std;

int main() {
cout << "Hello World!" << endl;
return 0;
}
```
Hope that helps solve some confusion.

---

### Post by noerrorsfound on 2009-09-29
> **mhh91 said:**
> try adding "void" after "int" and removing the "return 0;" line
His error message clearly stated the problem and the two posters above me provided valid solutions. You, on the other hand...:lolflag:

---

### Post by TheBuzzSaw on 2009-09-29
I have not seen a void-main program in ages.

---

### Post by zardosht on 2009-09-30
thank you all guys for useful notes,

just by adding 

using namespace std;

everything worked fine.

thank u again :)

---

