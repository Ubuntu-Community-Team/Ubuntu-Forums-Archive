---
title: "[SOLVED] another wine question?"
date: 2007-12-21
forum: Wine
---

### Post by tech9 on 2007-12-21
Could someone tell me how you execute a single exe from a path...

I put all my exes in my /home/AMD dir

but obliviously cannot change directories to cd /home/AMD

I have successfully installed small programs from CD...

```
wine /media/cdrom0/ICS.exe
```

But, when I try to execute an exe from a path in my system, I get...

wine: cannot find /"folder"/file.exe

---

### Post by cogadh on 2007-12-21
You can most certainly "cd" to /home/AMD, its just that normally when you open a new terminal you are already in that directory (provided that "AMD" is the user name you logged in as). If that is your home directory and the executable you are trying to run is already in that directory, then all you need to do is open a terminal and type "wine <executable name>.exe".

---

### Post by tech9 on 2007-12-21
> **cogadh said:**
> You can most certainly "cd" to /home/AMD, its just that normally when you open a new terminal you are already in that directory (provided that "AMD" is the user name you logged in as). If that is your home directory and the executable you are trying to run is already in that directory, then all you need to do is open a terminal and type "wine <executable name>.exe".

ok , I did tried this... 
```

AMD@AMD-desktop:~$ cd /home/AMD
AMD@AMD-desktop:~$ wine /ICS/ICS.exe

```and I got this...
```

wine: cannot find '/ICS/ICS.exe'

```the command line points me back to desktop... I must be doing something wrong here?

The ICS.exe is under a directory called ICS under /home/AMD

I eventually figure this out... Thanks for the help

---

### Post by tech9 on 2007-12-21
really weird that I am having problems executing this from the terminal.

Anyway I marked the thread as Solved because I was able to right-click the exe and execute it with wine! :)

---

### Post by cogadh on 2007-12-21
It didn't work because of how you entered the path to the executable. By starting the path with "/" you are telling Wine that the executable is contained in a directory on the root of the drive, like /home, /etc, /usr, etc.

What you should do is either "cd" all the way to the directory containing the executable or run it like this:
```
wine ~/ICS/ICS.exe <---note the "~", that indicates "in the current user's home directory"
```
OR
```
 wine ICS/ICS.exe <--note there is no leading "/", that indicates "in the current directory"
```

---

### Post by tech9 on 2007-12-26
> **cogadh said:**
> It didn't work because of how you entered the path to the executable. By starting the path with "/" you are telling Wine that the executable is contained in a directory on the root of the drive, like /home, /etc, /usr, etc.

What you should do is either "cd" all the way to the directory containing the executable or run it like this:
```
wine ~/ICS/ICS.exe <---note the "~", that indicates "in the current user's home directory"
```OR
```
 wine ICS/ICS.exe <--note there is no leading "/", that indicates "in the current directory"
```

I did try cd / to the directory.

I figured it out, I had a space in between the folder name ICS SYS instead of ICS_SYS, but it is strange when it didn't work when I renamed the folder to ICS... oh well - all fixed :)

---

