---
title: "Moonlight"
date: 2007-07-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by skabaas on 2007-07-26
Did someone manage to get moonlight up and running on an Ubuntu Feisty AMD64 install?! I tried to and I always get the same error:

```

/usr/bin/ld: /usr/local/lib/libavformat.a(utils.o): relocation R_X86_64_32 against `first_iformat' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavformat.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libmoon.la] Fout 1
make[2]: Map '/home/bart/moon/src' wordt verlaten
make[1]: *** [all-recursive] Fout 1
make[1]: Map '/home/bart/moon' wordt verlaten
make: *** [all] Fout 2

```

What am I doing wrong? I just followed the instructions on [http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight)

---

### Post by skabaas on 2007-10-03
After I installed Moonlight using [this How-To](http://groups.google.com/group/mono-olive/browse_thread/thread/a8a35fa2485e362b/3845d870a888663c#3845d870a888663c) everything works fine, but when I start Swiftfox I get the following errormessage:

```

bart@Bananenboom:/opt/swiftfox$ swiftfox_start 

(swiftfox-bin:8190): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
LoadPlugin: failed to initialize shared library /opt/swiftfox/plugins/libmoonloader.so [/opt/swiftfox/plugins/libmoonloader.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/swiftfox/plugins/libmoonplugin.so [/opt/swiftfox/plugins/libmoonplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/swiftfox/plugins/libmoonloader.so [/opt/swiftfox/plugins/libmoonloader.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/swiftfox/plugins/libmoonplugin.so [/opt/swiftfox/plugins/libmoonplugin.so: wrong ELF class: ELFCLASS64]

```

And the worst off all... Moonlight still doesn't work. Is there anybody who can help me fix this?!

---

### Post by Kilz on 2007-10-04
> **skabaas said:**
> After I installed Moonlight using [this How-To](http://groups.google.com/group/mono-olive/browse_thread/thread/a8a35fa2485e362b/3845d870a888663c#3845d870a888663c) everything works fine, but when I start Swiftfox I get the following errormessage:

```

bart@Bananenboom:/opt/swiftfox$ swiftfox_start 

(swiftfox-bin:8190): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
LoadPlugin: failed to initialize shared library /opt/swiftfox/plugins/libmoonloader.so [/opt/swiftfox/plugins/libmoonloader.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/swiftfox/plugins/libmoonplugin.so [/opt/swiftfox/plugins/libmoonplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/swiftfox/plugins/libmoonloader.so [/opt/swiftfox/plugins/libmoonloader.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/swiftfox/plugins/libmoonplugin.so [/opt/swiftfox/plugins/libmoonplugin.so: wrong ELF class: ELFCLASS64]

```

And the worst off all... Moonlight still doesn't work. Is there anybody who can help me fix this?!

The moonlight plugin you have is 64bit, swiftfox is 32 bit, even the packages for amd64. You might consider using [Swiftweasel.]("http://swiftweasel.sourceforge.net/")

---

### Post by d-harry on 2008-03-19
Hello,

I have tried to install Moonlight using [this Howto]("http://www.deepakg.com/blog/archives/39.htm").

I have now a problem. I cant find any *.so file. Where can I find these files? What did I wrong?

---

### Post by trippinnik on 2008-04-05
i've got hardy and I can't seem to find the mozilla-xpcom package.  Anyone know how I can install it?  I'm up to the last part where I have to compile moon but need the mozilla-xpcom first.

---

### Post by trippinnik on 2008-04-05
found it but now I get this error:
** (/usr/lib/monodoc/monodocer.exe:8287): WARNING **: The following assembly referenced from /tmp/moon/gtk/gtksilver.dll could not be loaded:
     Assembly:   agclr    (assemblyref_index=2)
     Version:    0.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/tmp/moon/gtk/).


** (/usr/lib/monodoc/monodocer.exe:8287): WARNING **: Could not load file or assembly 'agclr, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/monodoc/monodocer.exe:8287): WARNING **: Could not load file or assembly 'agclr, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
monodocer: System.Reflection.ReflectionTypeLoadException: The classes in the module cannot be loaded.
  at (wrapper managed-to-native) System.Reflection.Assembly:GetTypes (bool)
  at System.Reflection.Assembly.GetTypes () [0x00000]
  at Stub+<>c__CompilerGenerated0.MoveNext () [0x00000]
  at Stub.DoUpdateAssembly (System.Reflection.Assembly assembly, System.Xml.XmlElement index_types, System.String source, System.String dest, System.Collections.Hashtable goodfiles) [0x00000]
  at Stub.DoUpdateAssemblies (System.String source, System.String dest) [0x00000]
  at Stub.Main (System.String[] args) [0x00000]
Members Added: 0, Members Deleted: 0
make[2]: *** [gtksilver.zip] Error 1
make[2]: Leaving directory `/tmp/moon/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/moon'
make: *** [all] Error 2

Has anyone been able to get it to work?

---

### Post by bodhi.zazen on 2009-03-12
I know this is an old thread, but it comes up on google searches for 

"Ubuntu moonlight"

At any rate it is now much much easier to install moonlight, in fact it is available as a Firefox extension. Much much much easier then the previous links, works on 64 bit Ubuntu (as well as 32 bit).

See my blog here : [How to Moonlight]("http://blog.bodhizazen.net/linux/how-to-moonlight/")

---

