---
title: "Wine fails to run .exe files."
date: 2014-02-27
forum: Wine
---

### Post by Hunter_Connelly on 2014-02-27
I recently installed wine because I was interested in running windows programs in Ubuntu. I installed it from the Ubuntu Software Center, and then set it as the default application for exe files. However, when I right click and select "open" nothing happens. It doesn't even display an error message or anything. I don't know if I'm doing something wrong or if maybe it only woks with certain exe files.

The file I tried to open was a quick little console program I coded in Code::Blocks. All it does is ask you to type your name then repeats it back to you.

---

### Post by ian-weisser on 2014-02-27
Wine tries very hard to do an impossible task - to recreate as many Windows system calls as possible without seeing any of the source code.
It's possible your quick little console program, or the Code::Block framework, refers to a call that is unsupported.

You may get a definitive answer in a Wine forum.
To get a better answer here, you will need to tell us more detail about the Code::Blocks version and origin, and perhaps your little console program code.

---

### Post by Hunter_Connelly on 2014-02-28
My version of Code::Blocks is just the one on the Ubuntu Software Center. I have mine updated to the latest version. The compiler I use is GNU GCC. My console program consists of only this:
```

#include<iostream>
#include<string>

using namespace std;

string answer;
int main() {
   cout << "What is your name?" << endl;
   cin >> answer;
   cout << "Your name is " << answer << ".";
   return 0;
}

```
I am able to run it using the "build and run" button in Code::Blocks but when I try to use the actual exe file nothing happens.

---

### Post by ian-weisser on 2014-02-28
Please clarify:
Are you running codeblocks in Wine trying to generate Win executables?
Or are you running codeblocks in Wine trying to generate Linux binaries?
Or are you running codeblocks in Ubuntu trying to generate Linux binaries?
Or are you running codeblocks in Ubuntu trying to generate Win executables?

---

### Post by Hunter_Connelly on 2014-02-28
I am running codeblocks in Ubuntu trying to generate Win executables.

---

### Post by ian-weisser on 2014-02-28
Ah, then you should read [http://stackoverflow.com/questions/2033997/howto-compile-for-windows-on-linux-with-gcc-g](http://stackoverflow.com/questions/2033997/howto-compile-for-windows-on-linux-with-gcc-g)

---

