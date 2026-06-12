---
title: "How to run 32-bit Firefox without entering chroot"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by ngolian on 2005-10-14
I finally managed it! Here's how. I'm still using the 32-bit chroot to get it and all the bits that go with it installed, because that seems to be the easiest way. My 32-bit chroot is at /chroot32, so change it if yours lives somewhere else.

All this is done after getting Firefox and its plugins up and running in the chroot, but without entering the chroot

You need the ia32-libs-gtk package. 
ia32-libs-openoffice.org may also come in handy, but probably isn't necessary.

Breezy's ia32-libs currently doesn't include the version of libstdc++ that Firefox needs, so link it from the chroot:

ln -s /chroot32/usr/lib/libstdc++.so.6.0.5 /usr/lib32
ldconfig

The exact version number may vary; use whichever libstdc++.so.6 is linked to.

Create some links:

ln -nsf /chroot32/usr/lib/mozilla-* /usr/lib32

Create a new version of the wrapper script:

cp /usr/lib32/mozilla-firefox/firefox /usr/lib32/mozilla-firefox/firefox32
ln -nsf /usr/lib32/mozilla-firefox/firefox32 /usr/local/bin/

Apply this patch to the new file: <http://www.realh.co.uk/unix/firefox32.patch>.

The Flash plugin's links are absolute instead of relative paths, which stops them working from /usr/lib32. You'd better fix this, because Flash is the whole reason for using 32-bit Firefox:

ln -nsf ../../flashplugin-nonfree/flashplayer.xpt \
/usr/lib32/mozilla-firefox/plugins/
ln -nsf ../../flashplugin-nonfree/libflashplayer.so \
/usr/lib32/mozilla-firefox/plugins/

If the package gets upgraded you'll probably need to do that again. Alternatively you could do this:

ln -ns /chroot32/usr/lib/flashplugin-nonfree /usr/lib

If there ever is a /usr/lib/flashplugin-nonfree which that would interfere with, then there shouldn't be any need for this malarkey anyway. 

I think that's it. Sorry if I've missed something important, but I wasn't really expecting this to work and didn't make notes or anything.

It appears to run OK, but there are some problems caused by some of the libraries still looking in /usr/lib for their plugins instead of /usr/lib32. We really need custom-compiled ia32-libs*, not just copies of the 32-bit packages.

---

