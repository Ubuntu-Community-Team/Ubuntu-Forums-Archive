---
title: "Is Ubuntu 64-bit only for AMD processor?"
date: 2009-02-24
forum: x86 64-bit Users
---

### Post by Mazen on 2009-02-24
Hi everyone,
My laptop has an Intel Core2 Duo processor, which is a 64-bit processor, so i thought i'd install Ubuntu64, i know it's for 64-bit architectures but the name states "AMD" so i thought i'd seek clarification!
And is there any compatibility issues or anything of the sort?
Thanks,

---

### Post by kelvin spratt on 2009-02-24
its fine

---

### Post by Faolan on 2009-02-24
If it's a 64bit processor it should be fine. I've installed the 64bit version on both Intel and AMD platforms with no issues so far.

---

### Post by philinux on 2009-02-24
I wish they'd fix the naming of these iso's. If I has a quid for every time this comes up......:lolflag:

---

### Post by Thelasko on 2009-02-24
> **philinux said:**
> I wish they'd fix the naming of these iso's. If I has a quid for every time this comes up......:lolflag:

Did you vote to fix it on [Brainstorm]("http://brainstorm.ubuntu.com/idea/17720/")?

---

### Post by deltaiscain on 2009-02-25
> **philinux said:**
> I wish they'd fix the naming of these iso's. If I has a quid for every time this comes up......:lolflag:

:lolflag: i had he same issue. Was scared all the files were for a AMD processor, luckily they worked just fine. ;)

---

### Post by 3Miro on 2009-02-25
I have an AMD desktop and INtel Core 2 Duo Laptop, both run on the 64 bit Linux version. Amd64 is just a name.

---

### Post by Yellow Pasque on 2009-02-25
> **philinux said:**
> I wish they'd fix the naming of these iso's.

If we want to be technical about it, the x86_64 architecture was invented by AMD and they called it AMD64. So you're suggesting that Debian/Ubuntu change the naming and not "fix" it. I suspect that changing the naming would probably cause issues with backwards compatibility (packaging scripts breaking and such).

IMO, a better idea would be to put a little note on the download page explaining that the amd64 iso is also used on intel processors with "EM64T".

---

### Post by stchman on 2009-02-25
> **Mazen said:**
> Hi everyone,
My laptop has an Intel Core2 Duo processor, which is a 64-bit processor, so i thought i'd install Ubuntu64, i know it's for 64-bit architectures but the name states "AMD" so i thought i'd seek clarification!
And is there any compatibility issues or anything of the sort?
Thanks,

I run 64 bit Hardy on the following:

Athlon 64
Core 2 Duo
Core 2 Quad

On the Ubuntu homepage when downloading the OS it asks you if you want the 32 or 64 bit version.  It says nothing about having to have AMD to use it.

---

### Post by bvanaerde on 2009-02-27
> **stchman said:**
> On the Ubuntu homepage when downloading the OS it asks you if you want the 32 or 64 bit version.  It says nothing about having to have AMD to use it.

It does, right after the download starts:
> Your Download Should Begin Shortly
If your download does not start in approximately 15 seconds, you can click here to launch the download.

Download URL: [http://ftp.belnet.be/mirror/ubuntu.com/releases/intrepid/ubuntu-8.10-desktop-amd64.iso](http://ftp.belnet.be/mirror/ubuntu.com/releases/intrepid/ubuntu-8.10-desktop-amd64.iso)
Ubuntu Edition: Ubuntu 8.10 desktop
**Computer Platform: amd64**
Download Location: [http://ftp.belnet.be/mirror/ubuntu.com/releases/](http://ftp.belnet.be/mirror/ubuntu.com/releases/)

I can see why it is a bit confusing...

---

### Post by Sockerdrickan on 2009-02-27
yeah but amd64 is not a processor

---

### Post by bvanaerde on 2009-02-27
True. But I hope you see it can be confusing for some people.
Anyway, I just saw that there is a pretty good description on [the download page of Jaunty Jackalope Alpha 5]("http://cdimage.ubuntu.com/releases/jaunty/alpha-5/"):
> Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead.


---

