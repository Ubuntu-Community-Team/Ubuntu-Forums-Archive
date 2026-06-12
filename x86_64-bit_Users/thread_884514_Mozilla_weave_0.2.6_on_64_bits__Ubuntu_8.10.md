---
title: "Mozilla weave 0.2.6 on 64 bits / Ubuntu 8.10"
date: 2008-08-09
forum: x86 64-bit Users
---

### Post by Typhoe on 2008-08-09
Hi,

did someone manage to compile the new weave 0.2.6 version on intrepid ?

I tried the usual commands, but only get error:

# Needed packages
sudo apt-get install xulrunner-1.9-dev mercurial build-essential
# Get sources
hg clone [http://hg.mozilla.org/labs/weave](http://hg.mozilla.org/labs/weave)
cd weave
# version ( [http://hg.mozilla.org/labs/weave/](http://hg.mozilla.org/labs/weave/) )
#hg up -r c8bce0724360 # the 0.2.5 release build
hg up -r 29093153230e # the 0.2.6 release build
# build
make sdkdir=/usr/lib/xulrunner-devel-1.9.0.1 xpi

```

./build/subst.pl src/WeaveCrypto.rc 'buildid=1073' 'unpacked=# ' 'jar='
./build/subst.pl chrome.manifest 'buildid=1073' 'unpacked=# ' 'jar='
make -C src install
make[1]: entrant dans le répertoire « /home/typhoe/weave/src »
c++ -shared -pipe -Os -fPIC -fno-rtti -fno-exceptions -fno-strict-aliasing -fno-common -fshort-wchar -pthread -Wall -Wconversion -Wpointer-arith -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wcast-align -Wno-long-long -include xpcom-config.h -I/usr/lib/xulrunner-devel-1.9.0.1/include -I/usr/lib/xulrunner-devel-1.9.0.1/include/system_wrappers -I/usr/lib/xulrunner-devel-1.9.0.1/include/nss -I/usr/lib/xulrunner-devel-1.9.0.1/include/xpcom -I/usr/lib/xulrunner-devel-1.9.0.1/include/string -I/usr/lib/xulrunner-devel-1.9.0.1/include/pipnss -I/usr/lib/xulrunner-devel-1.9.0.1/include/nspr -I/usr/lib/xulrunner-devel-1.9.0.1/sdk/include -o WeaveCrypto.so WeaveCrypto.cpp WeaveCryptoModule.cpp -pthread -pipe -DMOZILLA_STRICT_API -Wl,-dead_strip -Wl,-exported_symbol -Wl,-z,defs -Wl,-h,WeaveCrypto.so -Wl,-rpath-link,/usr/lib/xulrunner-devel-1.9.0.1/bin /usr/lib/xulrunner-devel-1.9.0.1/lib/libxpcomglue_s.a -L/usr/lib/xulrunner-devel-1.9.0.1/lib -L/usr/lib/xulrunner-devel-1.9.0.1/bin -lxpcomglue_s -lxpcom -lnspr4 -lcrmf -lsmime3 -lssl3 -lnss3 -lnssutil3 -lplds4 -lplc4
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:51:21: error: prtypes.h: Aucun fichier ou dossier de ce type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:12:20: error: prtime.h: Aucun fichier ou dossier de ce type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:61,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsImpl.h:55:60: error: prthread.h: Aucun fichier ou dossier de ce type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsImpl.h:56:81: error: pratom.h: Aucun fichier ou dossier de ce type
In file included from WeaveCrypto.cpp:41:
WeaveCrypto.h:44:21: error: pk11pub.h: Aucun fichier ou dossier de ce type
In file included from WeaveCrypto.cpp:43:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsStringAPI.h:55:19: error: prlog.h: Aucun fichier ou dossier de ce type
WeaveCrypto.cpp:45:22: error: plbase64.h: Aucun fichier ou dossier de ce type
WeaveCrypto.cpp:46:19: error: prmem.h: Aucun fichier ou dossier de ce type
WeaveCrypto.cpp:47:20: error: secerr.h: Aucun fichier ou dossier de ce type
WeaveCrypto.cpp:49:22: error: pk11func.h: Aucun fichier ou dossier de ce type
WeaveCrypto.cpp:50:19: error: keyhi.h: Aucun fichier ou dossier de ce type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:347: error: ‘PRUint32’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:360: error: ‘PRUint32’ does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:368,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsError.h:314: error: ‘nsresult’ does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:424: error: ‘PRUint16’ does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:44,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:122,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:60: error: ‘PRUint32’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:61: error: ‘PRUint16’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:62: error: ‘PRUint16’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:63: error: ‘PRUint8’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:76: error: ‘PRBool’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:95: error: ‘PRBool’ does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:122,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:86: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:94: error: ‘nsrefcnt’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:103: error: ‘nsrefcnt’ does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsDebug.h:49,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:57,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: ISO C++ forbids declaration of ‘nsresult’ with no type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: typedef ‘nsresult’ is initialized (use __typeof__ instead)
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: ‘PR_CALLBACK’ was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: ‘nsGetModuleProc’ was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:139: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:153: error: ‘nsGetModuleProc’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:196: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:216: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:230: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:243: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:256: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:269: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:297: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:302: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:320: warning: ‘NS_Alloc’ initialized and declared ‘extern’
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:320: error: ‘PRSize’ was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:341: error: ‘PRSize’ has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:383: warning: ‘NS_DebugBreak’ initialized and declared ‘extern’
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:383: error: variable or field ‘NS_DebugBreak’ declared void
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:383: error: ‘PRUint32’ was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:384: error: expected primary-expression before ‘const’
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:384: error: expected primary-expression before ‘const’
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:385: error: expected primary-expression before ‘const’
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:385: error: ‘PRInt32’ was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:420: error: ‘PRUint32’ has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:423: error: ‘PRUint32’ has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:436: error: ‘nsrefcnt’ has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:437: error: ‘PRUint32’ has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:440: error: ‘nsrefcnt’ has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:463: error: ‘PRBool’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:466: error: ‘PRBool’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:550: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:553: error: ‘nsresult’ does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:57,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsDebug.h:275: error: expected constructor, destructor, or type conversion before ‘void’
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsImpl.h:60,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:61,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsTraceRefcnt.h:102: error: expected constructor, destructor, or type conversion before ‘class’
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h: In instantiation of ‘const nsIID nsISupports::COMTypeInfo<int>::kIID’:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:69:   instantiated from here
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:69: error: too many initializers for ‘const nsIID’
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:51:21: error: prtypes.h: Aucun fichier ou dossier de ce type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:12:20: error: prtime.h: Aucun fichier ou dossier de ce type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:61,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsImpl.h:55:60: error: prthread.h: Aucun fichier ou dossier de ce type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsImpl.h:56:81: error: pratom.h: Aucun fichier ou dossier de ce type
In file included from WeaveCryptoModule.cpp:40:
WeaveCrypto.h:44:21: error: pk11pub.h: Aucun fichier ou dossier de ce type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:347: error: ‘PRUint32’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:360: error: ‘PRUint32’ does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:368,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsError.h:314: error: ‘nsresult’ does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:424: error: ‘PRUint16’ does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:44,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:122,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:60: error: ‘PRUint32’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:61: error: ‘PRUint16’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:62: error: ‘PRUint16’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:63: error: ‘PRUint8’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:76: error: ‘PRBool’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:95: error: ‘PRBool’ does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:122,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:86: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:94: error: ‘nsrefcnt’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:103: error: ‘nsrefcnt’ does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsDebug.h:49,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:57,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: ISO C++ forbids declaration of ‘nsresult’ with no type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: typedef ‘nsresult’ is initialized (use __typeof__ instead)
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: ‘PR_CALLBACK’ was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: ‘nsGetModuleProc’ was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:139: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:153: error: ‘nsGetModuleProc’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:196: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:216: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:230: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:243: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:256: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:269: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:297: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:302: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:320: warning: ‘NS_Alloc’ initialized and declared ‘extern’
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:320: error: ‘PRSize’ was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:341: error: ‘PRSize’ has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:383: warning: ‘NS_DebugBreak’ initialized and declared ‘extern’
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:383: error: variable or field ‘NS_DebugBreak’ declared void
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:383: error: ‘PRUint32’ was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:384: error: expected primary-expression before ‘const’
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:384: error: expected primary-expression before ‘const’
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:385: error: expected primary-expression before ‘const’
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:385: error: ‘PRInt32’ was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:420: error: ‘PRUint32’ has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:423: error: ‘PRUint32’ has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:436: error: ‘nsrefcnt’ has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:437: error: ‘PRUint32’ has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:440: error: ‘nsrefcnt’ has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:463: error: ‘PRBool’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:466: error: ‘PRBool’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:550: error: ‘nsresult’ does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:553: error: ‘nsresult’ does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:57,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsDebug.h:275: error: expected constructor, destructor, or type conversion before ‘void’
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsImpl.h:60,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:61,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsTraceRefcnt.h:102: error: expected constructor, destructor, or type conversion before ‘class’
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h: In instantiation of ‘const nsIID nsISupports::COMTypeInfo<int>::kIID’:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:69:   instantiated from here
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:69: error: too many initializers for ‘const nsIID’
make[1]: *** [WeaveCrypto.so] Erreur 1
make[1]: quittant le répertoire « /home/typhoe/weave/src »
make: *** [platform] Erreur 2

```

regards,
Typhoe

---

### Post by Yellow Pasque on 2008-08-09
Make sure you have the libgcrypt11-dev package:
```
sudo apt-get install libgcrypt11-dev
```
If it still doesn't work, I've attached the one I built.

---

### Post by Typhoe on 2008-08-09
> **Temüjin said:**
> Make sure you have the libgcrypt11-dev package:
```
sudo apt-get install libgcrypt11-dev
```
If it still doesn't work, I've attached the one I built.

Thank you for the answer.

I tried again after installing libgcrypt11-dev.... but not more success.

However, your version seems to work fine, so thank you !!!

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
xulrunner-1.9-dev is already the newest version.
mercurial is already the newest version.
build-essential is already the newest version.
libgcrypt11-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
destination directory: weave
real URL is http://hg.mozilla.org/labs/weave/
requesting all changes
adding changesets
adding manifests
adding file changes
added 1074 changesets with 2080 changes to 209 files
updating working directory
163 files updated, 0 files merged, 0 files removed, 0 files unresolved
0 files updated, 0 files merged, 0 files removed, 0 files unresolved
./build/subst.pl src/WeaveCrypto.rc 'buildid=1073' 'unpacked=# ' 'jar='
./build/subst.pl chrome.manifest 'buildid=1073' 'unpacked=# ' 'jar='
make -C src install
make[1]: Entering directory `/home/typhoe/weave/src'
/usr/lib/xulrunner-devel-1.9.0.1/bin/xpidl -m header -I/usr/lib/xulrunner-devel-1.9.0.1/idl IWeaveCrypto.idl
c++ -shared -pipe -Os -fPIC -fno-rtti -fno-exceptions -fno-strict-aliasing -fno-common -fshort-wchar -pthread -Wall -Wconversion -Wpointer-arith -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wcast-align -Wno-long-long -include xpcom-config.h -I/usr/lib/xulrunner-devel-1.9.0.1/include -I/usr/lib/xulrunner-devel-1.9.0.1/include/system_wrappers -I/usr/lib/xulrunner-devel-1.9.0.1/include/nss -I/usr/lib/xulrunner-devel-1.9.0.1/include/xpcom -I/usr/lib/xulrunner-devel-1.9.0.1/include/string -I/usr/lib/xulrunner-devel-1.9.0.1/include/pipnss -I/usr/lib/xulrunner-devel-1.9.0.1/include/nspr -I/usr/lib/xulrunner-devel-1.9.0.1/sdk/include -o WeaveCrypto.so WeaveCrypto.cpp WeaveCryptoModule.cpp -pthread -pipe -DMOZILLA_STRICT_API -Wl,-dead_strip -Wl,-exported_symbol -Wl,-z,defs -Wl,-h,WeaveCrypto.so -Wl,-rpath-link,/usr/lib/xulrunner-devel-1.9.0.1/bin /usr/lib/xulrunner-devel-1.9.0.1/lib/libxpcomglue_s.a -L/usr/lib/xulrunner-devel-1.9.0.1/lib -L/usr/lib/xulrunner-devel-1.9.0.1/bin -lxpcomglue_s -lxpcom -lnspr4 -lcrmf -lsmime3 -lssl3 -lnss3 -lnssutil3 -lplds4 -lplc4
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:51:21: error: prtypes.h: No such file or directory
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:12:20: error: prtime.h: No such file or directory
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:61,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsImpl.h:55:60: error: prthread.h: No such file or directory
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsImpl.h:56:81: error: pratom.h: No such file or directory
In file included from WeaveCrypto.cpp:41:
WeaveCrypto.h:44:21: error: pk11pub.h: No such file or directory
In file included from WeaveCrypto.cpp:43:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsStringAPI.h:55:19: error: prlog.h: No such file or directory
WeaveCrypto.cpp:45:22: error: plbase64.h: No such file or directory
WeaveCrypto.cpp:46:19: error: prmem.h: No such file or directory
WeaveCrypto.cpp:47:20: error: secerr.h: No such file or directory
WeaveCrypto.cpp:49:22: error: pk11func.h: No such file or directory
WeaveCrypto.cpp:50:19: error: keyhi.h: No such file or directory
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:347: error: 'PRUint32' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:360: error: 'PRUint32' does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:368,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsError.h:314: error: 'nsresult' does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:424: error: 'PRUint16' does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:44,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:122,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:60: error: 'PRUint32' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:61: error: 'PRUint16' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:62: error: 'PRUint16' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:63: error: 'PRUint8' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:76: error: 'PRBool' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:95: error: 'PRBool' does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:122,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:86: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:94: error: 'nsrefcnt' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:103: error: 'nsrefcnt' does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsDebug.h:49,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:57,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: ISO C++ forbids declaration of 'nsresult' with no type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: typedef 'nsresult' is initialized (use __typeof__ instead)
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: 'PR_CALLBACK' was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: 'nsGetModuleProc' was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:139: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:153: error: 'nsGetModuleProc' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:196: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:216: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:230: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:243: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:256: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:269: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:297: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:302: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:320: warning: 'NS_Alloc' initialized and declared 'extern'
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:320: error: 'PRSize' was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:341: error: 'PRSize' has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:383: warning: 'NS_DebugBreak' initialized and declared 'extern'
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:383: error: variable or field 'NS_DebugBreak' declared void
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:383: error: 'PRUint32' was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:384: error: expected primary-expression before 'const'
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:384: error: expected primary-expression before 'const'
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:385: error: expected primary-expression before 'const'
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:385: error: 'PRInt32' was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:420: error: 'PRUint32' has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:423: error: 'PRUint32' has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:436: error: 'nsrefcnt' has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:437: error: 'PRUint32' has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:440: error: 'nsrefcnt' has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:463: error: 'PRBool' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:466: error: 'PRBool' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:550: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:553: error: 'nsresult' does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:57,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsDebug.h:275: error: expected constructor, destructor, or type conversion before 'void'
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsImpl.h:60,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:61,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from IWeaveCrypto.h:10,
                 from WeaveCrypto.h:43,
                 from WeaveCrypto.cpp:41:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsTraceRefcnt.h:102: error: expected constructor, destructor, or type conversion before 'class'
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h: In instantiation of 'const nsIID nsISupports::COMTypeInfo<int>::kIID':
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:69:   instantiated from here
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:69: error: too many initializers for 'const nsIID'
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:51:21: error: prtypes.h: No such file or directory
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:12:20: error: prtime.h: No such file or directory
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:61,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsImpl.h:55:60: error: prthread.h: No such file or directory
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsImpl.h:56:81: error: pratom.h: No such file or directory
In file included from WeaveCryptoModule.cpp:40:
WeaveCrypto.h:44:21: error: pk11pub.h: No such file or directory
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:347: error: 'PRUint32' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:360: error: 'PRUint32' does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:368,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsError.h:314: error: 'nsresult' does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsrootidl.h:11,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nscore.h:424: error: 'PRUint16' does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:44,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:122,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:60: error: 'PRUint32' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:61: error: 'PRUint16' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:62: error: 'PRUint16' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:63: error: 'PRUint8' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:76: error: 'PRBool' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsID.h:95: error: 'PRBool' does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:122,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:86: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:94: error: 'nsrefcnt' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:103: error: 'nsrefcnt' does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsDebug.h:49,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:57,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: ISO C++ forbids declaration of 'nsresult' with no type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: typedef 'nsresult' is initialized (use __typeof__ instead)
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: 'PR_CALLBACK' was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:101: error: 'nsGetModuleProc' was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:139: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:153: error: 'nsGetModuleProc' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:196: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:216: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:230: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:243: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:256: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:269: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:297: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:302: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:320: warning: 'NS_Alloc' initialized and declared 'extern'
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:320: error: 'PRSize' was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:341: error: 'PRSize' has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:383: warning: 'NS_DebugBreak' initialized and declared 'extern'
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:383: error: variable or field 'NS_DebugBreak' declared void
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:383: error: 'PRUint32' was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:384: error: expected primary-expression before 'const'
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:384: error: expected primary-expression before 'const'
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:385: error: expected primary-expression before 'const'
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:385: error: 'PRInt32' was not declared in this scope
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:420: error: 'PRUint32' has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:423: error: 'PRUint32' has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:436: error: 'nsrefcnt' has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:437: error: 'PRUint32' has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:440: error: 'nsrefcnt' has not been declared
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:463: error: 'PRBool' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:466: error: 'PRBool' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:550: error: 'nsresult' does not name a type
/usr/lib/xulrunner-devel-1.9.0.1/include/nsXPCOM.h:553: error: 'nsresult' does not name a type
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:57,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsDebug.h:275: error: expected constructor, destructor, or type conversion before 'void'
In file included from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsImpl.h:60,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsUtils.h:61,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsISupports.h:123,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIFactory.h:10,
                 from /usr/lib/xulrunner-devel-1.9.0.1/include/nsIGenericFactory.h:42,
                 from WeaveCryptoModule.cpp:39:
/usr/lib/xulrunner-devel-1.9.0.1/include/nsTraceRefcnt.h:102: error: expected constructor, destructor, or type conversion before 'class'
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h: In instantiation of 'const nsIID nsISupports::COMTypeInfo<int>::kIID':
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:69:   instantiated from here
/usr/lib/xulrunner-devel-1.9.0.1/include/nsISupportsBase.h:69: error: too many initializers for 'const nsIID'
make[1]: *** [WeaveCrypto.so] Error 1
make[1]: Leaving directory `/home/typhoe/weave/src'
make: *** [platform] Error 2

```

---

### Post by Yellow Pasque on 2008-08-09
You're welcome. FYI, I had the same issue when I tried to build on intrepid. From what I can tell, the version of xulrunner-1.9.0.1-dev in the intrepid repo is actually older than the one in hardy-proposed.

---

### Post by aurojr on 2008-09-13
It worked for me.
Just installed recommended libgcrypt11-dev and useed provided xpi.
:guitar:

---

