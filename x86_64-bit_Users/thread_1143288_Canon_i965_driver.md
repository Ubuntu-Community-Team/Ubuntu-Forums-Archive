---
title: "Canon i965 driver?"
date: 2009-04-29
forum: x86 64-bit Users
---

### Post by Stolea on 2009-04-29
I just installed Ubuntu 9.04 64bit. Very pleased with this version.
Has anyone got any idea where i can get a driver for my Canon i965 printer? Do I have to use a specific 64bit driver? I had the printer working with a 32bit driver under 8.10 32bit.

---

### Post by 3Miro on 2009-04-29
Canon Linux support sux. I have IP1800 and I have to use virtual box o get it to work under 64-bit. Basically I set it up using the free version of Virtual Box (not the OSE from the repos) and reading the VB manual, then I share the printer on the network so that both my laptop and the desktop (running the VB host) can print with a click of a button.

I hope you can get a better solution, if not, this one works for me.

---

### Post by Stolea on 2009-04-29
That is a bit like having a dog and doing the barking. I am sure that there isa better way. Do I have to use a 64bit driver, or can I use the driver I used before?

---

### Post by 3Miro on 2009-04-29
> **Stolea said:**
> That is a bit like having a dog and doing the barking. I am sure that there isa better way. Do I have to use a 64bit driver, or can I use the driver I used before?

For couple of days I was trying to get the 32-bit driver work under 64-bit Ubuntu and failed. I have little knowledge of nswrapper and I could not recompile the 32-bit driver (it could not be recompiles since the source rpm contained complied libraries). At the end, I only have 2 extra windows open on one of my 4 desktops and I can print as easy as if I had installed the driver.

I hope you find a better way though, you printer is a different version.

---

### Post by Arup on 2009-04-30
Your only option is to buy Turboprint from [http://www.turboprint.info/](http://www.turboprint.info/) but its costly.

Canon is pathetic to say the least, I have been asking for a driver since 2006 for my IP6210D printer and no go.

---

### Post by Thelasko on 2009-04-30
The [OpenPrinting database]("http://openprinting.org/show_printer.cgi?recnum=Canon-i965") says:

>  Select driver similar to: Canon BCJ-8200 - CUPS+Gutenprint v5.0.1 (en)

[Gutenprint is in the repositories.]("http://packages.ubuntu.com/jaunty/cups-driver-gutenprint")

---

### Post by Stolea on 2009-04-30
The BCJ-8200 sort of worked for the 32bit version, but "sort of" is a bit of a euphamism. It does not work with the 64 bit version :(
With my old 32bit setup I used the Japanese drivers, which did the job very well, but the site seems to have disappeared anyhow.
Any other suggestions?

---

### Post by Stolea on 2009-04-30
I just downloaded and installed Turboprint. It takes the pain out of the printing process and will be well worth the price. :) Got all the features that the free Canon Windoze drivers provide.
Needless to say I will not be recomending Canon printers to anyone. The way I see it, if Canon can't be bothered to support Linux (or for that matter even answering any emails about drivers for Linux) I certainly won't buy their goods in future.

---

### Post by Arup on 2009-04-30
Very true I would now be using either HP or Epson and no Canon.

---

### Post by Thelasko on 2009-05-01
> **Stolea said:**
> With my old 32bit setup I used the Japanese drivers...

I've noticed that Canon likes to scatter their Linux drivers all over the globe.  I've had some luck finding drivers on the Australian website.  Unfortunately, most of the drivers are 32-bit rpm files.  They provide source (src.rpm), but it's very difficult to build.

---

### Post by 3Miro on 2009-05-01
> **Thelasko said:**
> I've noticed that Canon likes to scatter their Linux drivers all over the globe.  I've had some luck finding drivers on the Australian website.  Unfortunately, most of the drivers are 32-bit rpm files.  They provide source (src.rpm), but it's very difficult to build.

In my case the rpm was impossible to build. It turned out that it contained already build libraries (32-bit).

---

### Post by Thelasko on 2009-05-01
> **3Miro said:**
> In my case the rpm was impossible to build. It turned out that it contained already build libraries (32-bit).

What a crock!

---

