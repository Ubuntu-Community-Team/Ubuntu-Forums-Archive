---
title: "Compiling Iceweasel as amd64"
date: 2006-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Joe_CoT on 2006-10-17
Hi, I've been trying to compile iceweasel for a significant portion of the night. I've finally got it compiled, but i'm getting errors on run. Here is my .mozconfig:

```

export MOZ_PHOENIX=1
ac_add_options --disable-official-branding
mk_add_options MOZ_PHOENIX=1
ac_cv_visibility_pragma=no
ac_add_options --disable-ldap
ac_add_options --disable-calendar
ac_add_options --disable-mailnews
ac_add_options --disable-chatzilla
ac_add_options --enable-extensions="cookie,xml-rpc,xmlextras,pref,transformiix,universalchardet,webservices,inspector,gnomevfs,spellcheck"
ac_add_options --enable-crypto
ac_add_options --disable-composer
ac_add_options --enable-single-profile
ac_add_options --disable-profilesharing
ac_add_options --enable-static
ac_add_options --disable-shared
ac_add_options --disable-debug
#ac_add_options --disable-toolkit-gtk
ac_add_options --enable-toolkit-gtk2
ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-xft
ac_add_options --disable-freetype2
ac_add_options --disable-tests
ac_add_options --disable-accessibility
ac_add_options --disable-installer
ac_add_options --enable-strip
ac_add_options --disable-toolkit-qt
ac_add_options --prefix=/usr/local
ac_add_options --disable-pango
#ac_add_options --with-default-mozilla-five-home=/usr/local/lib
#ac_add_options --enable-postscript
ac_add_options --disable-xprint
ac_add_options --with-user-appdir=.gnuzilla
ac_add_options --disable-xinerama
ac_add_options --with-system-zlib
ac_add_options --with-system-jpeg
ac_add_options --with-system-png
ac_add_options --with-pthreads
ac_add_options --disable-svg-renderer-cairo
ac_add_options -enable-application=browser
ac_add_options --disable-negotiateauth

```

I also edited the autoconf.mk to add -lXfl

this is the debug output upon trying to run:

```

joe@necromancer:/usr/local/lib/firefox-1.5.0.7-g1$ sh --debug iceweasel
Type Manifest File: /home/joe/.gnuzilla/iceweasel/nndpmoo9.default/xpti.dat
*** Registering xpcomObsoleteModule components (all right -- a generic module!)
*** Registering xpconnect components (all right -- a generic module!)
*** Registering nsUConvModule components (all right -- a generic module!)
*** Registering nsUCvMathModule components (all right -- a generic module!)
*** Registering nsI18nModule components (all right -- a generic module!)
*** Registering necko_core_and_primary_protocols components (all right -- a generic module!)
*** Registering necko_secondary_protocols components (all right -- a generic module!)
*** Registering nsJarModule components (all right -- a generic module!)
*** Registering nsPrefModule components (all right -- a generic module!)
*** Registering nsSecurityManagerModule components (all right -- a generic module!)
*** Registering nsRDFModule components (all right -- a generic module!)
*** Registering nsParserModule components (all right -- a generic module!)
*** Registering nsGfxPSModule components (all right -- a generic module!)
*** Registering nsGfxGTKModule components (all right -- a generic module!)
*** Registering nsImageLib2Module components (all right -- a generic module!)
*** Registering nsPluginModule components (all right -- a generic module!)
*** Registering nsWidgetGtk2Module components (all right -- a generic module!)
*** Registering nsLayoutModule components (all right -- a generic module!)
*** Registering docshell_provider components (all right -- a generic module!)
*** Registering embedcomponents components (all right -- a generic module!)
*** Registering Browser_Embedding_Module components (all right -- a generic module!)
*** Registering nsEditorModule components (all right -- a generic module!)
*** Registering nsTransactionManagerModule components (all right -- a generic module!)
*** Registering nsComposerModule components (all right -- a generic module!)
*** Registering appshell components (all right -- a generic module!)
*** Registering nsCJVMManagerModule components (all right -- a generic module!)
*** Registering nsChromeModule components (all right -- a generic module!)
*** Registering nsMorkModule components (all right -- a generic module!)
*** Registering nsFindComponent components (all right -- a generic module!)
*** Registering application components (all right -- a generic module!)
*** Registering nsFileViewModule components (all right -- a generic module!)
*** Registering RemoteServiceModule components (all right -- a generic module!)
*** Registering CommandLineModule components (all right -- a generic module!)
*** Registering nsToolkitCompsModule components (all right -- a generic module!)
*** Registering Apprunner components (all right -- a generic module!)
*** Registering BOOT components (all right -- a generic module!)
*** Registering NSS components (all right -- a generic module!)
*** Registering PKI components (all right -- a generic module!)
*** Registering nsCookieModule components (all right -- a generic module!)
*** Registering nsXMLExtrasModule components (all right -- a generic module!)
*** Registering nsAutoConfigModule components (all right -- a generic module!)
*** Registering nsSystemPrefModule components (all right -- a generic module!)
*** Registering TransformiixModule components (all right -- a generic module!)
*** Registering nsUniversalCharDetModule components (all right -- a generic module!)
*** Registering nsWebServicesModule components (all right -- a generic module!)
*** Registering SearchServiceModule components (all right -- a generic module!)
*** Registering BrowserDirProvider components (all right -- a generic module!)
*** Registering nsBrowserCompsModule components (all right -- a generic module!)
nsNativeComponentLoader: autoregistering begins.
nsNativeComponentLoader: autoregistering succeeded
nsNativeComponentLoader: registering deferred (0)
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 377
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 534
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 534
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 534
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 377
WARNING: malformed pref file, file prefread.cpp, line 534
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 534
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 534
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: NS_ENSURE_TRUE(NS_SUCCEEDED(rv)) failed, file nsChromeRegistry.cpp, line 1252
GFX: dpi=96 t2p=0.0666667 p2t=15 depth=24
WARNING: default.xpm not found, file nsWindow.cpp, line 3094
++WEBSHELL == 1
++DOMWINDOW == 1
WARNING: nsExceptionService ignoring thread destruction after shutdown, file nsExceptionService.cpp, line 191
--WEBSHELL == 0
###!!! ASSERTION: Main thread being held past XPCOM shutdown.: 'cnt == 0', file nsThread.cpp, line 478
Break: at file nsThread.cpp, line 478
No Persistent Registry Found.
Type Manifest File: /home/joe/.gnuzilla/iceweasel/nndpmoo9.default/xpti.dat
*** Registering xpcomObsoleteModule components (all right -- a generic module!)
*** Registering xpconnect components (all right -- a generic module!)
*** Registering nsUConvModule components (all right -- a generic module!)
*** Registering nsUCvMathModule components (all right -- a generic module!)
*** Registering nsI18nModule components (all right -- a generic module!)
*** Registering necko_core_and_primary_protocols components (all right -- a generic module!)
*** Registering necko_secondary_protocols components (all right -- a generic module!)
*** Registering nsJarModule components (all right -- a generic module!)
*** Registering nsPrefModule components (all right -- a generic module!)
*** Registering nsSecurityManagerModule components (all right -- a generic module!)
*** Registering nsRDFModule components (all right -- a generic module!)
*** Registering nsParserModule components (all right -- a generic module!)
*** Registering nsGfxPSModule components (all right -- a generic module!)
*** Registering nsGfxGTKModule components (all right -- a generic module!)
*** Registering nsImageLib2Module components (all right -- a generic module!)
*** Registering nsPluginModule components (all right -- a generic module!)
*** Registering nsWidgetGtk2Module components (all right -- a generic module!)
*** Registering nsLayoutModule components (all right -- a generic module!)
*** Registering docshell_provider components (all right -- a generic module!)
*** Registering embedcomponents components (all right -- a generic module!)
*** Registering Browser_Embedding_Module components (all right -- a generic module!)
*** Registering nsEditorModule components (all right -- a generic module!)
*** Registering nsTransactionManagerModule components (all right -- a generic module!)
*** Registering nsComposerModule components (all right -- a generic module!)
*** Registering appshell components (all right -- a generic module!)
*** Registering nsCJVMManagerModule components (all right -- a generic module!)
*** Registering nsChromeModule components (all right -- a generic module!)
*** Registering nsMorkModule components (all right -- a generic module!)
*** Registering nsFindComponent components (all right -- a generic module!)
*** Registering application components (all right -- a generic module!)
*** Registering nsFileViewModule components (all right -- a generic module!)
*** Registering RemoteServiceModule components (all right -- a generic module!)
*** Registering CommandLineModule components (all right -- a generic module!)
*** Registering nsToolkitCompsModule components (all right -- a generic module!)
*** Registering Apprunner components (all right -- a generic module!)
*** Registering BOOT components (all right -- a generic module!)
*** Registering NSS components (all right -- a generic module!)
*** Registering PKI components (all right -- a generic module!)
*** Registering nsCookieModule components (all right -- a generic module!)
*** Registering nsXMLExtrasModule components (all right -- a generic module!)
*** Registering nsAutoConfigModule components (all right -- a generic module!)
*** Registering nsSystemPrefModule components (all right -- a generic module!)
*** Registering TransformiixModule components (all right -- a generic module!)
*** Registering nsUniversalCharDetModule components (all right -- a generic module!)
*** Registering nsWebServicesModule components (all right -- a generic module!)
*** Registering SearchServiceModule components (all right -- a generic module!)
*** Registering BrowserDirProvider components (all right -- a generic module!)
*** Registering nsBrowserCompsModule components (all right -- a generic module!)
nsNativeComponentLoader: autoregistering begins.
*** Registering nsInspectorModule components (all right -- a generic module!)
*** Registering JavaScript_Debugger components (all right -- a generic module!)
*** Registering mozgnome components (all right -- a generic module!)
*** Registering mozMySpellModule components (all right -- a generic module!)
*** Registering nsGnomeVFSModule components (all right -- a generic module!)
*** Registering mozSpellCheckerModule components (all right -- a generic module!)
*** Registering nsSoftwareUpdate components (all right -- a generic module!)
*** Registering BrowserDirProvider components (all right -- a generic module!)
nsNativeComponentLoader: autoregistering succeeded
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 377
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 534
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 534
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 534
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 377
WARNING: malformed pref file, file prefread.cpp, line 534
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 534
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 534
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
WARNING: malformed pref file, file prefread.cpp, line 253
nsNativeComponentLoader: registering deferred (0)
nsNativeComponentLoader: registering deferred (0)
nsNativeComponentLoader: registering deferred (0)
nsNativeComponentLoader: autoregistering begins.
*** Registering nsInspectorModule components (all right -- a generic module!)
nsNativeComponentLoader: autoregistering succeeded
nsNativeComponentLoader: registering deferred (0)
nsNativeComponentLoader: autoregistering begins.
nsNativeComponentLoader: autoregistering succeeded
nsNativeComponentLoader: registering deferred (0)
WARNING: NS_ENSURE_TRUE(NS_SUCCEEDED(rv)) failed, file nsChromeRegistry.cpp, line 1252
GFX: dpi=96 t2p=0.0666667 p2t=15 depth=24
WARNING: default.xpm not found, file nsWindow.cpp, line 3094
++WEBSHELL == 1
++DOMWINDOW == 1
************************************************************
* Call to xpconnect wrapped JSObject produced this error:  *
[Exception... "Component returned failure code: 0x8000ffff (NS_ERROR_UNEXPECTED) [nsIPrefBranch.getBoolPref]"  nsresult: "0x8000ffff (NS_ERROR_UNEXPECTED)" location: "JS frame :: chrome://browser/content/sanitize.js :: anonymous :: line 297"  data: no]
************************************************************
************************************************************
* Call to xpconnect wrapped JSObject produced this error:  *
[Exception... "Component returned failure code: 0x8000ffff (NS_ERROR_UNEXPECTED) [nsIPrefBranch.getCharPref]"  nsresult: "0x8000ffff (NS_ERROR_UNEXPECTED)" location: "JS frame :: file:///usr/local/lib/firefox-1.5.0.7-g1/components/nsBrowserContentHandler.js :: anonymous :: line 197"  data: no]
************************************************************
WARNING: nsExceptionService ignoring thread destruction after shutdown, file nsExceptionService.cpp, line 191
--WEBSHELL == 0
###!!! ASSERTION: Main thread being held past XPCOM shutdown.: 'cnt == 0', file nsThread.cpp, line 478
Break: at file nsThread.cpp, line 478
nsStringStats
 => mAllocCount:           5054
 => mReallocCount:         1330
 => mFreeCount:            5053  --  LEAKED 1 !!!
 => mShareCount:           4465
 => mAdoptCount:            701
 => mAdoptFreeCount:        700  --  LEAKED 1 !!!
joe@necromancer:/usr/local/lib/firefox-1.5.0.7-g1$

```

Any ideas? I'm not finding anything which remotely looks like a solution on  the web or in usenet. Has anyone been able to successfully compile iceweasel in 64 bit? Any help would be appreciated.

---

### Post by kopilo on 2006-10-17
I don't know... If you manage to do it, could you make the compiled deb file avaliable for public download?

Yes I'd like to leech it. :P

---

### Post by Joe_CoT on 2006-10-17
yeah, i thought this might be beyond the scope of the forums :shock: I'll post it to their dev mailing list and see what they say

---

### Post by s_spiff on 2006-10-17
hey, kliz has already made a deb and put it up as a part of his 'how to' install 32bit firefox on 64 bit en.
[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)

---

### Post by Joe_CoT on 2006-10-17
> hey, kliz has already made a deb and put it up as a part of his 'how to' install 32bit firefox on 64 bit en.

I saw that, but that's a 32 bit binary using the 32 bit linux libraries. Isn't there a way to compile it 64 bit?

---

