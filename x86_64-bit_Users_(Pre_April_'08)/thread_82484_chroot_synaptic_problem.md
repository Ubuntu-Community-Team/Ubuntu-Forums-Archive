---
title: "chroot synaptic problem"
date: 2005-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Navyblue on 2005-10-26
I have actually asked this question here:

[http://www.ubuntuforums.org/showthread.php?t=24575&highlight=howto+chroot](http://www.ubuntuforums.org/showthread.php?t=24575&highlight=howto+chroot)

But I guess now no one looked at Hoary Forums anymore.

I have been in following the how to. I am running Breezy, but still following the Hoary chroot, as someone here recommends to follow word by word unless I know what I am doing. Anyway when I reached the final step of  "sudo synaptic32", I get this:

```

(hoary) synaptic32
bash: synaptic32: command not found
dchroot: Child exited non-zero.
dchroot: Operation failed.

```

At the step of "sudo apt-get install synaptic", it doesn't seem to work. I got this message:

```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_SG:en",
        LC_ALL = (unset),
        LANG = "en_SG.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: syntax error: unknown group `postdrop' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Any clue?

Thanks :)

---

### Post by nudd on 2005-10-27
I also had this problem, but it works if you do:

```

sudo bash
synaptic32

```

However, this is really not satisfactory, because you are effectively logging into a bash shell with root privileges!

---

### Post by Navyblue on 2005-10-28
That doesn't work for me. :(

Synaptic32 isn't even installed in my case.

---

### Post by Navyblue on 2005-10-28
I have generated a few more locales version and now locale related error message stopped appearing. but I still get this at "sudo apt-get install synaptic":

```

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  defoma docbook-xml fontconfig laptop-detect libatk1.0-0 libexpat1
  libfontconfig1 libfreetype6 libglade2-0 libglib2.0-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libjpeg62 libpango1.0-0 libpango1.0-common
  libpng12-0 libscrollkeeper0 libtiff4 libvte-common libvte4 libx11-6
  libxcursor1 libxext6 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 libxslt1.1 perl perl-modules scrollkeeper sgml-base sgml-data
  ttf-bitstream-vera ucf xlibs-data xml-core xorg-common
Suggested packages:
  defoma-doc psfontmgr x-ttcidfont-conf dfontmgr docbook docbook-doc
  docbook-dsssl docbook-xsl libfreetype6-dev ttf-kochi-gothic ttf-kochi-mincho
  ttf-thryomanes ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp
  ttf-arphic-gkai00mp ttf-arphic-bkai00mp perl-doc libterm-readline-perl-perl
  sgml-base-doc perlsgml doc-html-w3 opensp libxml2-utils debhelper
  x-window-system-core x-window-system
Recommended packages:
  libft-perl libatk1.0-data libglib2.0-data hicolor-icon-theme gksu deborphan
  libgnome2-perl
The following NEW packages will be installed:
  defoma docbook-xml fontconfig laptop-detect libatk1.0-0 libexpat1
  libfontconfig1 libfreetype6 libglade2-0 libglib2.0-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libjpeg62 libpango1.0-0 libpango1.0-common
  libpng12-0 libscrollkeeper0 libtiff4 libvte-common libvte4 libx11-6
  libxcursor1 libxext6 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 libxslt1.1 perl perl-modules scrollkeeper sgml-base sgml-data
  synaptic ttf-bitstream-vera ucf xlibs-data xml-core xorg-common
0 upgraded, 42 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/16.4MB of archives.
After unpacking 70.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  perl-modules perl defoma sgml-base xml-core sgml-data docbook-xml libexpat1
  libfreetype6 libfontconfig1 ucf ttf-bitstream-vera laptop-detect fontconfig
  libglib2.0-0 libatk1.0-0 libgtk2.0-common libpango1.0-common xorg-common
  xlibs-data libx11-6 libxrender1 libxft2 libpango1.0-0 libxcursor1 libxext6
  libxi6 libxinerama1 libxrandr2 libgtk2.0-bin libjpeg62 libpng12-0 libtiff4
  libgtk2.0-0 libxml2 libglade2-0 libxslt1.1 libscrollkeeper0 libvte-common
  libvte4 scrollkeeper synaptic
Install these packages without verification [y/N]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: syntax error: unknown group `postdrop' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by Navyblue on 2005-10-28
Btw, I also get the same error at "apt-get upgrade"

---

### Post by Navyblue on 2005-10-31
Anyone?

---

### Post by queenorych on 2005-10-31
from your error you have not set your locale.  See the amd64 list.  I think apt-get install locales may do it.

---

### Post by Navyblue on 2005-11-01
[QUOTE=queenorych]from your error you have not set your locale.  See the amd64 list.  I think apt-get install locales may do it.[/QUOTE]

The error message about the locale had gone away. Now left with the "postdrop" thingie. You mean it is still locale related?

Thanks.

---

### Post by queenorych on 2005-11-01
Hmm.  Just for grins.  Try 
apt-get update;
apt-get install -f

Here's a thread on it: [http://lists.plug.phoenix.az.us/lurker/message/20040406.171001.d0868daf.en.html](http://lists.plug.phoenix.az.us/lurker/message/20040406.171001.d0868daf.en.html)

Looks to me like something like /var/lib/dpkg/statoverride  is using a postdrop group.  Did you try adding the group?  Check /etc/passwd, and /etc/group to see if it is there.  If not try just 'groupadd postdrop.  Though I'd try to see what the postdrop group is, and figure out why you don't have it.

Does everyone that has this working have a postdrop group? (I'm away from my computer)

---

### Post by Navyblue on 2005-11-01
There isn't any postdrop in the two files you mentioned. And I have created the group as you have suggested.

Now the message become:

```

dpkg: syntax error: unknown user `postfix' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

And then, I've created a user "postfix". And Synaptic got installed.

Don't ask me what postdrop and postfix are.

---

### Post by alanhaggai on 2007-02-11
This solved the problem for me:
```
sudo groupadd postdrop
sudo useradd postfix

```

---

