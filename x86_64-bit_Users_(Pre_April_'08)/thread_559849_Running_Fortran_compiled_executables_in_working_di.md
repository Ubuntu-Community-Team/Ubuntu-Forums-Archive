---
title: "Running Fortran compiled executables in working directory"
date: 2007-09-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by atomicdad on 2007-09-25
I'm thinking this should be an easy problem to fix, but I can't solve it. I downloaded the gnu fortran compiler and it appears to work fine. The problem is that I can't run the executable at the command line while I am in the current directory.

Example, my fortran executable is sitting in a directory /d1/fortran_test  , when I am in the directory and type the executable a.out I get a message:
bash: a.out: command not found

If I back up one directory to /d1 and type at the command line:
./fortran_test/a.out the executable runs just fine.

I suspect there is something I need to add into my .bashrc file or something along those lines, but i'm not sure what.

Thanks, this linux newbie would appreciate any help.

---

### Post by lisati on 2007-09-25
Sometimes when you're running an executable from the current directory, you have to put "./" (without the quotes) in front of the file name

---

### Post by atomicdad on 2007-09-25
Thanks, that is pretty much what I did, and i just tried it in the current directory and it works as well. Although that seems a little awkward to have to put ./ before I run my executables or script files. Shouldn't there be something I can set in one of the bash files or something so it will recognize executable commands?

---

### Post by raid996 on 2007-10-25
I think you can by defining an alias in the **.bashrc** or in ** /etc/profile**, this way you'll just have to type the alias in the terminal and it should launch the file, you can also define the alias already with the options you use regularly with that program. Add the line:

```

alias myalias='command'

```

or with the options appended:

```

alias myalias='command --with --lots --options'

```

you can later append parameters in the terminal when invoking your alias. Just as with any other command:

```
myalias new_option
```

Hope it helped, let me know :popcorn:

---

