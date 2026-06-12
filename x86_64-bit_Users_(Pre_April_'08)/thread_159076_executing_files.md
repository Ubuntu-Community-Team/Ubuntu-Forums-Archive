---
title: "executing files"
date: 2006-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by wilstoff on 2006-04-12
Ok i'm really lost here.  I'm used to using red hat linux that my school has so i'm kind of a newb on ubuntu.  I want to be able to program in my amd64 setting some c++ files.  Say for example i have a .cxx file and i g++ it to make and executable called "bob".  Now for the love of god i can't figure out how to run this on my system.  I type bob and it says 

bash: bob: command not found

Well of course bob is not a command its a filename and i want it to run.  So obviously i'm confused here on something very simple.  I know when i program on my school's machines with red hat all i have to do is type the name on the command line and it runs.  What am i missing?

---

### Post by localzuk on 2006-04-12
you need to have it set to be executable (chmod +x bob) and then run it like ./bob (or sh bob).

---

### Post by xenmax on 2006-04-12
Since it seems like you have experience in this stuff, i guess you would have already made the file executable like localzuk mentioned. What could be is that in red hat machines in your school, the PATH variable might contain '.' - the current directory. If that is present in your directory, you just need to type for ex: "bob" to run it. If not, you need to supply its path to shell, like "./bob" as localzuk mentioned.

Do ```
echo $PATH
``` do view your PATH settings. If you prefer you can add '.' to your PATH like this;
```
export PATH=$PATH:.
```
EDIT: And if you want this change permanently, you can add above piece of code to your .bashrc (if your shell is bash - guess what- the code only works for bash anyway :wink)

---

### Post by localzuk on 2006-04-12
Also, if the partition is mounted so that executable files cannot run in the /etc/fstab file, you may have issues - this is routinely done on home directories and temporary file areas (/tmp).

---

### Post by wilstoff on 2006-04-12
Thanks alot that PATH definetly helped.  I knew it was something simple.

---

