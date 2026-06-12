---
title: "Unable to start the program using Wine"
date: 2011-07-25
forum: Wine
---

### Post by claymore.s on 2011-07-25
Hi, I just made a casino based program with C# and would like to import it to Ubuntu but I'm unable to do so. Wine merely shows Opening Casino.exe in the Task Bar and then closes by itself. Can anyone possibly help me out?

Greatly appreciated

---

### Post by ipatfrmww on 2011-07-25
You probably don't have the .NET or C# runtime's installed (they wouldn't be in a fresh wineprefix)
The best way to install them is with winetricks.

---

### Post by claymore.s on 2011-07-25
Hi, I've done as what you've asked me to do and installed the .net stuffs. Upon opening Casino.exe, it told me to download 4.0 but I'm unable to install 4.0.. I'm still trying to look for a solution with google.

Greatly appreciated.

PS: This is the error I've gotten after failing to install .net 4.0
"Error parsing C:\windows\Microsoft.NET\Framework\v4.0.30319\config\machine.config *Parser returned error 0x80004001"*

---

### Post by nerdy_kid on 2011-07-25
I don't exactly know what I am talking about, but if I understand correctly, what you need to do is install mono develop from the software center and recompile your program under that.

---

### Post by claymore.s on 2011-07-26
> **nerdy_kid said:**
> I don't exactly know what I am talking about, but if I understand correctly, what you need to do is install mono develop from the software center and recompile your program under that.

 Hi, I've tried using your method but there's an error message in the compiler stating that Framework Mono/.NET 4.0 is not installed. I'll try a clean re install later on. Can someone really help me here? It's for my final year project.  Greatly appreciated.

---

### Post by ipatfrmww on 2011-07-26
If you still want to run the programs in wine (I suppose you don't now if your using mono), then you could find some other program with an installer that you know uses C#. I would expect them to automatically install the runtime environment for you. 

I'm not sure if .NET and C# runtime's are the same thing which may be the problem. Not sure though. I just went into winetricks and installed everything when I installed wine, so I don't actually know what I did. I just know that stuff works now that didn't before. Perhaps you should try that :).
I think though that it might be vcrun2010 vcrun2008 or something like that (or is visual C++ something different again?)

---

### Post by directhex on 2011-07-26
Only Ubuntu 11.10 and higher support .NET 4.0 apps.

---

### Post by claymore.s on 2011-07-26
Hi, I'm currently on Ubuntu 10.10 and the installation for .NET 4.0 has been failing. Any idea how to fix it?

Greatly appreciated

---

### Post by directhex on 2011-07-27
> **claymore.s said:**
> Hi, I'm currently on Ubuntu 10.10 and the installation for .NET 4.0 has been failing. Any idea how to fix it?

Greatly appreciated

No idea. I'm not interested in Wine or Wine problems - try a Wine support forum, you'll get more dedicated & knowledgeable help there.

Mono can execute .NET apps directly (Tomboy, gbrainy and Banshee are .NET apps, for example), and is preinstalled. But 4.0 support requires Mono 2.8 or higher, which is only in Ubuntu 11.10

Perhaps you could try installing Mono for Windows in Wine, and run your app with Mono for Windows in Wine? Worth a shot

---

### Post by claymore.s on 2011-07-27
> **directhex said:**
> No idea. I'm not interested in Wine or Wine problems - try a Wine support forum, you'll get more dedicated & knowledgeable help there.

Mono can execute .NET apps directly (Tomboy, gbrainy and Banshee are .NET apps, for example), and is preinstalled. But 4.0 support requires Mono 2.8 or higher, which is only in Ubuntu 11.10

Perhaps you could try installing Mono for Windows in Wine, and run your app with Mono for Windows in Wine? Worth a shot

 Hey, is there anyway that i can downgrade my program into 1 which doesn't require net. 4.0?

---

### Post by claymore.s on 2011-07-28
Already found the solution to this by converting the whole program to .NET 2.0. Thanks all!

---

