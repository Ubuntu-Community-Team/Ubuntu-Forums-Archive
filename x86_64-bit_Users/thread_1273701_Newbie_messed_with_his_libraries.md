---
title: "Newbie messed with his libraries"
date: 2009-09-23
forum: x86 64-bit Users
---

### Post by syzygies on 2009-09-23
I am a newbie and think I should take it more slowly next time, but I've gotten myself into trouble.  I was trying to get Cisco's VPN software to work on my 64-bit machine.  I followed the directions from Post #34 at [http://ubuntuforums.org/showthread.php?t=855485&page=4](http://ubuntuforums.org/showthread.php?t=855485&page=4) (which I've pasted below) and now things aren't working well.  Here are some of the problems upon logging into my system:

[LIST]
[*]There is no internet connection (not even an icon for the wireless network)
[*]Whenever I try to start firefox, I get the error "load XPCOM"
[*]Whenever I login, I receive the error "The panel encountered an error while loading 'OAFIID:GNOME_ClockApplet'.  Do you want to delete the applet from your configuration"
[/LIST]
 Is it clear to anyone what my next steps should be to fix the problem?

----------------------------------------------------------------------------------------
[INDENT]Tips from this forum helped me: [http://ubuntuforums.org/archive/index.php/t-855485.html](http://ubuntuforums.org/archive/index.php/t-855485.html)

I am running 64-bit Fedora 10.

1) install vpn client software

tar xzf anyconnect-linux-2.3.2016-k9.tar.gz
cd ciscovpn
sudo sh vpn_install.sh

2) I don't know why this wasn't made executable to begin with...

sudo chmod +x /opt/cisco/vpn/bin/vpndownloader.sh

32-bit users you *should* be good to go as long as you have the libraries from step 3 below installed.
64-bit users read on...

3)
Download the following 32-bit libraries from the repositories (all .i386 packages for the libs). As other tips suggest, you can, but don't need to, download firefox 3; it's just that it is packaged with almost all the 32-bit libraries that you need. You can get all the necessary files from the redhat/fedora/ubuntu/debian/etc repositories otherwise.

These are the ones you need:
libnss3.so
libplc4.so
libnspr4.so
libsmime3.so
libsoftokn3.so
libnssdbm3.so
libfreebl3.so
libnssutil3.so
libplds4.so
libsqlite3.so

/lib and /usr/lib contain 32-bit libraries
/lib64 and /usr/lib64 contain 64-bit libraries

3)
Create symlinks to the appropriate libraries.
Here's what /opt/cisco/vpn/lib looks like:
[... lib]$ ls -lAH
-rwxr-xr-x 1 root root 1149892 2009-07-13 08:35 libcrypto.so.0.9.8
lrwxrwxrwx 1 root root      22 2009-07-13 09:00 libfreebl3.so -> /usr/lib/libfreebl3.so
lrwxrwxrwx 1 root root      16 2009-07-13 09:02 libnspr4.so -> /lib/libnspr4.so
lrwxrwxrwx 1 root root      19 2009-07-13 08:56 libnss3.so -> /usr/lib/libnss3.so
lrwxrwxrwx 1 root root      22 2009-07-13 09:02 libnssdbm3.so -> /usr/lib/libnssdbm3.so
lrwxrwxrwx 1 root root      23 2009-07-13 09:02 libnssutil3.so -> /usr/lib/libnssutil3.so
lrwxrwxrwx 1 root root      15 2009-07-13 09:01 libplc4.so -> /lib/libplc4.so
lrwxrwxrwx 1 root root      16 2009-07-13 09:01 libplds4.so -> /lib/libplds4.so
lrwxrwxrwx 1 root root      21 2009-07-13 08:56 libsmime3.so -> /usr/lib/libsmime3.so
lrwxrwxrwx 1 root root      23 2009-07-13 08:56 libsoftokn3.so -> /usr/lib/libsoftokn3.so
lrwxrwxrwx 1 root root      28 2009-07-13 09:03 libsqlite3.so -> /usr/lib/libsqlite3.so.0.8.6
-rwxr-xr-x 1 root root  222300 2009-07-13 08:35 libssl.so.0.9.8

4) Create /usr/local/firefox directory and link (or copy) to there as well.

5)
Linking to the i386 version of zlib (libz.so):

sudo ln -s /lib/libz.so.1 /usr/lib/libz.so
sudo ln -s /lib/libz.so.1 /usr/local/firefox/libz.so

which enabled me to download the certificate from the VPN server.

6) make vpnui available for your user to execute globally. Fedora, Ubuntu, and I think Debian all make the PATH environment variable include ~/bin if it exists for user-local installations.
mkdir ~/bin
cd ~/bin
ln -s /opt/cisco/vpn/bin/vpnui

7) run client
vpnui

Note: you don't need to run vpnui as root, run it as your user because the vpn daemon that was installed with the cisco software is already running with the necessary privilages to modify networking configuration after the install completed.

This is how I got Cisco AnyConnect Client 2.3.2016 working.
[/INDENT]

---

### Post by Yellow Pasque on 2009-09-23
- Ubuntu64 puts 32-bit libraries in /usr/lib32. There should be no 32-bit libraries in /lib or /usr/lib. To reinstall 64-bit versions of those libs you've listed.
```
sudo apt-get install --reinstall libsqlite3-0 libnss3-1d libnspr4-0d
```

- Delete any symbolic links you've created.

- In the future, use getlibs to install 32-bit libraries: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by syzygies on 2009-09-23
Thank you so much, Temüjin!  Now everything is as good as new.

---

