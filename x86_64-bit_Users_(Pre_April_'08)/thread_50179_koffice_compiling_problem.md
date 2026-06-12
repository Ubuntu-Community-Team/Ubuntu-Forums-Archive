---
title: "koffice compiling problem"
date: 2005-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tamir on 2005-07-19
hi, I have this output while compiling koffice:

```
   declared void
/usr/include/kde/arts/startupmanager.h:74: error: parse error before `}' token
In file included from /usr/include/kde/arts/objectmanager.h:27,
                 from /usr/include/kde/arts/common.h:31,
                 from /usr/include/kde/arts/soundserver.h:6,
                 from /usr/include/kde/arts/kplayobjectfactory.h:28,
                 from kpresenter_sound_player.cc:34:
/usr/include/kde/arts/factory.h:45: error: syntax error before `:' token
/usr/include/kde/arts/factory.h:51: error: virtual outside class declaration
/usr/include/kde/arts/factory.h:51: error: function `Arts::Object_skel* 
   Arts::createInstance()' is initialized like a variable
/usr/include/kde/arts/factory.h:52: error: virtual outside class declaration
/usr/include/kde/arts/factory.h:52: error: function `std::string 
   Arts::interfaceName()' is initialized like a variable
/usr/include/kde/arts/factory.h:67: error: parse error before `}' token
In file included from /usr/include/kde/arts/common.h:31,
                 from /usr/include/kde/arts/soundserver.h:6,
                 from /usr/include/kde/arts/kplayobjectfactory.h:28,
                 from kpresenter_sound_player.cc:34:
/usr/include/kde/arts/objectmanager.h:30:25: arts_export.h: No such file or directory
In file included from /usr/include/kde/arts/common.h:31,
                 from /usr/include/kde/arts/soundserver.h:6,
                 from /usr/include/kde/arts/kplayobjectfactory.h:28,
                 from kpresenter_sound_player.cc:34:
/usr/include/kde/arts/objectmanager.h:44: error: syntax error before `{' token
/usr/include/kde/arts/objectmanager.h:50: error: `Factory' was not declared in 
   this scope
/usr/include/kde/arts/objectmanager.h:50: error: parse error before `>' token
/usr/include/kde/arts/objectmanager.h:53: error: parse error before `public'
/usr/include/kde/arts/objectmanager.h:55: error: destructors must be member 
   functions
/usr/include/kde/arts/objectmanager.h:57: error: syntax error before `*' token
/usr/include/kde/arts/objectmanager.h:66: error: `Factory' was not declared in 
   this scope
/usr/include/kde/arts/objectmanager.h:66: error: `factory' was not declared in 
   this scope
/usr/include/kde/arts/objectmanager.h:66: error: variable or field `
   registerFactory' declared void
/usr/include/kde/arts/objectmanager.h:67: error: `Factory' was not declared in 
   this scope
/usr/include/kde/arts/objectmanager.h:67: error: `factory' was not declared in 
   this scope
/usr/include/kde/arts/objectmanager.h:67: error: variable or field `
   removeFactory' declared void
/usr/include/kde/arts/objectmanager.h:73: error: parse error before `}' token
In file included from /usr/include/kde/arts/common.h:32,
                 from /usr/include/kde/arts/soundserver.h:6,
                 from /usr/include/kde/arts/kplayobjectfactory.h:28,
                 from kpresenter_sound_player.cc:34:
/usr/include/kde/arts/idlfilereg.h:29:25: arts_export.h: No such file or directory
In file included from /usr/include/kde/arts/common.h:32,
                 from /usr/include/kde/arts/soundserver.h:6,
                 from /usr/include/kde/arts/kplayobjectfactory.h:28,
                 from kpresenter_sound_player.cc:34:
/usr/include/kde/arts/idlfilereg.h:41: error: syntax error before `:' token
/usr/include/kde/arts/idlfilereg.h:44: error: parse error before `public'
/usr/include/kde/arts/idlfilereg.h:50: error: parse error before `}' token
In file included from /usr/include/kde/arts/common.h:33,
                 from /usr/include/kde/arts/soundserver.h:6,
                 from /usr/include/kde/arts/kplayobjectfactory.h:28,
                 from kpresenter_sound_player.cc:34:
/usr/include/kde/arts/asyncstream.h:26:25: arts_export.h: No such file or directory
In file included from /usr/include/kde/arts/asyncstream.h:28,
                 from /usr/include/kde/arts/common.h:33,
                 from /usr/include/kde/arts/soundserver.h:6,
                 from /usr/include/kde/arts/kplayobjectfactory.h:28,
                 from kpresenter_sound_player.cc:34:
/usr/include/kde/arts/datapacket.h:26:25: arts_export.h: No such file or directory
In file included from /usr/include/kde/arts/asyncstream.h:28,
                 from /usr/include/kde/arts/common.h:33,
                 from /usr/include/kde/arts/soundserver.h:6,
                 from /usr/include/kde/arts/kplayobjectfactory.h:28,
                 from kpresenter_sound_player.cc:34:
/usr/include/kde/arts/datapacket.h:43: error: syntax error before `{' token
/usr/include/kde/arts/datapacket.h:53: error: virtual outside class declaration
/usr/include/kde/arts/datapacket.h:53: error: function `void 
   Arts::processedPacket(Arts::GenericDataPacket*)' is initialized like a 
   variable
/usr/include/kde/arts/datapacket.h:58: error: virtual outside class declaration
/usr/include/kde/arts/datapacket.h:58: error: function `void 
   Arts::sendPacket(Arts::GenericDataPacket*)' is initialized like a variable
/usr/include/kde/arts/datapacket.h:60: error: parse error before `public'
/usr/include/kde/arts/datapacket.h:65: error: virtual outside class declaration
/usr/include/kde/arts/datapacket.h:65: error: function `void Arts::endPull()' 
   is initialized like a variable
/usr/include/kde/arts/datapacket.h:67: error: ISO C++ forbids declaration of `
   GenericDataChannel' with no type
/usr/include/kde/arts/datapacket.h: In function `int Arts::GenericDataChannel()
   ':
/usr/include/kde/arts/datapacket.h:67: error: only constructors take base 
   initializers
/usr/include/kde/arts/datapacket.h:68: confused by earlier errors, bailing out
make[4]: *** [kpresenter_sound_player.lo] Error 1
make[4]: Leaving directory `/home/tamir/koffice/koffice-1.4.0a/kpresenter'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/tamir/koffice/koffice-1.4.0a/kpresenter'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tamir/koffice/koffice-1.4.0a'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/tamir/koffice/koffice-1.4.0a'
make: *** [build-stamp] Error 2
```

I have all the depencies, dont know..

---

### Post by filterban on 2005-07-19
That's ugly.

What compiler are you using?  It may be worth trying a different one (older gcc/g++)?

---

### Post by Tamir on 2005-07-19
[QUOTE=filterban]That's ugly.

What compiler are you using?  It may be worth trying a different one (older gcc/g++)?[/QUOTE]
 gcc 3.4. do you understand what it means?

---

### Post by filterban on 2005-07-19
[QUOTE=Tamir]gcc 3.4. do you understand what it means?[/QUOTE]

Well, the compiler doesn't appear to be working with whatever is installed in KDE.

Does your KDE installation work?

---

### Post by Tamir on 2005-07-20
[QUOTE=filterban]Well, the compiler doesn't appear to be working with whatever is installed in KDE.

Does your KDE installation work?[/QUOTE]
 After reinstallation of Hoary, I have this same problem. What can I do?

---

### Post by medication on 2005-07-20
Tamir are you sure that you posted all of the error message?  It looks to me like you've only got the tail end of the error.  Not sure that I can help, but I'm a software developer by trade and the error message just doesn't feel complete (in the start/beginning).

---

### Post by filterban on 2005-07-20
Yeah, what medication said. 

 I'm also a software developer and the errors seem to be syntax errors, so I'd like to know why the compiler thinks the syntax of the code is incorrect.

Perhaps output from running "./configure" would be useful as well.

---

### Post by Tamir on 2005-07-20
[QUOTE=filterban]Yeah, what medication said. 

 I'm also a software developer and the errors seem to be syntax errors, so I'd like to know why the compiler thinks the syntax of the code is incorrect.

Perhaps output from running "./configure" would be useful as well.[/QUOTE]
 Are you sure? because it is min 40 mins of compiling :/
and how I do that ? by - dpkg-builidpackage > logfile ?

---

### Post by filterban on 2005-07-20
You're building right from dpkg?

Ahhh.

That makes more sense.

I was thinking you would just be doing a straight download of the source code and would not be using dpkg to make the installation.

In either case, I have no idea what's going on with your setup right now as is.

---

### Post by Tamir on 2005-07-21
[QUOTE=filterban]You're building right from dpkg?

Ahhh.

That makes more sense.

I was thinking you would just be doing a straight download of the source code and would not be using dpkg to make the installation.

In either case, I have no idea what's going on with your setup right now as is.[/QUOTE]
 I will try to compile with the default way (./configure, make, make install)

---

