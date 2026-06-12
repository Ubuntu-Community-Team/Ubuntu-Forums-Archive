---
title: "How do I install Galaxium?"
date: 2005-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by negatory on 2005-06-19
Hi!
I've installed mono from [http://www.mono-project.com/Downloads](http://www.mono-project.com/Downloads) and downloaded the Galaxium binary [here](http://galaxium.sourceforge.net/download.html) and when I try to run galaxium it gives me:
```
negatory@matrix:~/programs/Galaxium-0.1.112-Binary$ mono Galaxium.exe
[2:10 PM] > Galaxium Messenger v0.1.111
[2:10 PM] > Application Started.

(<unknown>:16046): Gdk-WARNING **: locale not supported by Xlib

(<unknown>:16046): Gdk-WARNING **: can not set locale modifiers

(<unknown>:16046): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(<unknown>:16046): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

Unhandled Exception: System.DllNotFoundException: libglade-2.0.so.0
in (wrapper managed-to-native) Glade.XML:glade_xml_new_from_buffer (byte[],int,string,string)
in <0x000a6> Glade.XML:.ctor (System.Reflection.Assembly assembly, System.String resource_name, System.String root, System.String domain)
in <0x000bc> Galaxium.GalaxiumApp:.ctor (System.String[] args)
in <0x00019> Galaxium.MainClass:Main (System.String[] args)
negatory@matrix:~/programs/Galaxium-0.1.112-Binary$
```
What am I doing wrong?

Thanks 
Pedro Carrico

---

### Post by Draek on 2006-09-19
I'm sure that you wrote this AGES ago. But I am the developer of Galaxium Messenger, and I didn't use Ubuntu at the time, so was never on the forums.

You had some requirements missing. There is a very much newer version of galaxium available now! Please visit:

[http://galaxium.bountysource.com/](http://galaxium.bountysource.com/)

You can find all the details there!

---

### Post by ounn on 2006-11-23
Hi

Can you help-me compile Galaxium from command line? I cant open monodevelop because its always craxing.

Thanks

ounn

---

