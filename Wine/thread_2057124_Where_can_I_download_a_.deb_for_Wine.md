---
title: "Where can I download a .deb for Wine?"
date: 2012-09-13
forum: Wine
---

### Post by aligator12 on 2012-09-13
I am going to perform an offline install. Thanks.

---

### Post by GeForce 9500GT on 2012-09-13
You can download it [here]("http://www.winehq.org/download/").

---

### Post by aligator12 on 2012-09-13
> **GeForce 9500GT said:**
> You can download it [here]("http://www.winehq.org/download/").
Where? when I click ubuntu it requires an internet connection which  the computer I am going to install it to does not have. And I am not sure what to make of the debian download sections.

---

### Post by GeForce 9500GT on 2012-09-13
> **aligator12 said:**
> Where? when I click ubuntu it requires an internet connection which the computer I am going to install it to does not have. And I am not sure what to make of the debian download sections.
 
Do you have computer with internet connection? Looking at your reply i really believe that you want ot do something which can't be done. You ask where you can download the .deb package of Wine and you want to do it with a computer without any network/internet connection :confused: Pretty impossible....

---

### Post by aligator12 on 2012-09-13
> **GeForce 9500GT said:**
> Do you have computer with internet connection? Looking at your reply i really believe that you want ot do something which can't be done. You ask where you can download the .deb package of Wine and you want to do it with a computer without any network/internet connection :confused: Pretty impossible....
No, I want to download wine's .deb with this computer and copy it to a flash drive. :)

---

### Post by Lars Noodén on 2012-09-13
Best get it from the Ubuntu download web site.  You can find the address in your copy of /etc/apt/sources.list and browse down to W for wine in the Universe repository.  

Or if you have installed WINE recently on your computer it and its dependencies should still be in your cache.  In that case check /var/cache/apt/archives/

---

### Post by aligator12 on 2012-09-13
> **Lars Noodén said:**
> Best get it from the Ubuntu download web site.  You can find the address in your copy of /etc/apt/sources.list and browse down to W for wine in the Universe repository.  

Or if you have installed WINE recently on your computer it and its dependencies should still be in your cache.  In that case check /var/cache/apt/archives/
Can you please give me a link? Thanks.

---

### Post by Lars Noodén on 2012-09-13
I can give you the link in *my* sources.list file:

[http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/)

You want to substitute "fi" for the [ISO-3166 country code](http://www.iso.org/iso/country_names_and_code_elements) for the country you are in right now.  That will hook you up with the closest mirror.

Note, you'll have to download any dependencies manually.  Getting the file(s) from /var/cache/apt/archives/ is faster.

---

### Post by mastablasta on 2012-09-13
you cna use synaptic package manager to download the packages for offline install.
 
another option is keryx: [http://keryxproject.org](http://keryxproject.org)

---

### Post by GeForce 9500GT on 2012-09-13
[This is the link to the pool]("http://archive.ubuntu.com/ubuntu/pool/universe/w/"). Scroll down to Wine and there's everything. But what was wrong with the link i provided you in [post #2]("http://ubuntuforums.org/showpost.php?p=12235644&postcount=2")??

---

### Post by Bucky Ball on 2012-09-13
*Thread moved to **Wine***

---

### Post by aligator12 on 2012-09-13
Sooooo.... if I download all of the x86 debs, from here:
[http://archive.ubuntu.com/ubuntu/pool/universe/w/wine1.4/](http://archive.ubuntu.com/ubuntu/pool/universe/w/wine1.4/)

that is all i will need for a successful wine install?

---

### Post by Lars Noodén on 2012-09-13
You will also need to download and install the packages that WINE depends on.   You can see the immediate dependencies with [apt-cache](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-cache.8.html)

```

apt-cache depends wine1.4

```

Note that some of the dependencies might have dependencies of their own and so on.  There must be an easy way to find and download all them but I do not know it.

One hack might be to uninstall WINE, clear the cache and then re-install it.  Then copy all the .deb files from the cache.

```

sudo apt-get remove wine
sudo apt-get autoremove
sudo apt-get clean

sudo apt-get install wine
cp /var/cache/apt/archives/*.deb /media/usbstick/.

```

Scratch all that.  I did an installation of WINE on a clean machine (12.04) and here are the contents of /var/cache/apt/archives after installing:

```

binfmt-support_2.0.8_i386.deb
cabextract_1.4-1_i386.deb
fonts-droid_20101110+git-2_all.deb
fonts-horai-umefont_434-1_all.deb
fonts-unfonts-core_1.0.3.is.1.0.2-080608-5ubuntu1_all.deb
gettext_0.18.1.1-5ubuntu3_i386.deb
gnome-exe-thumbnailer_0.9-0ubuntu1_all.deb
icoutils_0.29.1-2_i386.deb
imagemagick_8%3a6.6.9.7-5ubuntu3.2_i386.deb
imagemagick-common_8%3a6.6.9.7-5ubuntu3.2_all.deb
libcapi20-3_1%3a3.12.20071127-0ubuntu11_i386.deb
libcdt4_2.26.3-10ubuntu1_i386.deb
libencode-locale-perl_1.02-2_all.deb
libfile-listing-perl_6.03-1_all.deb
libfont-afm-perl_1.20-1_all.deb
libgettextpo0_0.18.1.1-5ubuntu3_i386.deb
libgif4_4.1.6-9ubuntu1_i386.deb
libgraph4_2.26.3-10ubuntu1_i386.deb
libgvc5_2.26.3-10ubuntu1_i386.deb
libhtml-format-perl_2.10-1_all.deb
libhtml-form-perl_6.00-1_all.deb
libhtml-parser-perl_3.69-1build1_i386.deb
libhtml-tagset-perl_3.20-2_all.deb
libhtml-tree-perl_4.2-1_all.deb
libhttp-cookies-perl_6.00-2_all.deb
libhttp-daemon-perl_6.00-1_all.deb
libhttp-date-perl_6.00-1_all.deb
libhttp-message-perl_6.01-1_all.deb
libhttp-negotiate-perl_6.00-2_all.deb
libilmbase6_1.0.1-3build2_i386.deb
libio-socket-inet6-perl_2.69-2_all.deb
libio-socket-ssl-perl_1.53-1_all.deb
liblqr-1-0_0.4.1-1.1_i386.deb
liblwp-mediatypes-perl_6.01-1_all.deb
liblwp-protocol-https-perl_6.02-1_all.deb
libmagickcore4_8%3a6.6.9.7-5ubuntu3.2_i386.deb
libmagickcore4-extra_8%3a6.6.9.7-5ubuntu3.2_i386.deb
libmagickwand4_8%3a6.6.9.7-5ubuntu3.2_i386.deb
libmailtools-perl_2.08-1_all.deb
libmpg123-0_1.12.1-3.2ubuntu1_i386.deb
libnet-http-perl_6.02-1_all.deb
libnetpbm10_2%3a10.0-15_i386.deb
libnet-ssleay-perl_1.42-1build1_i386.deb
libodbc1_2.2.14p2-5ubuntu3_i386.deb
libopenal1_1%3a1.13-4ubuntu3_i386.deb
libopenal-data_1%3a1.13-4ubuntu3_all.deb
libopenexr6_1.6.1-4.1_i386.deb
libpam-winbind_2%3a3.6.3-2ubuntu2.3_i386.deb
libpathplan4_2.26.3-10ubuntu1_i386.deb
libsocket6-perl_0.23-1build2_i386.deb
libunistring0_0.9.3-5_i386.deb
liburi-perl_1.59-1_all.deb
libwww-perl_6.03-1_all.deb
libwww-robotrules-perl_6.01-1_all.deb
netpbm_2%3a10.0-15_i386.deb
odbcinst1debian2_2.2.14p2-5ubuntu3_i386.deb
odbcinst_2.2.14p2-5ubuntu3_i386.deb
ttf-droid_20101110+git-2_all.deb
ttf-mscorefonts-installer_3.4ubuntu3_all.deb
ttf-umefont_434-1_all.deb
ttf-unfonts-core_1.0.3.is.1.0.2-080608-5ubuntu1_all.deb
unixodbc_2.2.14p2-5ubuntu3_i386.deb
unrar_1%3a4.0.3-1_i386.deb
winbind_2%3a3.6.3-2ubuntu2.3_i386.deb
wine_1.4-0ubuntu4.1_i386.deb
wine1.4_1.4-0ubuntu4.1_i386.deb
wine1.4-common_1.4-0ubuntu4.1_all.deb
wine1.4-i386_1.4-0ubuntu4.1_i386.deb
wine-gecko1.4_1.4.0-0ubuntu2_i386.deb
winetricks_0.0+20120308_i386.deb

```

---

### Post by Lars Noodén on 2012-09-13
That was for i386.  If you are using 64-bit Linux then you need to download the corresponding amd64 packages instead.

---

### Post by aligator12 on 2012-09-14
> **Lars Noodén said:**
> That was for i386.  If you are using 64-bit Linux then you need to download the corresponding amd64 packages instead.
Thanks for the post. :) Where can I download those?

---

### Post by GeForce 9500GT on 2012-09-14
> **aligator12 said:**
> Thanks for the post. :) Where can I download those?
 
Some people are just soooooo unbelievable........
 
[Go here]("http://archive.ubuntu.com/ubuntu/pool/universe/w/wine1.4/") and there you see the files you need.
 
[wine_1.4.1-0ubuntu1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/w/wine1.4/wine_1.4.1-0ubuntu1_i386.deb") for 32-bit
[wine_1.4.1-0ubuntu1_amd64.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/w/wine1.4/wine_1.4.1-0ubuntu1_amd64.deb") for 64-bit

---

### Post by Stosswalkinator on 2012-09-22
> **GeForce 9500GT said:**
> [This is the link to the pool]("http://archive.ubuntu.com/ubuntu/pool/universe/w/"). Scroll down to Wine and there's everything. But what was wrong with the link i provided you in [post #2]("http://ubuntuforums.org/showpost.php?p=12235644&postcount=2")??
Which file do I download? I too want to install Wine offline. I clicked on the folder that just said "wine" and there are lots of files there. What should I download?

---

### Post by Lars Noodén on 2012-09-22
> **Stosswalkinator said:**
> Which file do I download? I too want to install Wine offline. I clicked on the folder that just said "wine" and there are lots of files there. What should I download?

See post #13 above.  Those are the files that Ubuntu installed to provide WINE.

---

