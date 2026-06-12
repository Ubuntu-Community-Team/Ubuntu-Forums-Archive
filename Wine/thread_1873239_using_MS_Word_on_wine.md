---
title: "using MS Word on wine"
date: 2011-11-01
forum: Wine
---

### Post by kartik1807 on 2011-11-01
Hi guys,
I was wondering how to use MS Word(2011) in wine.  I have it installed already. but when i run wine says "IOPL not enabled".I'm using Ubuntu 11.04
:confused:
:guitar:

---

### Post by beew on 2011-11-01
No, it doesn't work. And why would you want that?

---

### Post by Elfy on 2011-11-01
Thread moved to Wine.

---

### Post by anaconda on 2011-11-01
> **beew said:**
> No, it doesn't work. And why would you want that?

Yeah it works. I am using word 2007, and haven't noticed anything unusual yet&#803;

To OP. Cant help, because I never had that kind of a problem. Which version are you running?

---

### Post by vasa1 on 2011-11-01
> **beew said:**
> No, it doesn't work. And why would you want that?

+1.
Seriously, why do you want to use it? If you have a good reason, do share!

---

### Post by VeeDubb on 2011-11-01
> **beew said:**
> No, it doesn't work. And why would you want that?

> **vasa1 said:**
> +1.
Seriously, why do you want to use it? If you have a good reason, do share!

How about because there isn't a single open source office suite that fully supports the features in Word 2011?

If you have a job at a company that uses Office (like most companies) you will frequently find that things like forms do not function correctly.

And don't even get me started on VBA.  I'm responsible for creating and maintaining several highly complex word and excel files that use a huge amount of VBA.  While there are open source office suites with 'some' support for basic, or their own alternative implementations, none of them consistently function the way I need them to.

There are MANY reasons to use one office suite over another.  While Libre Office is lighter, faster and more secure; it is missing mountains of functionality that advanced users need.  Modern office software isn't just for writing letters.

Office 2011 is now the only reason I every fire up virtualbox.  If there was a native Linux port of Office, or if it was even usable in wine, I would be thrilled.  Sadly, only Word and Excel work from 2k7, and 2011 doesn't work at all for most people, although a few have been able to get Word 2011 to 'mostly' work with a lot a tweaking.

---

### Post by vasa1 on 2011-11-01
> **VeeDubb said:**
> How about because there isn't a single open source office suite that fully supports the features in Word 2011?
...

That's actually reason _not_ to use Word 2011.

---

### Post by beew on 2011-11-01
> **anaconda said:**
> Yeah it works. I am using word 2007, and haven't noticed anything unusual yet&#803;

To OP. Cant help, because I never had that kind of a problem. Which version are you running?

Yeah 2007,  not 2011. See WINEHQ's list.

---

### Post by beew on 2011-11-01
> 
Originally Posted by **VeeDubb**
How about because there isn't a single open source office suite that fully supports the features in Word 2011?And neither do older versions of MSOffice (2007, which is most commonly used)

Nobody uses those feature anyway, in the real world most people are still using 2007 (or 2003). MSO2010 is barely compatible with something we use at work, we are considering downgrading Office if this doesn't get fixed soon.

Why would you encourage MS to constantly breaking compatibility just to maintain a monopoly by paying for it latest offer?

BTW we as a rule send out documents and excel sheets in .doc and .xls rather than .docx and .xlsx. Anyone can open the former but not necessarily the latter (well some people in large organizations are still using Office 2003 and to install the compatibility patch may need administrative clearance that could take a few days in such workplaces)

---

### Post by Mark Phelps on 2011-11-01
> **kartik1807 said:**
> Hi guys,
I was wondering how to use MS Word(2011) in wine.

First of all, MS Word 2011 only exists for the Mac.

Second, most of the Office 2010 components don't work in Wine.  It took CodeWeavers three years to get Office 2007 working -- and by then, Office 2010 was out.  So, don't hold your breath for getting Office 2010 working.

---

### Post by kartik1807 on 2011-11-02
> **beew said:**
> No, it doesn't work. And why would you want that?
BEcause LIBRE office considers mw watermarks IMAGES!

---

### Post by kartik1807 on 2011-11-02
> **kartik1807 said:**
> BEcause LIBRE office considers mw watermarks IMAGES! MY reson for trying to use MSO2010 on wine 2.2

---

