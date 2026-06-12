---
title: "How to: Compile Thunderbird 1.5 on 64 bit"
date: 2006-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by art on 2006-04-14
Hi forum.
 I have been looking for a way to compile thunderbird 1.5 on 64 bit, and I want to share how I got it working. Some of this come from a blog I found on Net, but now I don't remember where that was, so kudos to that guy. I am now not sure which dependencies I needed, but hopefully the error message will tell you. So here is what I did:
1) Download Thunderbird source from [http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/1.5/source/thunderbird-1.5-source.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/1.5/source/thunderbird-1.5-source.tar.bz2)
2)  sudo -s
3) mkdir /opt/thunderbird_build
4) Move source to the /opt/thunderbird_build
5) cd /opt/thunderbird_build, then 
tar jxf thunderbird-1.5-source.tar.bz2
6) From synaptic install build-essential, libgtk2-dev, libfontconfig1-dev, freetype, pkgconfig, libidl-dev, libglib2.0-dev, libxranrd2, libxranrd-dev, libxrender-dev, gtk-imlib1, libpango1.0-dev, libgnomeui-common maybe more 
7) gedit ~/.mozconfig and paste this into it 
```
export BUILD_OFFICIAL=1
export MOZILLA_OFFICIAL=1
mk_add_options MOZ_THUNDERBIRD=1
mk_add_options MOZ_OBJDIR=/opt/thunderbird/
mk_add_options BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
ac_add_options --enable-application=mail
ac_add_options --enable-optimize=-O3
ac_add_options --disable-debug
ac_add_options --enable-xft
ac_add_options --enable-default-toolkit=gtk2
ac_cv_visibility_pragma=no

```8.) If you have a dual CPU processor add 
```
mk_add_options MOZ_MAKE_FLAGS=-j2
```
to your .mozconfig
```
mkdir /opt/thunderbird #this is where thunderbird will be built
cd  /opt/thunderbird_build/mozilla
make -f client.mk build_all
```
12) While compiling 
```
gedit /opt/thunderbird/config/autoconf.mk
```
and change the line 
```
XLIBS		= -lX11 to
XLIBS		= -lX11 -lXft
```
13) When finished compiling 
```
ln -s /opt/thunderbird/dist/bin/thunderbird /usr/bin/thunderbird
```
14) Launch thunderbird running 
thunderbird 
You can also make a launcher in panel for it. I hope someone will like it

---

### Post by beefsprocket on 2006-04-14
That looks pretty good. One question, how fast is it in comparison to running the 1.5 i386 that you can dl and run directly? Perhaps running it with time would be a sort of useful comparison?

---

### Post by mschievano on 2006-04-14
why you compile the version for the 64 bit if this is included in the apt sources?

---

### Post by art on 2006-04-14
Thunderbird 1.5 is not available in repos, at least for breezy.   
    As for the 686 version running on 64 bit, I think there is a little difference in speed, although this is a mail app, not much to speak about in the sense of speed. I followed the guide on how to install Firefox with java and flash, making it always thunderbird instead of firefox, and this is running much smoother, I also compiled FF this way, with a different .mozconfig, and that is running waaay faster then 686. Ofcourse without the plugins, but I don't care about the flash and java anyway.

---

### Post by saratchandra on 2006-04-27
It worked for me. Can you please post the mozconfig for building firefox?

---

### Post by art on 2006-04-27
Sure, this is what I used:
```
# options to build Firefox
ac_add_options --enable-application=browser

# Options for 'configure' (same as command-line options).
ac_add_options --disable-accessibility
ac_add_options --disable-debug
ac_add_options --disable-freetype2
ac_add_options --disable-installer
ac_add_options --disable-jsd
ac_add_options --disable-pedantic
ac_add_options --disable-shared
ac_add_options --disable-tests

ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-plaintext-editor-only
ac_add_options --enable-static
ac_add_options --enable-xft

## processor optimization options
ac_add_options --enable-optimize="-O2" 
mk_add_options MOZ_OBJDIR=/opt/firefox

ac_cv_visibility_pragma=no
ac_add_options --enable-official-branding
```
 if you have dual cpu, again put this line as well::
```
mk_add_options MOZ_MAKE_FLAGS=-j2
```

On the line "ac_add_options --enable-optimize="-O2" " you can put O3 to have even better optimization, put the package built will not be as portable, i.e. you cannot run it on another computer. But as long as you are using it on a computer you compiled it on, it is the best you'll get...
I built it in /opt/firefox as you can see from MOZ_OBJDIR, so you need to mkdir /opt/firefox.

---

### Post by saratchandra on 2006-04-28
It worked like magic. Now, firefox is faster than ever. It is faster than the debian package that I downloaded and even faster than firefox in windows. I installed firefox 1.5.0.2. But the titlebar shows deerpark instead of firefox. I've been thinking that deerpark is the alpha release of firefox 1.5. How can I fix this? Also, how can I make synaptic identify this firefox? I uninstalled firefox provided with breezy and it removed yelp and some other packages.

---

### Post by art on 2006-04-29
I will try to compile with some different options when I get back to office on Monday, to see how to change the DeerPark, I never tried to change it. As for building a debian package(for synaptic to recognize), I wouldn't do that, I am not sure how it will work out, it might break something else... You should install firefox provided with breezy, it won't damage anything.

---

### Post by art on 2006-05-01
So, in order to have the name displayed as Firefox put this in your .mozconfig
ac_add_options --enable-official-branding

---

### Post by WhiteHorse on 2006-05-04
This method breaks the enigmail installation. I had to remove the the line:
mk_add_options MOZ_OBJDIR=/opt/thunderbird/

and then change the link to
ln -s /opt/thunderbird/mozilla/dist/bin/thunderbird /usr/bin/thunderbird

---

### Post by art on 2006-05-06
I didn't know about this, but apparently it is a known feature. Enigmail up to v0.93.2 and IPC up to v1.1.3 cannot handle MOZ_OBJDIR, check this out:
[http://enigmail.mozdev.org/source.html#enigmail](http://enigmail.mozdev.org/source.html#enigmail)
Never used enigmail...

---

### Post by radinator on 2006-05-22
I got the firefox one working, but after the build for thunderbird, I get nothing.  By this I mean that I try to start it, and after less than a second the command-line prompt returns.  No window attempted to open, no error message, nothing.  AND64 X2 here, running Breezy.  At this point I'm at a loss.

---

### Post by art on 2006-05-22
You got firefox working following my directions? TBird should have worked if that is the case. Did you create a new MOZ_OBJDIR for the thunderbird? Did it compile without any errors? Can you paste the output of 
```
ls /opt/thunderbird/dist/bin
```
or instead of /opt/thunderbird put wherever you built your thunderbird.

---

### Post by radinator on 2006-05-22
No errors at all during the build.

I have both /opt/thunderbird_build and /opt/thunderbird as per the directions.

Here's the output:

```
rswartz@hellmouth:/opt/thunderbird_build/mozilla$ ls -l /opt/thunderbird/dist/bin
total 191
lrwxrwxrwx  1 root root     50 2006-05-22 01:18 bloaturls.txt -> /opt/thunderbird_build/mozilla/build/bloaturls.txt
drwxr-xr-x  3 root root   1024 2006-05-22 09:05 chrome
drwxr-xr-x  3 root root   5120 2006-05-22 09:05 components
drwxr-xr-x  8 root root   1024 2006-05-22 01:38 defaults
-rw-r--r--  1 root root     52 2006-05-22 01:19 dependentlibs.list
lrwxrwxrwx  1 root root     39 2006-05-22 01:17 dirver -> ../../directory/c-sdk/ldap/build/dirver
drwxr-xr-x  3 root root   1024 2006-05-22 01:38 extensions
drwxr-xr-x  2 root root   1024 2006-05-22 01:31 greprefs
drwxr-xr-x  2 root root   1024 2006-05-22 01:38 icons
drwxr-xr-x  2 root root   1024 2006-05-22 01:38 init.d
lrwxrwxrwx  1 root root     38 2006-05-22 01:22 libgfxpsshar.so -> ../../gfx/src/psshared/libgfxpsshar.so
lrwxrwxrwx  1 root root     25 2006-05-22 01:22 libgkgfx.so -> ../../gfx/src/libgkgfx.so
lrwxrwxrwx  1 root root     49 2006-05-22 01:38 libgtkembedmoz.so -> ../../embedding/browser/gtk/src/libgtkembedmoz.so
lrwxrwxrwx  1 root root     40 2006-05-22 01:20 libgtkxtbin.so -> ../../widget/src/gtkxtbin/libgtkxtbin.so
lrwxrwxrwx  1 root root     59 2006-05-22 01:18 libldap50.so -> ../../directory/c-sdk/ldap/libraries/libldap/./libldap50.so
lrwxrwxrwx  1 root root     24 2006-05-22 01:18 libmozjs.so -> ../../js/src/libmozjs.so
lrwxrwxrwx  1 root root     33 2006-05-22 01:18 libmozz.so -> ../../modules/zlib/src/libmozz.so
lrwxrwxrwx  1 root root     34 2006-05-22 01:17 libnspr4.so -> ../../nsprpub/pr/src/./libnspr4.so
lrwxrwxrwx  1 root root     48 2006-05-22 01:33 libnss3.so -> ../../security/manager/../../dist/lib/libnss3.so
lrwxrwxrwx  1 root root     51 2006-05-22 01:33 libnssckbi.so -> ../../security/manager/../../dist/lib/libnssckbi.so
lrwxrwxrwx  1 root root     39 2006-05-22 01:17 libplc4.so -> ../../nsprpub/lib/libc/src/./libplc4.so
lrwxrwxrwx  1 root root     34 2006-05-22 01:17 libplds4.so -> ../../nsprpub/lib/ds/./libplds4.so
lrwxrwxrwx  1 root root     63 2006-05-22 01:18 libprldap50.so -> ../../directory/c-sdk/ldap/libraries/libprldap/./libprldap50.so
lrwxrwxrwx  1 root root     50 2006-05-22 01:33 libsmime3.so -> ../../security/manager/../../dist/lib/libsmime3.so
lrwxrwxrwx  1 root root     53 2006-05-22 01:33 libsoftokn3.chk -> ../../security/manager/../../dist/lib/libsoftokn3.chk
lrwxrwxrwx  1 root root     52 2006-05-22 01:33 libsoftokn3.so -> ../../security/manager/../../dist/lib/libsoftokn3.so
lrwxrwxrwx  1 root root     48 2006-05-22 01:33 libssl3.so -> ../../security/manager/../../dist/lib/libssl3.so
lrwxrwxrwx  1 root root     39 2006-05-22 01:19 libxpcom_compat.so -> ../../xpcom/obsolete/libxpcom_compat.so
lrwxrwxrwx  1 root root     34 2006-05-22 01:19 libxpcom_core.so -> ../../xpcom/build/libxpcom_core.so
-rwxr-xr-x  1 root root  19832 2006-05-22 01:19 libxpcom.so
lrwxrwxrwx  1 root root     34 2006-05-22 01:32 libxpistub.so -> ../../xpinstall/stub/libxpistub.so
-rwxr-xr-x  1 root root   6426 2005-09-28 15:08 LICENSE.txt
lrwxrwxrwx  1 root root     27 2006-05-22 01:33 mangle -> /opt/thunderbird/nss/mangle
lrwxrwxrwx  1 root root     54 2006-05-22 01:32 mozilla-installer-bin -> ../../xpinstall/wizard/unix/src2/mozilla-installer-bin
lrwxrwxrwx  1 root root     53 2006-05-22 01:31 mozilla-xremote-client -> ../../widget/src/xremoteclient/mozilla-xremote-client
lrwxrwxrwx  1 root root     22 2006-05-22 01:17 nsinstall -> ../../config/nsinstall
lrwxrwxrwx  1 root root     60 2006-05-22 01:38 README.txt -> /opt/thunderbird_build/mozilla/mail/locales/en-US/README.txt
lrwxrwxrwx  1 root root     35 2006-05-22 01:19 regxpcom -> ../../xpcom/tools/registry/regxpcom
drwxr-xr-x  8 root root   2048 2006-05-22 01:32 res
lrwxrwxrwx  1 root root     56 2006-05-22 01:18 run-mozilla.sh -> /opt/thunderbird_build/mozilla/build/unix/run-mozilla.sh
lrwxrwxrwx  1 root root     30 2006-05-22 01:33 shlibsign -> /opt/thunderbird/nss/shlibsign
lrwxrwxrwx  1 root root     46 2006-05-22 01:38 TestGtkEmbed -> ../../embedding/browser/gtk/tests/TestGtkEmbed
-rwxr-xr-x  1 root root   5205 2006-05-22 01:38 thunderbird
-rwxr-xr-x  1 root root 142116 2006-05-22 01:38 thunderbird-bin
lrwxrwxrwx  1 root root     35 2006-05-22 09:04 thunderbird-config -> ../../build/unix/thunderbird-config
lrwxrwxrwx  1 root root     48 2006-05-22 01:31 updater -> ../../toolkit/mozapps/update/src/updater/updater
lrwxrwxrwx  1 root root     69 2006-05-22 01:38 updater.ini -> /opt/thunderbird_build/mozilla/mail/locales/en-US/updater/updater.ini
lrwxrwxrwx  1 root root     37 2006-05-22 01:20 xpcshell -> ../../js/src/xpconnect/shell/xpcshell
lrwxrwxrwx  1 root root     34 2006-05-22 01:32 xpicleanup -> ../../xpinstall/cleanup/xpicleanup
lrwxrwxrwx  1 root root     31 2006-05-22 01:18 xpidl -> ../../xpcom/typelib/xpidl/xpidl
lrwxrwxrwx  1 root root     38 2006-05-22 01:18 xpt_dump -> ../../xpcom/typelib/xpt/tools/xpt_dump
lrwxrwxrwx  1 root root     38 2006-05-22 01:18 xpt_link -> ../../xpcom/typelib/xpt/tools/xpt_link
rswartz@hellmouth:/opt/thunderbird_build/mozilla$


```

Edit:  It seems to be a permissions thing.  I can't run it in a user account, and I can't sudo it.  However, if I 'su' to root I can get it running.  I don't want it completely unsecure so I don't want to open it up via chmod 777 /opt/thunderbird, but I do seem to have to open something up.  I'm just not sure what the minimal change is at this point to allow user accounts to run it.

Ray

---

### Post by art on 2006-05-22
what are the permissions on /usr/bin/thunderbird? Mine is 
```
ls -l
lrwxrwxrwx  1 root root 37 2006-04-04 12:21 /usr/bin/thunderbird -> /opt/thunderbird/dist/bin/thunderbird
```

---

### Post by radinator on 2006-05-22
Mine is the same.
```
rswartz@hellmouth:~$ ls -l /usr/bin/thunderbird
lrwxrwxrwx  1 root root 37 2006-05-22 01:47 /usr/bin/thunderbird -> /opt/thunderbird/dist/bin/thunderbird

```

---

### Post by art on 2006-05-22
That's really bizarre. Are you sure you don't have any thunderbird process running. Maybe logout->log back in. If no try compiling in your home directory(change /opt to your $HOME), and see how that goes.

---

### Post by radinator on 2006-05-22
Nope.  The only difference is that it will run as root, it will not run as user.  I suppose I could build a copy for each individual user to sit in their home directory, but that is very unsatisfying.

The machine has been restarted several times in the past day (it's a dual-boot machine, and I have to switch it to XP sometimes) so there are no 'old' processes running.

There has to be some simple reason, but I haven't found it yet.

---

### Post by art on 2006-05-22
Oh yeah, that is not the right way to go... I was suggesting it just to see if that is definetely a permissions problem or no. Can you run the debugger
```
gdb /opt/thunderbird/dist/bin/thunderbird-bin
then at the prompt type
run
```
and see what you get. Do this both with you and the root. Post back what you see...

---

### Post by radinator on 2006-05-22
Ok, the first time I tried it I got the following:

```

(gdb) run
Starting program: /opt/thunderbird/dist/bin/thunderbird-bin
/opt/thunderbird/dist/bin/thunderbird-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

```

Note that I do get this error if I run /opt/thunderbird/dist/bin/thunderbird-bin directly (from user or root), but NOT if I run it via the link /usr/bin/thunderbird.  I thought that was interesting.

[Edit:  I see that /usr/bin/thunderbird links to the /opt/thunderbird/dist/bin/thunderbird *script*, not the /opt/thunderbird/dist/bin/thunderbird-bin binary.  That difference makes sense now.]

So anyway, I found the needed library in /opt/thunderbird/dist/lib, and added that to my LD_LIBRARY_PATH environment variable.

Now, when I bring up the debugger and do it I get

```

(gdb) run
Starting program: /opt/thunderbird/dist/bin/thunderbird-bin
[Thread debugging using libthread_db enabled]
[New Thread 46912551764928 (LWP 15875)]
[New Thread 1082132832 (LWP 15878)]
[Thread 1082132832 (LWP 15878) exited]

Program exited with code 01.
(gdb)

```

This is so perplexing.

---

### Post by art on 2006-05-23
OK, at this point I would suggest to start over to be sure what is happening, and compile it with the installer this time (a bit different route but should bring to the same place)
So let's check you have all that is needed to compile again
```
sudo apt-get install build-essential libgtk2.0-dev libidl-dev libxt-dev libgnomevfs2-dev
```
Get the Thunderbird source, and put it in your $HOME, NOT /opt. 
```
tar jxf thunderbird-1.5.0.2-source.tar.bz2
cd mozilla
```
make your mozconfig in the current directory as (taken from ubuntu wiki):
```
. $topsrcdir/mail/config/mozconfig

export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
ac_add_options --enable-official-branding

mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/thunderbird-bin

ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-pango
ac_add_options --with-user-appdir=.mozilla
ac_add_options --with-system-png=/usr
ac_add_options --with-system-jpeg=/usr
ac_add_options --enable-postscript
ac_add_options --disable-installer
ac_add_options --disable-xprint
ac_add_options --enable-crypto
ac_add_options --enable-strip-libs
ac_add_options --enable-canvas
ac_add_options --enable-svg
ac_add_options --enable-svg-renderer=cairo
ac_add_options --enable-system-cairo
ac_add_options --enable-mathml
ac_add_options --disable-tests
ac_add_options --disable-gtktest
ac_add_options --disable-debug
ac_add_options --enable-xft
ac_add_options --enable-optimize=-O3 
ac_add_options --with-system-zlib=/usr
ac_add_options --without-system-nspr
ac_add_options --enable-xinerama
ac_add_options --enable-extensions=default
ac_add_options --disable-pedantic
ac_add_options --disable-long-long-warning
ac_add_options --enable-single-profile
ac_add_options --disable-profilesharing
ac_add_options --enable-gnomevfs
ac_add_options --disable-updater
ac_add_options --enable-application=mail
ac_cv_visibility_pragma=no
mk_add_options MOZ_MAKE_FLAGS=-j2

```
```
make -f client.mk build
make -C thunderbird-bin/mail/installer/
```
a tar.gz file will be created in $HOME/mozilla/thunderbird-bin/dist/, which you'll install in /opt

```
sudo rm -rf /opt/thunderbird
sudo rm -rf /opt/thunderbird_build
```

```
sudo rm /usr/bin/thunderbird
cd /$HOME/mozilla/thunderbird-bin/dist/
sudo tar -C /opt -zxf *.tar.gz
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
```

Has to work...

---

### Post by radinator on 2006-05-23
Thanks for the help.

I had to make a minor addition to get it to build:

```

mk_add_options MOZ_CO_PROJECT=mail

```

I went through the procedure, and when I run it (type 'thunderbird') I get:

```

/opt/thunderbird/thunderbird-bin: symbol lookup error: /opt/thunderbird/components/libgfx_gtk.so: undefined symbol: pango_xft_get_font_map

```

I've checked and the libpango1.0 and libxft stuff is already installed.

Ray

---

### Post by art on 2006-05-23
Well, try compiling with the:
ac_add_options --enable-pango
 removed from .mozconfig. We'll need to go in successive approximations I guess...

---

### Post by radinator on 2006-05-24
Art,

I want to thank you for the help.

Somehow, the problem has been fixed.  In between trying these little experiments I would go back to the original recipie and give it a shot again and again.  I must have compiled the whole thing 10 times or so, trying little variations and looking for what changed.

In one of your latest posts, you mentioned creating .mozconfig in the <build>/mozilla/ directory where in the original recipie you mentioned putting it in the /home directory.  Well, that was the latest change I made.

Somehow in these variations I have a version that works using the original recipie.  I'm not exactly sure what the key was, but it now works.

Thank you for your time.

Ray

---

### Post by art on 2006-05-24
I am glad it worked. Maybe it was not looking at the right mozconfig indeed...

---

