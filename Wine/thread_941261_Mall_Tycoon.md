---
title: "Mall Tycoon"
date: 2008-10-07
forum: Wine
---

### Post by RealG187 on 2008-10-07
I bought Mall Tycoon a long time ago and wanna try it now, but since then I switched to Ubuntu.

[here]("http://paste.ubuntu.com/55166/") is the text I get when I try it with Wine...

---

### Post by david_kt on 2008-10-13
> **RealG187 said:**
> preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report


The above error could be fixed by doing as following:

```
sudo sysctl -w vm.mmap_min_addr=0
```

After you run the above command, try to launch your program again and see what happen.

DK

---

### Post by RealG187 on 2008-10-14
What does that command do?

So typing one command could make it work?

Anywyas, my laptop is in repiar and I am stuck (again) using my Windoze machine...

---

### Post by david_kt on 2008-10-14
> **RealG187 said:**
> What does that command do?

So typing one command could make it work?

Anywyas, my laptop is in repiar and I am stuck (again) using my Windoze machine...
Short answer:

To open range 00000000-60000000 address.

Long answer:

mmap_min_addr sysctl was added to provide the ability to prevent processes from mapping the NULL address, thus preventing the exploitation of a kind of possibly yet undiscovered kernel bugs (NULL dereferences) to escalate privileges. For ubuntu, it was 
```

vm.mmap_min_addr = 65536
```

That is the reason wine to reserve range 00000000-60000000, as it violates system security.

By issuing below command:

```
sudo sysctl -w vm.mmap_min_addr=0
```

you will override 65536 setting to become zero. As such, it slightly reduce the system security so as to allow wine to reserve range 00000000-60000000.

This will also fix below error:
```
err:dosmem:setup_dos_mem Cannot use _first megabyte for DOS address space_, please report
```

and hopefully your program could run smoothly if the above two errors are corrected.

DK

---

### Post by RealG187 on 2008-10-23
So it makes wine more compatible but at the same time makes it more compatible.

Then in that case, Winodws is self is the most compatible but the most vulnerable lol!

---

### Post by RealG187 on 2009-01-08
I am running Mall Tycoon and the display is garbled... (see attached screenshot)

[img]http://operation420.net/tmp/Screenshot.png[/img]

I had to upload it externally cuz I can't attach it (I think something is up with Ubuntu's server)

---

### Post by RealG187 on 2009-01-08
Double post made by connection lag (I keep getting 503 errors on this site)

---

