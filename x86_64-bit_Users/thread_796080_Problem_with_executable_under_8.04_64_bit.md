---
title: "Problem with executable under 8.04 64 bit"
date: 2008-05-16
forum: x86 64-bit Users
---

### Post by aussiedaddy on 2008-05-16
I recently installed 8.04 64 bit Workstation.  Previously I ran 7.10 32 bit.

My executables (compiled xHarbour to gcc to executable) wont run.  What's more I get a crazy result when I try to run them - I get the following message: "No such file or directory" even though the file can be displayed with ls and I am the owner and I have rwx rights as the owner.

Is this because of:

trying to run a 32 bit app on 64 bit OS

need to recompile with later gcc (some libraries are linked in for which I don't have the source)

Or some weird 8.04 issue?

Can anyone out there help please.

---

### Post by hermes0710 on 2008-05-16
Can you post the exact output of the terminal when you try to run it (with the command you use attached)?

---

### Post by aussiedaddy on 2008-05-16
I just installed a 32 bit 8.04 on another box and executables run fine.  So its some sort of 64 bit issue.

---

### Post by aussiedaddy on 2008-05-16
The command I am using is 

./mSYS

mSYS is the name of my executable

The response I get is:

bash: ./mSYS: No such file or directory

but if I type ls -l I get a listing which includes mSYS with rights set to

-rwx------

with me as owner and the group as my group

Which seems a strange response if it is a 64 bit issue (which it appears to be)

Thanks for your help

---

### Post by Cappy on 2008-05-16
You need to install ia32-libs

Any additional 32-bit libraries can be installed with getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by hermes0710 on 2008-05-16
Yeap it's strange. Any case you need the "sh"? ```
sh ./mSYS
```

---

### Post by aussiedaddy on 2008-05-16
Cappy

Will experiment - sounds promising except some of my libraries I don't have source for and will need to get the vendor to upgrade.  But is the error message I am getting the one you would expect?  

Thanks

---

### Post by aussiedaddy on 2008-05-16
Hermes0710

Will try - although I never needed it in 32bit.  Can't try at the moment because I've come home and 64 bit machine is at my workplace.

Thanks

---

### Post by jim_24601 on 2008-05-16
What is the output of 'ldd ./mSYS' ?

---

### Post by aussiedaddy on 2008-05-16
Jim_24601

I am at home so can't run on 64bit box at present.  On my home box (Ubuntu 7.10 32 bit) I get:

	linux-gate.so.1 =>  (0xffffe000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb7bca000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7b43000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb7b27000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb7b0f000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7aea000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb7ae1000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb7ab6000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7aa8000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7a9f000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb7a9c000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb7a94000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb7a8e000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb7a85000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb7a82000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb7a7e000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb7a41000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb79ca000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb78d9000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb78d4000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb7899000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7894000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7890000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb77d3000)
	libglade-2.0.so.0 => /usr/lib/libglade-2.0.so.0 (0xb77bb000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb769d000)
	libgnomeprintui-2-2.so.0 => /usr/lib/libgnomeprintui-2-2.so.0 (0xb765d000)
	libgnomeprint-2-2.so.0 => /usr/lib/libgnomeprint-2-2.so.0 (0xb75f5000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb75e0000)
	libgnomecanvas-2.so.0 => /usr/lib/libgnomecanvas-2.so.0 (0xb75b0000)
	libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb759a000)
	libgpm.so.1 => /usr/lib/libgpm.so.1 (0xb7594000)
	libncurses.so.5 => /lib/libncurses.so.5 (0xb7550000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7405000)
	/lib/ld-linux.so.2 (0xb7f5f000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb73d7000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7367000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb7347000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb7344000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb7320000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb731b000)
	libgailutil.so.18 => /usr/lib/libgailutil.so.18 (0xb7313000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb72fa000)

Thanks for your help

Must get a bit of sleep now!

---

### Post by jim_24601 on 2008-05-16
That's quite a list of dependencies. I expect the 64-bit machine is missing the 32-bit version of one or more (probably more) of those. (Which you can take to be the case if you get "no such file or directory" when the file is staring you in the face. It seems that it's impractical for the dynamic linker to distinguish missing executable from missing library--at any rate, Windows has the same problem, although it at least admits that it might be missing "one of its components".) Anyway, getlibs may help you, as Cappy said. Looks as if the getlibs script does pretty much the same thing--scans the output of 'ldd' to find missing libraries, then installs them.

---

### Post by aussiedaddy on 2008-05-17
Thanks everyone for your help.  I will try to get all the required 32 bit libraries installed and / or recompile 64 bit and get 64 bit libraries.

---

