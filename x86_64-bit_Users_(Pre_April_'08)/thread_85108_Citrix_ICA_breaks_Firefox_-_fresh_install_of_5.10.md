---
title: "Citrix ICA breaks Firefox - fresh install of 5.10"
date: 2005-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by neurator on 2005-11-01
Hello all.  So I've tried installing both V9 and an earlier version of the Citrix ICA client as downloaded from their website.  Every time I install it firefox breaks.  If I uninstall Firefox starts to work fine.  Any thoughts?

---

### Post by neurator on 2005-11-01
ok so I got Citrix to install after some help in a prior post, but I cannot figure out what  application to have my browser run when executing the "launch.asp" script which houses the ISA connection.  It defaults to opening ASP files with Gedit. 

Also, I tried doing

ln -s /usr/lib/ICAClient/npica.so /usr/lib/mozilla-firefox/plugins/npica.so

only to have Firefox fail to load until I rm the npica.so link. 

Thoughts?  
Thanks in advance

---

### Post by neurator on 2005-11-02
Anybody out there to help?  Another thing I tried was converting the Citrix RPM file to .Deb, but alien gives an error:  

root@Satabox:/home/reg/downloads# alien -d ICAClient-9.0-1.i386.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/icaclient
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find path for libXaw.so.7
dpkg-shlibdeps: warning: could not find path for libXaw.so.7
dpkg-shlibdeps: warning: could not find path for libXaw.so.7
dpkg-shlibdeps: warning: could not find path for libldapsdk.so.0
dpkg-shlibdeps: warning: could not find path for libXm.so.3
dpkg-shlibdeps: warning: could not find path for libXp.so.6
dpkg-shlibdeps: warning: could not find any packages for  (libXaw.so.7)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXaw (soname 7, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXt (soname 6, path /usr/lib32/libXt.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libXaw.so.7)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXaw (soname 7, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXt (soname 6, path /usr/lib32/libXt.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXmu (soname 6, path /usr/lib32/libXmu.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libXaw.so.7)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXaw (soname 7, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXt (soname 6, path /usr/lib32/libXt.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/lib32/libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libldapsdk.so.0)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libldapsdk (soname 0, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libXm.so.3)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXm (soname 3, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libXp.so.6)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXp (soname 6, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXpm (soname 4, path /usr/lib32/libXpm.so.4, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libSM (soname 6, path /usr/lib32/libSM.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libICE (soname 6, path /usr/lib32/libICE.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXmu (soname 6, path /usr/lib32/libXmu.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXt (soname 6, path /usr/lib32/libXt.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dh_gencontrol
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: ICAClient-9.0: No such file or directory

---

### Post by dpack on 2005-11-28
Not sure what to tell you about that. It sounds like something is foobar on your system. I am running a clean install of 5.10 and loaded the "MetaFrame Presentation Server Client for Linux x86" to my system last night with no problems. FireFox lists ICA in the plugins and continues to work flawlessly. The Citrix client I am using is for me to log into an NFUSE site and nothing else. I didn't get my install file from Citrix's web site either. I downloaded it directly from my companies NFUSE site. So I can tell you it does work in Breezy, but I'm still too much of a Linux newbie to tell you what's up with your system.

---

