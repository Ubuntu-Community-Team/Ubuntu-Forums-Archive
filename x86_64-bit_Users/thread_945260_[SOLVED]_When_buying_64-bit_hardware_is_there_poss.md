---
title: "[SOLVED] When buying 64-bit hardware is there possiblility to get non amd64 compatibl"
date: 2008-10-12
forum: x86 64-bit Users
---

### Post by abcuser on 2008-10-12
Hi,
I plan to buy a new desktop computer with more then 4 GB of RAM. I would like to install [64-bit PC (amd64) Ubuntu 8.04 Hardy Heron Minimal CD](https://help.ubuntu.com/community/Installation/MinimalCD) and top of it [Virtualbox 2.0.2 AMD64 for Ubuntu 8.04 Hardy Heron](http://virtualbox.org/wiki/Linux_Downloads). Inside VirtualBox I will install guest operating systems which will be 32-bits or 64-bits systems.

What I am wondering before buying a desktop computer is, there are two types of 64-bit computers. As I have read on [Wikipedia](http://en.wikipedia.org/wiki/X86-64) there are (different labels for the same type of hardware) x86-64 = AMD64 = Intel 64 = EM64T = IA-32e and there is also Intel Itanium = IA-64. Both are 64-bit hardware, but x86-64 is 32-bit full compatible and Itanium is not 32-bit compatible.

To run Ubuntu amd64 and Virtualbox amd64 I would just like to make sure to buy suitable hardware. Are Itanium type of processors available on desktops too or are they only available on servers? If so am I worrying to much about this two types of 64-bit hardware systems or not? When buying desktop will it be amd64 compatible? I will buy desktop from official IBM supplier so it will be Lenovo desktop with Intel processor.
Thanks,
Abcuser

---

### Post by Sef on 2008-10-12
Get the AMD64-bit.   The other is also an intel processor, but built mostly by HP.  For more information on it, click [here]("http://en.wikipedia.org/wiki/IA-64").

From [Wikipedia]("http://en.wikipedia.org/wiki/IA-64"):

> **Software support**

 In order to allow more software to run on the Itanium, Intel supported the development of effective compilers for its platform, especially its own suite of compilers.[[35]]("http://en.wikipedia.org/wiki/IA-64#cite_note-34")[[36]]("http://en.wikipedia.org/wiki/IA-64#cite_note-35") [GCC]("http://en.wikipedia.org/wiki/GNU_Compiler_Collection"),[[37]]("http://en.wikipedia.org/wiki/IA-64#cite_note-36")[[38]]("http://en.wikipedia.org/wiki/IA-64#cite_note-37") [Open64]("http://en.wikipedia.org/wiki/Open64") and [MS Visual Studio 2005 (and later)]("http://en.wikipedia.org/wiki/Microsoft_Visual_Studio")[[39]]("http://en.wikipedia.org/wiki/IA-64#cite_note-38") are also able to produce machine code for Itanium. As of 2007, Itanium is supported by [Windows Server 2003]("http://en.wikipedia.org/wiki/Windows_Server_2003"), multiple [Linux distributions]("http://en.wikipedia.org/wiki/Linux_distributions") (including [Debian]("http://en.wikipedia.org/wiki/Debian"), [Red Hat]("http://en.wikipedia.org/wiki/Red_Hat") and Novell [SuSE]("http://en.wikipedia.org/wiki/SuSE")), [FreeBSD]("http://en.wikipedia.org/wiki/FreeBSD"),[[40]]("http://en.wikipedia.org/wiki/IA-64#cite_note-39") and [HP-UX]("http://en.wikipedia.org/wiki/HP-UX"), [OpenVMS]("http://en.wikipedia.org/wiki/OpenVMS"), and [NonStop]("http://en.wikipedia.org/wiki/NonStop") from HP, all natively. HP also sells a [virtualization]("http://en.wikipedia.org/wiki/Virtualization") technology for Itanium called [Integrity Virtual Machines]("http://en.wikipedia.org/wiki/Integrity_Virtual_Machines"). Itanium also supports mainframe environment [GCOS]("http://en.wikipedia.org/wiki/General_Comprehensive_Operating_System") from Groupe Bull and several [IA-32]("http://en.wikipedia.org/wiki/IA-32") operating systems via [Instruction Set Simulators]("http://en.wikipedia.org/wiki/Instruction_Set_Simulator"). Using [QuickTransit]("http://en.wikipedia.org/wiki/QuickTransit"), application binary software for [IRIX]("http://en.wikipedia.org/wiki/IRIX")/[MIPS]("http://en.wikipedia.org/wiki/MIPS_architecture") and [Solaris]("http://en.wikipedia.org/wiki/Solaris_Operating_System")/[SPARC]("http://en.wikipedia.org/wiki/SPARC") can run via "dynamic binary translation" on Linux/Itanium. According to the Itanium Solutions Alliance, as of early 2007 over 10,000 applications are available for Itanium based systems,[[41]]("http://en.wikipedia.org/wiki/IA-64#cite_note-40") but Sun contests this number.[[42]]("http://en.wikipedia.org/wiki/IA-64#cite_note-Sun1-41") The ISA also supports [Gelato]("http://en.wikipedia.org/wiki/Gelato_Federation"), an Itanium HPC user group and developer community that ports and supports [open source]("http://en.wikipedia.org/wiki/Open_source") software for Itanium.[[43]]("http://en.wikipedia.org/wiki/IA-64#cite_note-42")
 The software requirements for Itanium were criticized by [Donald Knuth]("http://en.wikipedia.org/wiki/Donald_Knuth") who said: "...The Itanium approach ... was supposed to be so terrific&#8212;until it turned out that the wished-for compilers were basically impossible to write" [[1]]("http://www.informit.com/articles/article.aspx?p=1193856")


---

### Post by insane_alien on 2008-10-12
AMD64 is the one you go for. it will run on EM64T as well and you are unlikely to get an itanium as they are pretty damn pricey and usually found in the enterprise server market, infact, i've never actually seen a place that sells them.

---

### Post by felker2 on 2008-10-12
Mainstream desktops and laptops that are for sale now, have x86-64 compatible processors. So no risk there.

See full list on [http://en.wikipedia.org/wiki/X86-64]("http://en.wikipedia.org/wiki/X86-64")


Stay away from:
VIA-processors
Intel Atom processors
Intel Itanium processors

You won't find these processors in the mainstream channel of desktop and normal laptops. Do not buy a EEE-PC-like nettop; they have non-64-bit processors

---

### Post by Yellow Pasque on 2008-10-12
Any new AMD CPU that you find will support amd64, as will Intel's Core 2 series.

> I will buy desktop from official IBM supplier so it will be Lenovo desktop with Intel processor.
All of Lenovo's "ThinkCentre" and "IdeaCentre" desktop models have amd64/emt64-compatible CPU's.

---

### Post by jespdj on 2008-10-13
An Intel Itanium processor is not something that you can buy in a normal shop; it's only used in big servers. As far as I know there is no version of Ubuntu that runs on Intel Itanium processors.

The "normal" kind of 64-bit is called AMD64, EM64T or [Intel 64](http://en.wikipedia.org/wiki/EM64T#Intel_64) (that's the new name for EM64T).

Almost all AMD and Intel processors for regular desktop computers from the past three years or so are 64-bit capable.

---

### Post by felker2 on 2008-10-13
> **jespdj said:**
> 
Almost all AMD and Intel processors for regular desktop computers from the past three years or so are 64-bit capable.

Past *three* years? Be careful there: The 32-bit Core Duo (not the Core 2 Duo) has been *introduced* until the summer of 2006, and thus sold during 2006 and probably 2007.

I would say: at this moment you can be save to find only 64-bit CPU's in maintream PCs in mainstream shops (excluding the mini-laptops / EEE-PC-lookalikes)

---

### Post by abcuser on 2008-10-13
Hi,
I have decided to buy [Lenovo ThinkCentre M57p Tower](http://www5.pc.ibm.com/europe/products.nsf/$wwwPartNumLookup/_VVCBvxx?OpenDocument) which has according to specification [Intel Core 2 Duo E8400 Processor](http://processorfinder.intel.com/details.aspx?sSpec=SLAPL) and detailed specifications says Supported Features: [Intel EM64T](http://developer.intel.com/technology/intel64/index.htm), so this means support for x86-64/Intel64/AMD64 instructions. It also supports [Intel Virtualization Technology](http://www.intel.com/technology/virtualization/) so called VT-x which must have PC to run 64-bit applications under VirtualBox 2.0.

Thank you very much for help,
Abcuser

---

### Post by jespdj on 2008-10-13
> **felker2 said:**
> Past *three* years? Be careful there: The 32-bit Core Duo (not the Core 2 Duo) has been *introduced* until the summer of 2006, and thus sold during 2006 and probably 2007.
That's why I said *almost*. :)

Anyway, if you buy a new desktop computer today, then there would most likely be a 64-bit capable processor in it.

---

### Post by Robstarusa on 2008-10-13
Be _VERY_ careful buying a 64-bit processor.  Anything modern will be 64-bit compatible, HOWEVER most low end intel processors do NOT have hardware virtualization.  I would not buy something without hardware virtualization since Virtualization is the future!

---

### Post by abcuser on 2008-10-13
> **abcuser said:**
> It also supports [Intel Virtualization Technology](http://www.intel.com/technology/virtualization/) so called VT-x
Hi,
it looks like I have written little mistake. VT-x is just one part of VT according to [Wikipedia](http://en.wikipedia.org/wiki/Intel_vt):
*"Intel Virtualization Technology, or Intel VT, is a set of technologies from Intel for virtualization [...] Intel VT is composed of Virtualization Technology for IA-32 (VT-x), Virtualization Technology for IA-64 (VT-i), Virtualization Technology for Directed I/O (VT-d), and Virtualization Technology for Connectivity (VT-c)."*
Regards,
Abcuser

---

### Post by snowstorm167 on 2008-10-15
I am running a p4 ht with hrdy 64 bit server os

it is also running as a dual core with 512 ram and 1.5 gig virtual

---

### Post by jespdj on 2008-10-16
> **Robstarusa said:**
> Be _VERY_ careful buying a 64-bit processor.  Anything modern will be 64-bit compatible, HOWEVER most low end intel processors do NOT have hardware virtualization.  I would not buy something without hardware virtualization since Virtualization is the future!
That's probably a good idea, but you do not absolutely need hardware virtualization support to be able to run operating systems in virtual machines. VirtualBox also works if your processor does not have hardware virtualization support.

---

### Post by abcuser on 2008-10-17
> **jespdj said:**
> VirtualBox also works if your processor does not have hardware virtualization support.
True only for 32-bit guest systems.

From VirtualBox v2.0.2 manual:
[i]Enabling hardware virtualization is required only in two scenarios:
- for certain rare guest operating systems like OS/2 that make use of very esoteric
processor instructions that are not supported with our software virtualization
and
- if you want to run 64-bit guest operating systems (a feature added with
VirtualBox 2.0), since most 64-bit CPUs ship with hardware virtualization anyway.
The exceptions to this rule are e.g. older Intel Celeron and AMD Opteron
CPUs.[/i]

---

