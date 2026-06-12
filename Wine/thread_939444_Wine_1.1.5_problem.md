---
title: "Wine 1.1.5 problem"
date: 2008-10-05
forum: Wine
---

### Post by juanfran27 on 2008-10-05
I downloaded version 1.1.5 of Wine from the main site and tried to download it. I did not know how to work with tar.gz files, so I followed [this quick tutorial]("http://www.cyberciti.biz/faq/install-tarballs/"). I was able to decompress the file and navigate to the newly created folder. However, when I type the ./configure command (see link) I get the following message:

configure: error: C compiler cannot create executables.

??? Please help. And please do try to keep the answers simple, since I'm new at this using-linux-with-wine-to-ditch-windows thing.

Thanks in advance.

---

### Post by Gcentrex on 2008-10-06
You will have to give information on what version of Ubuntu your using and why your trying to use the tar.gz, if your using Ubuntu/Kbuntu then download the deb for your version, or a quick google search would have brought you to this page [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb).

Their is no need to compile wine unless you have to do it after patching wine to run your application properly.

---

### Post by david_kt on 2008-10-06
> **juanfran27 said:**
> I downloaded version 1.1.5 of Wine from the main site and tried to download it. I did not know how to work with tar.gz files.

Open terminal and run:

```
sudo apt-get install wine
```

DK

---

### Post by juanfran27 on 2008-10-07
I solved it. I followed [this]("http://tuxarena.blogspot.com/2008/09/how-to-install-wine-115-in-ubuntu-804.html") guide.

---

