---
title: "HELP: not possible to install i386.deb's on Ubuntu-9.04-x86_64"
date: 2009-05-07
forum: x86 64-bit Users
---

### Post by mickpf on 2009-05-07
Hi folks,

yesterday I installed the Ubuntu 9.04 x86_64 and tried to install some i386.deb packages (Adobe Acrobat Reader and others) with gdebi, which are not available from Ubuntu. There were no problems to install the same packages on the Ubuntu 9.04 i386.

On every try I got the message "Not possible to install i386...".

I've installed the i32-lib, but didn't solve the problem.

Can anybody help?

Kind Regards
Michael

---

### Post by b@sh_n3rd on 2009-05-07
Well, the 64bit architecture is totally alien to the usual 32bit one. In other words, the way it works is different so you've gotta get the 64bit equalent of the program...I *think*. Anyway, something like that if I remember correctly...I saw a post around here somewhere about a day ago or maybe 2, stating a similar problem...

---

### Post by mickpf on 2009-05-07
Hello b@sh_n3rd,

well, but such progies are not available for x86-64.

I searched for discussions related to my problem, found only one solution: install i32-libs. But it doesn't help.

---

### Post by Slim Odds on 2009-05-07
```
sudo dpkg -i --force-architecture foo.deb
```

There are tons of posts on this issue.....

---

### Post by jespdj on 2009-05-07
You can force-install a 32-bit .deb on 64-bit Ubuntu with the command that Slim Odds mentioned above.

But you will need to install the necessary 32-bit libraries yourself. The [getlibs](http://ubuntuforums.org/showthread.php?t=474790) script can help with this.

However, before you try all this, check if there is a 64-bit native version available of the program that you are trying to install. Adobe Acrobat Reader 8.1 for example is available from the [Medibuntu](http://www.medibuntu.org/) repository. (It's still a 32-bit program, but Medibuntu has a package for 64-bit Ubuntu which is easy to install).

---

### Post by Yellow Pasque on 2009-05-07
You can use the --force-architecture option to install x86 .debs ("Use the force" Get it? :P )

That said, you'll still need the appropriate 32-bit libs for those programs. This tool is helpful: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Also, it's best to stick with native 64-bit Linux apps when possible. For example, do you really need Acrobat Reader or does evince fulfill your PDF needs?

EDIT: I shouldn't have taken 10 minutes to hit the post button

---

### Post by mickpf on 2009-05-08
Hi folks,

Many Thanks for this advice...
I'll try it next time.

Kind Regards,
Michael

---

### Post by mickpf on 2009-05-18
Hi boys & girls,

it works as slim odds describes.

Thanks,
Michael

---

### Post by PatrickVogeli on 2009-05-18
for acrobat reader, I would suggest adding the mediubuntu.org repos and installing from there

---

