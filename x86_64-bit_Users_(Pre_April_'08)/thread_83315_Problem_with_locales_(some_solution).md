---
title: "Problem with locales (some solution?)"
date: 2005-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Eleka on 2005-10-28
Hello

I posted a days ago a question in one post to resolve my troubble with locales in my Ubuntu 64.

After investigate a little, I find that the dpkg-reconfigure locales have a issue that make it crashes and have a "segmentation fault". Then I discover that the problem were in the locale-gen script ... but, when I compare it with other locale-gen in other computer, it's the same ... and in one it works and in mine, it crashes.

I began to read the code of the script, and I found a line that, I think, is the problematic one:

while read locale charset ...

The "while" and the "read" I think are OK, but when I execute "locale charset" in one computer working OK, it doesn't return anything at the terminal, but in mine, it returns that:

```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```

If you think that I forgot to install my language-packs, I did it, it's all intalled ...

Can somebody help me?

Thanks a lot and excuse my poor english!

---

### Post by Eleka on 2005-10-28
I found that the problem is exactly with the command localedef, that is executed in the "while" loop ... How can a executable file providad with my Ubuntu CD are bad compiled???

How can I resolve that?

---

### Post by Navyblue on 2005-10-28
Have you tried "dpkg-reconfigure locales" to enable those locale?

---

### Post by Eleka on 2005-10-29
Yes, and dpkg-reconfigure locales uses locale-gen script, and it fails when runs localedef .... 

Yesterday I tried to run localedef in the same way that the script do, and I've the same segmentation fault. .. Can be a bug in the localedef program?

---

### Post by Eleka on 2005-11-02
Somebody knows somaething about this?

I'm very confused .... The libc6 package are making my system unstable at all and I can't use Ubuntu on this desketop ...

Can somebody help?

---

### Post by kawinter on 2005-11-07
[QUOTE=Eleka]Somebody knows somaething about this?

I'm very confused .... The libc6 package are making my system unstable at all and I can't use Ubuntu on this desketop ...

Can somebody help?[/QUOTE]

I am having the exact same problem.  I have been told to run locale-gen but when I do the system crashes and reboots.  I cannot run apt-get install because that causes the LOCALE error to come up and the system crashes and reboots.  I have googled this and find the error mentioned clearly in many forums but no "fix" clearly mentioned.  A lot of guesses, none of which has worked for me.  I am also running the 64bit package of Breezy Badger.

---

### Post by Eleka on 2005-11-08
I reported it some days ago to the Ubuntu bugzilla, and I'm working on it to discover whre is the problem: I know that localedef is the binary that fails, but I don't know why.

To test it, I want to install libc6-gdb (the package that contains localedef with debugging symbols), but when I run localedef, is the localedef of libc6 "normal", and I don't want to uninstall the libc6 pckage because more than 900 packages will be deleted with it ....

I'm waitting for a answer of the bugzilla people, when I know something, I will say ...

---

### Post by kawinter on 2005-11-08
[QUOTE=Eleka]I reported it some days ago to the Ubuntu bugzilla, and I'm working on it to discover whre is the problem: I know that localedef is the binary that fails, but I don't know why.

To test it, I want to install libc6-gdb (the package that contains localedef with debugging symbols), but when I run localedef, is the localedef of libc6 "normal", and I don't want to uninstall the libc6 pckage because more than 900 packages will be deleted with it ....

I'm waitting for a answer of the bugzilla people, when I know something, I will say ...[/QUOTE]

I hope I understand the answer when you get it :)  I am so much more of a newbie than you are.  Right now I am feeling like my only choices are to  switch distros.  Maybe if I went to the regular Debian for AMD 64 I would not be having so many problems, or maybe Fedora.

---

### Post by Psquared on 2005-11-08
Same problem here -- but a little different.

Whenever I try to compile or even install a program I get a warning, either by GTK or Perl saying that it is unable to 

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

or;

Perl warning: unable to set locale: No such file or directory.

This started after I installed Enlightenment. There are several modules which have to be compiled and it simply borks on the ./autogen.sh script.

I have run the dpkg-reconfigure locales so many times I am sick of it.

Please somebody come up with a solution.

I found a very technical website dealing the locale issue and Perl, but I couldn't make heads nor tails of it.

---

### Post by kawinter on 2005-11-10
Well I gave up.  I've fought with the locales problem for days and I need the computer to work and work reliably.  I wiped Ubuntu and installed straight Debian which seems to be working much better.  Best wishes to all the users on the Ubuntu forum.

---

### Post by Eleka on 2005-11-12
Well, I have notices. Good notices, but not perfect notices at all ...

I contue testing some things and I discover that localedef only crashes when the charset used is UTF-8 ... I generated various locales (es_ES and es_ES@euro) that uses ISOs charmaps and localedef generates it prefectly.

But now eith UTF-8: I tested with es_ES.UTF-8, es_AR.UTF-8 and the 2 give me segmentation fault :(

Are something at the same point with this problem???

---

### Post by kawinter on 2005-12-13
[QUOTE=Eleka]I reported it some days ago to the Ubuntu bugzilla, and I'm working on it to discover whre is the problem: I know that localedef is the binary that fails, but I don't know why.

To test it, I want to install libc6-gdb (the package that contains localedef with debugging symbols), but when I run localedef, is the localedef of libc6 "normal", and I don't want to uninstall the libc6 pckage because more than 900 packages will be deleted with it ....

I'm waitting for a answer of the bugzilla people, when I know something, I will say ...[/QUOTE]

Eleka - I looked for this bug in bugzilla so I could confirm it and I could not find it.  Could you give me the bug number?

---

### Post by Toxicity on 2005-12-13
I can also give a verbal confirmation, here's my hang up though (keep in good mind I am fairly lost in the technical aspects of anything revolving around linux because as of now I'm a fairly new convert.) I (and I could be wrong) have been recieving this error since my first package install on this system. With the self obtained iso which I installed it with previously I had no error resembling this, but when my shipit cds arrived for good measure, and time passing I installed with that opposed to my solf obtained iso. And to be sure we all know where I'm at, the gist of my errors are like this:

#dpkg-reconfigure locales

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

ah and, in running some scripts I recieve something like:

(zenity:14420): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

Assuming that since my locale is screwed it reads it as an unsupported locale?

---

### Post by Eleka on 2005-12-13
The bug number is 18890 ... I didn't use Ubuntu anymore in my amd64 desktop, but I will try to help to repair it to people that wants Ubuntu at all ....

If need something more I will read tis thread

---

### Post by DrGkill on 2005-12-27
[QUOTE=Psquared]Same problem here -- but a little different.

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

[/QUOTE]

Set your user as root, then,

$ export LC_CTYPE=C
$ export LC_MESSAGES=C
$ export LC_ALL=C

After that, you can retype :

$ dpkg-reconfigure locales

P.S : Be carefull when selecting locales. Select just all en_US* locales and deselect the others. Then, select en_US-UTF-8 as the default locale. It'll be sufficient.

That's it.

Enjoy ;)

---

### Post by StarQuake on 2006-04-22
I had the same problem, somehow the package 'language-pack-en-base' was not installed. I installed it and did dpkg-reconfigure locales and it was fixed. Might help some people.

---

### Post by incubus on 2006-04-25
Thanks, that did the trick.
Funny that debootstrap doesn't install it. "ubuntu-mimimal" should depend on something like that, although I see the problems of internationalization.

incubus

---

### Post by pek on 2006-06-20
[QUOTE=DrGkill]Set your user as root, then,

$ export LC_CTYPE=C
$ export LC_MESSAGES=C
$ export LC_ALL=C

After that, you can retype :

$ dpkg-reconfigure locales

[/QUOTE]

doesn't work when you switch back to user. one must export while user, then it works.

#-o

---

### Post by uantuzri on 2007-02-03
Have a look into this thread:
[http://www.ubuntuforums.org/showthread.php?p=2090770#post2090770](http://www.ubuntuforums.org/showthread.php?p=2090770#post2090770)

---

