---
title: "cant use CD command in terminal"
date: 2013-09-28
forum: Wine
---

### Post by James_Cracknell on 2013-09-28
I thought I would post this in the wine section as that's what I'm trying to achieve.. run an app using wine... Please forgive me if it's the wrong place for this.

This is what I get when I try to use the cd command in the terminal. DIR command says the directory is there, and it IS there in my home folder:

uboo@ubuntu:~$ dir
Deathbolt  Documents  examples.desktop    Pictures  Templates
Desktop    Downloads  Music        Public      Videos
uboo@ubuntu:~$ cd /deathbolt
bash: cd: /deathbolt: No such file or directory

If it's of any help I'm using Ubuntu 12.04 LTS.

Thanks In Advance - A Ubuntu Newbie.

---

### Post by Toz on 2013-09-28
First thing to keep in mind is that unix is case sensitive. **deathbolt** is not the same as **Deathbolt**. Secondly, by preceeding deathbolt with a slash, you are saying "go to the deathbolt directory off of the root directory", but that is not where the Deathbolt directory is located. What you really want to do is:
```
cd Deathbolt
```

---

### Post by James_Cracknell on 2013-09-28
Ohh I see, Thanks a million! :D

---

### Post by Lars Noodén on 2013-09-28
Linux is case sensitive so you have to watch whether names have uppercase or lower case.  You can also have spaces and other weird characters in the file and directory names, but that's workable too.  

About the / at the start of the directory, that would be an indicator of an absolute path.  I can't find a good, simple explanation of how to use directories, but this might be the closest:

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

Basically, there are two ways.  You can refer to directories (or files) relative to the top of the file system hierarchy.  These are known as absolute paths or directories.  Or you can refer to directories (and files) relative to your current working directory.   These are known as relative paths or directories.  If you ever want to be sure where you are, you can use [pwd](http://manpages.ubuntu.com/manpages/raring/en/man1/pwd.1posix.html) to remind you, but the bash prompt should show that, too. 

As far as relative paths go, two dots (..) refer to whatever directory is above your current working directory.  One dot (.) refers to whatever happens to be your current working directory at the moment.

---

