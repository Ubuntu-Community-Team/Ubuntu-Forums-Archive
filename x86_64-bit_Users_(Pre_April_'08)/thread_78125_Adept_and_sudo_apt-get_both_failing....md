---
title: "Adept and sudo apt-get both failing..."
date: 2005-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by malacoda on 2005-10-17
Can't seem to install anything via Adept or in terminal w/ sudo apt-get.  I've tried to get several different items all end up failing.  As an example to show the 'errors' I'm getting when I try I've attempted to get VLC through termimal using sudo apt-get install vlc.  Results are:

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liba52-0.7.4 libaa1 libdvbpsi3 libglib1.2 libgtk1.2 libgtk1.2-common
  libid3tag0 liblircclient0 libmad0 libmpeg2-4 libtar libwxgtk2.4-1 wxvlc
Suggested packages:
  lirc vlc-plugin-alsa mozilla-plugin-vlc
Recommended packages:
  ttf-thryomanes videolan-doc
The following NEW packages will be installed:
  liba52-0.7.4 libaa1 libdvbpsi3 libglib1.2 libgtk1.2 libgtk1.2-common
  libid3tag0 liblircclient0 libmad0 libmpeg2-4 libtar libwxgtk2.4-1 vlc wxvlc
0 upgraded, 14 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 9385kB of archives.
After unpacking 25.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libgtk1.2-common libglib1.2 libgtk1.2 liba52-0.7.4 libaa1 libdvbpsi3
  libid3tag0 libmad0 libmpeg2-4 libtar libwxgtk2.4-1 liblircclient0 wxvlc vlc
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libgtk1.2-common 1.2.10-17build1
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libglib1.2 1.2.10-10ubuntu1
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libgtk1.2 1.2.10-17build1
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main liba52-0.7.4 0.7.4-1
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libaa1 1.4p5-28ubuntu3
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe libdvbpsi3 0.1.4-2
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libid3tag0 0.15.1b-7
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libmad0 0.15.1b-2.1
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libmpeg2-4 0.4.0b-2ubuntu4
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe libtar 1.2.11-3
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe libwxgtk2.4-1 2.4.4.1ubuntu1
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main liblircclient0 0.7.0.1-1ubuntu3
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe wxvlc 0.8.4-svn20050920-3+hal0ubuntu3
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe vlc 0.8.4-svn20050920-3+hal0ubuntu3
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2-common_1.2.10-17build1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2-common_1.2.10-17build1_all.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-10ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-10ubuntu1_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2_1.2.10-17build1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2_1.2.10-17build1_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/a52dec/liba52-0.7.4_0.7.4-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/a52dec/liba52-0.7.4_0.7.4-1_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/aalib/libaa1_1.4p5-28ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/aalib/libaa1_1.4p5-28ubuntu3_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvbpsi3/libdvbpsi3_0.1.4-2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvbpsi3/libdvbpsi3_0.1.4-2_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-7_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-7_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/mpeg2dec/libmpeg2-4_0.4.0b-2ubuntu4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/mpeg2dec/libmpeg2-4_0.4.0b-2ubuntu4_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/libt/libtar/libtar_1.2.11-3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libt/libtar/libtar_1.2.11-3_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wxwindows2.4/libwxgtk2.4-1_2.4.4.1ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wxwindows2.4/libwxgtk2.4-1_2.4.4.1ubuntu1_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.7.0.1-1ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.7.0.1-1ubuntu3_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/wxvlc_0.8.4-svn20050920-3+hal0ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/wxvlc_0.8.4-svn20050920-3+hal0ubuntu3_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.4-svn20050920-3+hal0ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.4-svn20050920-3+hal0ubuntu3_amd64.deb)  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
john@john-kubuntu:~$

Seems I can't connect to the repositories... but if that's the case how can it build a dependency tree? (Note: I'm still a noob so this is just a guess).

I've tried VLC, Xine, Mplayer, and other items with no luck.  Any ideas as to what the cause and fix for this may be would be VERY much appreicated.

---

### Post by bluck on 2005-10-17
[QUOTE=malacoda]

Seems I can't connect to the repositories... but if that's the case how can it build a dependency tree? (Note: I'm still a noob so this is just a guess).

I've tried VLC, Xine, Mplayer, and other items with no luck.  Any ideas as to what the cause and fix for this may be would be VERY much appreicated.[/QUOTE]

seems theres been quite a few people with problems with some repositories.
I've had no issues with the canadian repositories (ca prefix instead of us).

try editing your /etc/apt/sources.list to point there instead..

---

### Post by malacoda on 2005-10-17
Thanks but no luck...  after replacing us with ca to point to canadian repositories and fetching updates to update the headers I've gone from ~17,000 available packages down to ~1500 and if I select something to install it it's designated as a 'BREAK'...:(

---

### Post by gomadtroll on 2005-10-18
[QUOTE=malacoda]Thanks but no luck...  after replacing us with ca to point to canadian repositories and fetching updates to update the headers I've gone from ~17,000 available packages down to ~1500 and if I select something to install it it's designated as a 'BREAK'...:([/QUOTE]

Not sure where the problem is but Ubuntu servers are having problems. Try sources from the following list until one works.
 [https://wiki.ubuntu.com//Archive](https://wiki.ubuntu.com//Archive)

---

### Post by ah_mad on 2006-02-05
I had the same problem, when I was disabling lo by

sudo ifconfig lo down 

and apt-get stop working just when it is looking to localhost. So, as the result of my search in a debian forum, the same guy had the problem and he could solve it by uninstalling the anon-proxy as I had installed this program a week before, I uninstalled it as well and it solves my problem.

---

