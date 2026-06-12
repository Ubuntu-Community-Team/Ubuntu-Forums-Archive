---
title: "Celeron M 540"
date: 2007-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by speediii on 2007-11-28
Hi

I've just ordered a new (cheap) laptop - 

Intel 956GM chipset
Intel Celeron M 540 1,8Ghz CPU

I am wondering whether I should install Ubuntu 32 or 64 bit version from the download site?

[http://processorfinder.intel.com/details.aspx?sspec=sla2f](http://processorfinder.intel.com/details.aspx?sspec=sla2f)

The above says it's a 64bit CPU, but the Support team from the site I ordered the laptop from say "The Celeron processor is only 32-bit, so installing the 32-bit version would be best."

They say if you install 64 bit things like Flash & Java won't work?

Sounds like BS to me, it's just to install the 64bit Java versions etc...

I understand very little about CPU's - I know I can install 32 on a 64 bit CPU, but what's the point if it does support 64?

Can someone tell me if this really is 64bit and if there are any implications I need to consider?

Please help!

Lee

---

### Post by Sef on 2007-11-28
> 2 Intel® EM64T requires a computer system with a processor, chipset, BIOS, operating system, device drivers and applications enabled for Intel EM64T. Processor will not operate (including 32-bit operation) without an Intel EM64T-enabled BIOS. Performance will vary depending on your hardware and software configurations. See [http://www.intel.com/info/em64t](http://www.intel.com/info/em64t) for more information including details on which processors support Intel® EM64T or consult with your system vendor for more information.

Likely there is something not included, so it can't do 64-bit operations.  You can ask Dell why it can't do 64-bit operations.

---

### Post by John.Michael.Kane on 2007-11-28
> **speediii said:**
> Hi

I've just ordered a new (cheap) laptop - 

Intel 956GM chipset
Intel Celeron M 540 1,8Ghz CPU

I am wondering whether I should install Ubuntu 32 or 64 bit version from the download site?

[http://processorfinder.intel.com/details.aspx?sspec=sla2f](http://processorfinder.intel.com/details.aspx?sspec=sla2f)

The above says it's a 64bit CPU, but the Support team from the site I ordered the laptop from say "The Celeron processor is only 32-bit, so installing the 32-bit version would be best."

Going on the cpu info only, and without knowing where the machine was purchased, As well as it's full specs. It would appear that cpu has the instruction set to run a 64bit OS according to this [Processor 540 Features]("http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/mobile/processors/celeron540/feature/index.htm"), however. It can't be said the machine is fully supported,If you can please post a link to site where you purchased this machine or a direct link to it's full spec's.

> **speediii said:**
> They say if you install 64 bit things like Flash & Java won't work?

Sounds like BS to me, it's just to install the 64bit Java versions etc...
Under most circumstances installing flash on 64bit Ubuntu is done through synaptic,however. some users have reported having issues installing flash using synaptic on the latest version of Ubuntu.Regarding java some have been able to use icedtea (which some say works with some sites).Some have had to resort to installing 32bit firefox for java use. You would have to test iecedtea, and see if it works with the java sites you visit.

> **speediii said:**
> I understand very little about CPU's - I know I can install 32 on a 64 bit CPU, but what's the point if it does support 64?

Can someone tell me if this really is 64bit and if there are any implications I need to consider?

Please help!

Lee

As said without knowing full spec's on the system, It would be hard to give a definitive answer. 

Hope this helps.

---

### Post by speediii on 2007-11-28
Sorry, thought the chipset might be ok:

[http://uk.zepto.com/Shop/Config.aspx?configurationid=348&notebookid=673](http://uk.zepto.com/Shop/Config.aspx?configurationid=348&notebookid=673)

and

[http://www.zepto.dk/Files/15_3215W_datasheet_1.0_ENG.pdf](http://www.zepto.dk/Files/15_3215W_datasheet_1.0_ENG.pdf)

It's a cheap, decent machine.  - My feeling so far is install Ubuntu 32bit and avoid problems?

Thanks again

Lee

---

### Post by mellowd on 2007-11-28
go with 32bit and be happy

---

### Post by speediii on 2007-11-28
Will do! Thanks :-]

---

### Post by John.Michael.Kane on 2007-11-28
The processor included with that machine is 64bit [http://uk.zepto.com/PageControls/Product.aspx?componentid=660](http://uk.zepto.com/PageControls/Product.aspx?componentid=660) I'm also inclined to believe that machines parts should work with 64bit Ubuntu should you go that route.

Why they would tell you it's not is beyond me. What they might have meant is the machine will come with a 32bit OS installed,however. this is only a guess on my part.

---

