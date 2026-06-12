---
title: "gnome-keyring:i386 not on server?? Failed to download file...gnome-keyring_3.4.1-4"
date: 2012-12-10
forum: Wine
---

### Post by NoCyberDom on 2012-12-10
While battling another issue I've run across this and figured others facing different problems may also hit this point, so I separated it into it's own thread.

I attempted to install the keyring:
*sudo getlibs -p gnome-keyring:i386*

My ia32-libs was already the current version but then, after hitting Y, this is the result.

[COLOR=Red][I]Failed to download file [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.4.1-4ubuntu1~precise1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.4.1-4ubuntu1~precise1_i386.deb)
The mirrors do not have the requested file or there is no internet connection
No packages to install[/I][/COLOR]

Someone else apparently used this same solution successfully not even 24 hours before this started happening but when I used a web browser to check the mirror's directory it shows that the number sequence around 3.4.1 is skipped over. Look for yourself:

[http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/)

Tips are appreciated... thanks.

---

### Post by glypto on 2012-12-21
I have the same issue.
Any Idea how to fix this please?

---

### Post by NoCyberDom on 2012-12-21
This remains unsolved but I found a workaround... I installed 12.04 32 bit in another partition and ran the program off that.

---

