---
title: "how do you run programs thru the terminal?"
date: 2008-06-10
forum: Wine
---

### Post by Meow27 on 2008-06-10
ive been trying to figure out how to get the terminal output for the programs i run in Wine. 

in the terminal, anything i type after wine basically gives me this.

if i type cd this will happen
```
wine cd
wine: could not load L"C:\\windows\\system32\\cd.exe": Module not found

```

im sure this is posted somewhere but i just cant find it.

---

### Post by cogadh on 2008-06-11
It looks like you are mixing commands. What you want to do is change directories (cd) to the application's install directory, *then* run the executable with Wine:
```
cd ~/.wine/drive_c/Program\ Files/<install directory>
wine <executable name>.exe
```

Oh, and the best place to find info like this is in the Wine Wiki and FAQ:
[http://wiki.winehq.org/FAQ#head-3b297df7a5411abe2b8d37fead01a2b8edc21619](http://wiki.winehq.org/FAQ#head-3b297df7a5411abe2b8d37fead01a2b8edc21619)

---

### Post by Meow27 on 2008-06-11
that wasn't very helpful but i found that dragging the executable to the terminal worked :/

thanks though

---

### Post by cogadh on 2008-06-11
I basically gave you the entire command you would need to run, you just needed to replace the "<install directory>" and "<executable name>" with the actual install directory and executable name of the application you are trying to run. If you do not understand very basic terminal usage like that, then I suggest you spend some time learning how to actually use Linux before you try to use something as potentially complicated as Wine. 

Dragging the executable into the terminal Window will work (sort of) but you will likely encounter bugs because you didn't change directories to wherever the executable was located first. As was explained in the FAQ page I linked to "Windows programs will often look for files in the location they were started from", so if you don't start them from where they are installed, they have problems finding needed support files, such as specific DLLs.

---

### Post by Meow27 on 2008-06-11
its not that.... its just the path for that program was so long i always wrote it wrong :P

whenever i try those commands with that program it didn't work for me........other programs (with smaller paths) did work...

---

### Post by cogadh on 2008-06-11
When using the terminal, use the TAB key to autocomplete directories. Just type the first few letters of the directory name you need, hit TAB and it will autofill the rest of that name for you, that way you don't have to worry about misspelling or anything. For example, typing this:
[INDENT]cd .wi<TAB>[/INDENT]
ends up with this:
[INDENT]cd .wine/[/INDENT]
you can then add to it by continuing to type with the next directory you are trying to get to:
[INDENT]cd .wine/dri<TAB>[/INDENT]
which will then complete that directory name so you now have this:
[INDENT]cd .wine/drive_c/[/INDENT]
Repeat within the command for the entire directory path you need and you will never have to worry about mistyping it.

---

### Post by Meow27 on 2008-06-11
whoa thanks! thats really helpful

---

### Post by MacAnthony on 2008-06-11
Also if you hit tab twice, it will give you a list of posible entries. So get your path to Program Files and hit <tab> <tab> and see what directory paths are possible.

---

