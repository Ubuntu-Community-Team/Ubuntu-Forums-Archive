---
title: "wine error does not want to play mshearts.exe???"
date: 2008-07-03
forum: Wine
---

### Post by ramaswamyps on 2008-07-03
ramaswamy@ramaswamy-laptop:~$ wine mshearts.exe 
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
wine: could not load L"Z:\\home\\ramaswamy\\mshearts.exe": Module not found
ramaswamy@ramaswamy-laptop:~$ preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report


is it wine problem/config problem? how to solve?

---

### Post by kellemes on 2008-07-04
Have yo checked [this place]("http://appdb.winehq.org/appview.php?iVersionId=4876") for tips?

---

### Post by ramaswamyps on 2008-07-04
you mean to say i have to get new hearts.exe?
it works if log in as root with same version running.
just copied the exe and dll from windows to home
i will try the new version also.
thanks for a reply:)

---

### Post by ramaswamyps on 2008-07-05
no matter what i tried it says same thing.
dos mem set up problem.:(

---

### Post by VMC on 2008-07-05
I've used most of Windows card games without incidence. 

What ubuntu version are you running, and what version of Wine?

---

### Post by ramaswamyps on 2008-07-05
wine-0.9.59
ubuntu-8.04 uptodate 
kde also installed.
in root login wine works fine.
user dos env it is not working.
the error is 

ramaswamy@ramaswamy-laptop:~$ wine
preloader: Warning: failed to reserve range 00000000-60000000
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
ramaswamy@ramaswamy-laptop:~$ wine mshearts.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"H:\\mshearts.exe": Module not found
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
ramaswamy@ramaswamy-laptop:~$ preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

except for wine sol.exe error is same for any win applications.
solitaire comes up after this error output.

---

### Post by VMC on 2008-07-06
> **ramaswamyps said:**
> wine-0.9.59


I think that older version of Wine might be your problem. As I recall, there was/is a fix on that error of yours. It had something to do with some module of the kernel and security. It was all fixed with the release of Wine 1.0

Remember, you have to remove any old Wine installs if you do decide to install the newest one. They are in the repositories.

---

### Post by ramaswamyps on 2008-07-07
i updated 2 3 times.
wine shows same 0.9.59 only latest.in synaptic
should i add some repository?
which one?

---

### Post by p_quarles on 2008-07-08
Moved to the Wine section.

---

### Post by V for Vincent on 2008-07-08
go to the download section of winehq.org to find out how to get the latest version.

---

