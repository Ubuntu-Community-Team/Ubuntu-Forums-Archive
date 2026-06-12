---
title: "About 32 Bits Processes on x64"
date: 2008-06-08
forum: x86 64-bit Users
---

### Post by Nullack on 2008-06-08
Hi folks :)

1. How do I query what processes are currently running on the kernel in 32 bit mode?

2. How do I query apt-get about what 32 bit packages are installed?

Thanks

---

### Post by jespdj on 2008-06-09
I don't know an answer to the first question.

For the second question, something like this should work:
```
dpkg-query -W --showformat="\${Package} \${Version} \${Architecture}" | grep i386
```
This will list packages for the i386 architecture that have been installed with dpkg --force-architecture on an amd64 system.

Note that it will not necessarily find all 32-bit programs. For example, I have Skype and Adobe Flash installed, which are both 32-bit programs, but which both came in amd64 packages.

---

### Post by Nullack on 2008-06-10
So theres heaps of x32 packages in a AMD64 hardy install :)

Wonder how many are running on the kernel?

---

### Post by Kilz on 2008-06-10
> **Nullack said:**
> [B]So theres heaps of x32 packages in a AMD64 hardy install :)
[/B]
Wonder how many are running on the kernel?

No, the 32bit applications listed are about it (flash and skype) both are closed source.

---

### Post by jespdj on 2008-06-10
> **Nullack said:**
> So theres heaps of x32 packages in a AMD64 hardy install :)
Why do you think that? I have no i386 packages on my amd64 system at all. (But that doesn't mean I don't have any 32-bit programs).

---

### Post by Jouke74 on 2008-06-10
There are also the "all" packages which work for both 32bit and 64bit. I assume they are 32 bit, and there are quite many of them.

---

### Post by John.Michael.Kane on 2008-06-10
> **Jouke74 said:**
> There are also the "all" packages which work for both 32bit and 64bit. I assume they are 32 bit, and there are quite many of them.

Programs/packages listed as (all) are architecture-independent and should be installable/shared by all machines 32bit or 64bit. They are in theory neutral packages. 

Almost all files with dedicated architecture will list it's dependent, as 32bit or 64bit.

---

### Post by Nullack on 2008-06-11
> **jespdj said:**
> I don't know an answer to the first question.

For the second question, something like this should work:
```
dpkg-query -W --showformat="\${Package} \${Version} \${Architecture}" | grep i386
```
This will list packages for the i386 architecture that have been installed with dpkg --force-architecture on an amd64 system.

Note that it will not necessarily find all 32-bit programs. For example, I have Skype and Adobe Flash installed, which are both 32-bit programs, but which both came in amd64 packages.

Has anyone got an improved version of this? When I run this I get heaps of packages that arent 32bit.

---

### Post by John.Michael.Kane on 2008-06-11
To check if a particular application you have installed is 32bit or 64bit you can try passing the file command. 

```
file /usr/bin/program name here
```

Examples:

```
file /usr/bin/skype
```

Will output the below.

```
/usr/bin/skype: **ELF 32-bit** LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.1, dynamically linked (uses shared libs), stripped
```

```
file /usr/bin/mencoder
```

Will output the below.

```
/usr/bin/mencoder: **ELF 64-bit** LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
```

---

### Post by Cappy on 2008-06-11
Ubuntu64 doesn't come with any 32-bit software at all, by default. 32-bit software is only generally needed for a few things like flash, wine, skype, etc. which is installed by the user (you).

---

### Post by jespdj on 2008-06-11
> **Jouke74 said:**
> There are also the "all" packages which work for both 32bit and 64bit. I assume they are 32 bit, and there are quite many of them.
They are not 32-bit. Programs written in for example Python or Java are really platform-independent. They run on a Python interpreter or a Java virtual machine.

The Python interpreter or the JVM are ofcourse native programs that are 32- or 64-bit, but the Python or Java program itself that you're running is not specific to one architecture.

---

### Post by Nullack on 2008-06-12
Thanks everyone :)

While weve made some progress:

1. We still dont have a working, global way of querying what 32 bit packages are installed on a machine

2. We still dont have a working method for seeing what 32bit processes are actually running on the kernel.

I know weve had some great responses but this is still open. :)

---

### Post by Cappy on 2008-06-12
To solve your bug #111282 use this: [http://www.uluga.ubuntuforums.org/showpost.php?p=4346978&postcount=7](http://www.uluga.ubuntuforums.org/showpost.php?p=4346978&postcount=7)

1) As others have mentioned, the 32-bit binaries are often install in 64-bit packages. Apt is pretty stupid when dealing with multiple architectures.

This should work for #1:
```
sudo find / -type f -exec file '{}' \; | grep '32-bit' | grep 'executable'
```

2) In the worst case, same as above but with ps. I would think there was a way to query what programs were running in compatibility mode but I don't know of one. 

The easier way is just to see what files are 32-bit on your filesystem using method #1 and then checking for those processes.

---

### Post by John.Michael.Kane on 2008-06-12
> **Cappy said:**
> To solve your bug #111282 use this: [http://www.uluga.ubuntuforums.org/showpost.php?p=4346978&postcount=7](http://www.uluga.ubuntuforums.org/showpost.php?p=4346978&postcount=7)

1) There's no way because, as others have mentioned, the 32-bit binaries are often install in 64-bit packages. Apt is pretty stupid when dealing with multiple architectures.

The only way I can imagine doing this is running a find {} and grepping file's output for "ELF 32-bit" on every single file.

2) In the worst case, same as above but with ps. I would think there was a way to query what programs were running in compatibility mode but I don't know of one.

This should work for #1:
```
cd /
find . -type f -exec file '{}' \; | grep '32-bit' | grep 'executable'
```

The user may have to pass the above command with sudo, as passing it as a standalone command will return the below errors, however. the command does work, and should output any ELF 32-bit files.

```
find: ./root/.gconfd: Permission denied
find: ./root/.gconf: Permission denied
find: ./root/.gnome2_private: Permission denied
find: ./root/.gnome2: Permission denied
find: ./root/.synaptic: Permission denied
```

---

### Post by Kilz on 2008-06-12
> **Nullack said:**
> Thanks everyone :)

While weve made some progress:

1. We still dont have a working, global way of querying what 32 bit packages are installed on a machine

2. We still dont have a working method for seeing what 32bit processes are actually running on the kernel.

I know weve had some great responses but this is still open. :)

What exactly is the purpose behind it?

---

### Post by Nullack on 2008-06-18
Simply understanding the system better :)

---

### Post by Kilz on 2008-06-18
> **Nullack said:**
> Simply understanding the system better :)

What are you trying to understand about the system?

---

