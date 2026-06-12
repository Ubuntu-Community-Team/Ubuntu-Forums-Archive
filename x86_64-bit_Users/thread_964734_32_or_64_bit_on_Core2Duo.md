---
title: "32 or 64 bit on Core2Duo"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by aleksandar_te on 2008-10-31
Hello people. Maybe this forum is not the right place for this thread, so admins please move it.

I have notebook with Core2Duo P8400 CPU. Should I install 32 or 64 bit version of K/Ubuntu and what's the difference between them?

Thank You

---

### Post by Laibcoms on 2008-10-31
Personally, 64-bit (K)Ubuntu, make use of your machine's power.

The difference between them, as far as I've read, is with how they handle memory blocks.  Performance-wise, it will depend.

Others have reported that 32-bit is much faster, but that is commonly the case if you run 32-bit apps under 64-bit.

Finally, no worries about apps not being available for 64-bit, since you are using Linux, and Ubuntu at that, most apps you will need are available for 64-bit.  The problem really lies with XP-64bit, because you have to wait for the proprietary developers to compile one :p

That's what I think ^_^

I'm using Ubuntu-64bit, and I actually like it for gaming.

---

### Post by Zack McCool on 2008-10-31
> **aleksandar_te said:**
> Hello people. Maybe this forum is not the right place for this thread, so admins please move it.

I have notebook with Core2Duo P8400 CPU. Should I install 32 or 64 bit version of K/Ubuntu and what's the difference between them?

Thank You

You can install either.  Both will work with your cpu.  The 32 Bit versions typically have better support for flash/java, and if there is not native support for your wireless card, you may find it difficult to get up and running in the 64 Bit version.  Otherwise, though, 64 bit runs a bit faster, and actually uses that shiny new hardware...   ;)

---

### Post by gorgeman on 2008-10-31
New to Linux...I want to load Ubuntu and have downloaded several 8.04.01 disc from different locations. None of which will load as I receive error messages (ex 184.860191, 197.014317 ect). Running E8400 on GA-EP45-DS3R with 4gb ram. I always pick the 64 bit versions for Intel. I must be doing something wrong.
Gorgeman

---

### Post by aleksandar_te on 2008-10-31
One more question: Will 32-bit applications run on 64-bit Ubuntu?

---

### Post by Kilz on 2008-10-31
> **aleksandar_te said:**
> One more question: Will 32-bit applications run on 64-bit Ubuntu?

Yes,
But you will only need it for obscure applications.

---

### Post by stmiller on 2008-11-01
> **aleksandar_te said:**
> One more question: Will 32-bit applications run on 64-bit Ubuntu?

Yes, 32bit apps run as normal. Install all of the ia32* packages and that installs a 32bit compatibility layer of libraries, for lack of a better way to describe it. These packages are something unique to Debian and Ubuntu which is quite nice.

Some 32bit only apps are: skype, google earth, picasa, quake3. These install and work without issue.

If something has trouble starting for any reason, you can start the 32bit app with this:

$ linux32 programname

---

### Post by Orange Luna on 2008-11-05
What about drivers?  I'm installing this on friends laptop and he wants to go 64bit.  Are there concerns about say the nvidia graphics card he installed?  How about an HP printer?

---

### Post by Funnnny on 2008-11-05
I have a Dell Vostro 1400, and I want to install Ubuntu 64bit version too. I heard much about driver compatbility problem when install Windows 64bit, is there any driver or app problem when using ubuntu 64bit ?
P/S: I think the driver and app is fine, I'll install 64bit version on my laptop

---

### Post by steveneddy on 2008-11-05
Go 64 bit.

I feel that if the hardware is 64 bit, run a 64 bit OS if at all possible.

64 bit will handle large amounts of memory better. (2 gigs and over)

64 bit runs smoother on my laptop that 32 bit did.

---

### Post by Sef on 2008-11-06
> How about an HP printer?

HP supports GNU/Linux very well.  It should work out of the box.  To check, click [here]("http://hplipopensource.com/hplip-web/index.html").

---

### Post by lisati on 2008-11-06
I have the 64-bit version of Ubuntu Intrepid on my other laptop, as an alternative to the Vista Home Premium it came with. Other than noticing the previously mentioned flash issues, it seems to work well. I haven't used it long or often enough on that machine to be aware of any other issues, with wireless and sound working "out of the box". 

I currently use 32-bit Xubuntu Intrepid on my day-to-day laptop - the taskbars have disappeared a couple of times, fixed by a brute force fresh install after a backup of data - I think there are other threads dealing with disappearing taskbars/panels.

EDIT: Both my laptops are from the "Toshiba Satellite" stable, one a two-year-old from the A100 range fitted with a Celeron M and 256Mb RAM, the other a newer one from the M200 range with a dual-core CPU and upgraded to 2GB RAM

---

### Post by zuheyr on 2008-11-06
Hi,

8.10 64 bit runs perfectly well on my Dell Inspiron 530S intel 2 core duo.
The only time I had problem was with Skype. I can still install but sound does not work. I did not test it on 32 bit so I cannot tell it is the 64 bit that fails or the Skype...

Regards, Zuheyr

---

### Post by borlosky on 2008-11-15
yea, skype is on of the programs that have issues in 64 bit, there are some work arounds on the forum on how to fix that though.

---

