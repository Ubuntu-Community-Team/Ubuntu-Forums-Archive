---
title: "question regarding compatibility"
date: 2008-08-09
forum: x86 64-bit Users
---

### Post by stevo24 on 2008-08-09
question regarding compatibility

i have a intel core 2 duo processor and 8gb of memory.  I want to create virtual machines and have been advised to run vmware on linux.  basically for training purposes.

Can anyone recommend what version of linux to go with, rememeber im new to linux.

Thanks in advance.

---

### Post by tvtech on 2008-08-09
go with whatever version you want it doesn't matter make sure your VM ware software supports it

personally I reccommend xensource for virtualization it doesn't do resource sharing and thus removes a lot of complications and lag that many other virtual boxes have. it does specified resource allocation for your primary and any virtualized operating systems. I personally like ubuntu 8.04 myself it's the newest long term release and works very well in almost all aspects.

---

### Post by stevo24 on 2008-08-09
will the amd64 release work even tho i dont have a amd processor

---

### Post by tamoneya on 2008-08-09
yes it will work.  And it is also the one you should use since it will be able to address all 8 GB of RAM.  The i386 version will not be able to.

---

### Post by stevo24 on 2008-08-09
and whats the difference between desktop and server edition???

---

### Post by dfreer on 2008-08-09
One thing you will want to find out is whether your Intel processor supports the Virtualization Technology. 

I have two Intel processors, one bought about 2 years ago (an Intel Core 2 Duo T7200 @ 2.0 Ghz) in my laptop, and one I bought about 1 year ago (an Intel Core 2 Duo E4500 @ 2.2 Ghz) for my server. I had planned on running a 64-bit version of linux with the E4500 and have 32-bit and 64-bit virtual machines in vmware.

Unfortunately, I found out my newer E4500 did not support VT, and so I am unable to run 64-bit machines AT ALL in vmware. I can do it on my laptop, but it's a friggin laptop :(

Beyond that, I would run the 64-bit version of debian or ubuntu. Apt-get is great, and I've had experience running VMWare on both OS and didn't have any real problems other than mentioned above. Note that if you plan on running the virtual machines remotely you will also want to install the remote console (I think that was what it was called).

EDIT: Desktop isn't free :D  Beyond that, it's probably best to read their features page:
[http://www.vmware.com/products/server/features.html](http://www.vmware.com/products/server/features.html)
[http://www.vmware.com/products/ws/new.html](http://www.vmware.com/products/ws/new.html)

---

### Post by tamoneya on 2008-08-09
> **stevo24 said:**
> and whats the difference between desktop and server edition???

The desktop version of ubuntu includes a GUI while the server edition is just CLI.

---

