---
title: "Acroread on 64bit (error!)"
date: 2008-10-23
forum: x86 64-bit Users
---

### Post by stinkinrich88 on 2008-10-23
Hello, 

Regarding this post: [http://ge.ubuntuforums.com/showthread.php?t=665201]("http://ge.ubuntuforums.com/showthread.php?t=665201") which I can't reply to for some reason...

I have followed the instructions and I get this message when I try to run acroread:

> terminate called after throwing an instance of 'ASErrException'
Aborted


Any ideas?

Thanks!

---

### Post by jespdj on 2008-10-23
The easiest way to install acroread is via [Medibuntu](http://www.medibuntu.org). Add the Medibuntu repository as described on the website, then simply install it with
```
sudo apt-get install acroread
```

---

### Post by cariboo on 2008-10-23
I have to agree using the Medibuntu repositories, is way easier than the way suggested in the link you provided. An added benefit is that you can also get libdvdcss2 from the same repository, so that you play dvd's.

Jim

---

### Post by stinkinrich88 on 2008-10-23
thanks for your replies, guys. I think I've messed something up pretty bad here:

I made sure I had uninstalled acroread. I had uninstalled it but I could still run it from the command line. Weird! Anyway, I went on to install acroread from the repository. It gave me this output:

> dpkg: error processing /var/cache/apt/archives/acroread_8.1.2.su1-0.0medibuntu0.8.04.1_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_8.1.2.su1-0.0medibuntu0.8.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


So I sudo rm /usr/bin/acroread and try to install it again and I get the same message (but I can no longer run acroread from the terminal). It still thinks acroread exists when I deleted it!

Any ideas?

thanks!

p.s. I tried to uninstall adobereader-enu and it tells me it isn't installed

---

### Post by cariboo on 2008-10-23
Try:

```
sudo apt-get purge acroread
```

This should remove all traces of acroread.

Jim

---

### Post by stinkinrich88 on 2008-10-24
> **cariboo907 said:**
> Try:

```
sudo apt-get purge acroread
```

This should remove all traces of acroread.

Jim

I already tried this one, still no luck!

---

### Post by stinkinrich88 on 2008-10-24
ooh, I managed to install acroread (and plugins etc) from the medibuntu repository. 

(i first downloaded the package from medibuntu's website, forced it to install with sudo dpkg -i --force-all Desktop/acroread_8.1.2.su1-0.0medibuntu0.8.04.1_amd64.deb then uninstalled it with sudo apt-get purge acroread)

so that's all sorted, but I still get the exact same error message on execution...

any ideas?

thanks!!

---

### Post by K.Nuebler on 2009-02-16
Hi, 
I have exactly the same problem and I followed the ideas described here.
Sadly, I get also exactly the same result as stinkinrich88. Have you solved the problem? 
Did anyone else do?

thanks!

---

### Post by stinkinrich88 on 2009-02-16
Hi K.Nuebler. Unfortunately I never got to the bottom of this problem. However, I can now run acroread because I re-installed Ubuntu (for other reasons). Sorry, I can't help!

---

### Post by stchman on 2009-02-16
Unless you need something really specific in Adobe Acrobat reader just use Evince document viewer.

---

### Post by BryanFRitt on 2009-05-09
I tried the 
*sudo ./AdbeRdr9.1.0-1_i486linux_enu.bin*
and the
*sudo apt-get install acroread acroread* acroread-escript* acroread-plugins* mozilla-acroread**
ones, and on both I type:
*acroread*
and get:
[FONT="Courier New"]terminate called after throwing an instance of 'ASErrException'
Aborted[/FONT]

How can I run Acrobat Reader?

I found this site:
[http://brneurosci.org/linuxsetup101.html](http://brneurosci.org/linuxsetup101.html)
which says:

> Acroread crashes with the message: terminate called after throwing an instance of 'ASErrException', Aborted. This uninterpretable message gives no clue what is wrong with it. The same problem occurred when I downloaded a new version from Adobe's Website.  Solution:  Install all the 32-bit packages, especially any 32-bit libraries, from the DVD. These should be listed as dependencies, but aren't. 

I know it's talking about OpenSUSE 11.0 instead of Ubuntu based systems but it sounds close enough to use. I don't know how to do what it's saying. I do have ia32-libs installed, if that's what it's asking for.

Really I guess I'm wanting to install Acrobat Reader so that I can print a file. All the readers I've tried so far are not printing right, or give an error message when I try to print. The ones that print only print the left hand side of the page on the right had side. On the programs that have print preview, the preview it looks like they are assuming my paper is twice as wide as it is, and they are centering the image on that page. I'm using standard 8.5"x11" paper, not 17"x11" paper. Any help one this would be appreciated too.

Thanks for any help,

BryanFRitt

p.s.
I'm currently using KUbuntu 8.04.2 64 bit (I might upgrading again one day though)

---

### Post by Yellow Pasque on 2009-05-10
You should have purged adobereader-enu before trying to install the medibuntu version of acroread (and then trying to install another version).

I wish I had some advice on how to clean up the mess but.. good luck. :\

---

### Post by dwightpaige79 on 2009-05-10
Here's how I did it:

[http://ubuntuforums.org/showthread.php?p=7252065#post7252065](http://ubuntuforums.org/showthread.php?p=7252065#post7252065)

---

### Post by BryanFRitt on 2009-05-11
> **Temüjin said:**
> You should have purged adobereader-enu before trying to install the medibuntu version of acroread (and then trying to install another version).

I wish I had some advice on how to clean up the mess but.. good luck. :\

I tried to install this using *aptitude* instead of *apt-get* when *apt-get* wouldn't let me do it, and now I have a big mess, and I don't know how to fix it. Can't fully install/uninstall *adobereader-emu*, etc... using either software yet I get this error:

*sudo apt-get install acroread*
[FONT="Courier New"]Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  acroread-plugins mozilla-acroread
The following NEW packages will be installed:
  acroread
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/29.5MB of archives.
After this operation, 73.9MB of additional disk space will be used.
(Reading database ... 276309 files and directories currently installed.)
Unpacking acroread (from .../acroread_8.1.3-0medibuntu0.8.04.1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_8.1.3-0medibuntu0.8.04.1_amd64.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/acroread.1.gz', which is also in package adobereader-enu
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_8.1.3-0medibuntu0.8.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]

p.s. after this I think I'll stick to apt-get, and not try aptitude anymore. Maybe this has something to do with the "Super Cow Powers" that apt-get has that aptitude doesn't. (see the --help pages)

---

### Post by Yellow Pasque on 2009-05-11
Can you purge adobereader-enu ?
```
sudo dpkg -P adobereader-enu
```

---

### Post by BryanFRitt on 2009-05-12
> **Temüjin said:**
> Can you purge adobereader-enu ?
```
sudo dpkg -P adobereader-enu
```

Thanks! Acrobat Reader at least it back to being able to be installed now, but I'm still getting the error when I run:
*acroread*
[FONT="Courier New"]terminate called after throwing an instance of 'ASErrException'
Aborted[/FONT]

---

### Post by BryanFRitt on 2009-05-12
> **BryanFRitt said:**
> Really I guess I'm wanting to install Acrobat Reader so that I can print a file. All the readers I've tried so far are not printing right, or give an error message when I try to print. The ones that print only print the left hand side of the page on the right had side. On the programs that have print preview, the preview it looks like they are assuming my paper is twice as wide as it is, and they are centering the image on that page. I'm using standard 8.5"x11" paper, not 17"x11" paper. Any help one this would be appreciated too.

*kghostview*, and *evince* print the margins correctly on the document I was trying to print, but *kpf* does _not_, looks like it was taking the page size from the first page in the pdf, instead the pages that were getting printed.

I filled a bug report out about *kpdf*
[https://bugs.kde.org/show_bug.cgi?id=192511](https://bugs.kde.org/show_bug.cgi?id=192511)

---

