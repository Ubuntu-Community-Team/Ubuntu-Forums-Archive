---
title: "libuuid.so.1 missing"
date: 2008-04-28
forum: x86 64-bit Users
---

### Post by amorangi on 2008-04-28
I'm trying to migrate a VMware VM to a vBox one using vditool. However ldd vditool lists 
```
linux-gate.so.1 =>  (0xffffe000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7fa8000)
	[COLOR="Red"]libuuid.so.1 => not found[/COLOR]
	librt.so.1 => /lib32/librt.so.1 (0xf7f9e000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7f9a000)
	VBoxDD.so => not found
	VBoxRT.so => not found
	libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0xf7ee0000)
	libm.so.6 => /lib32/libm.so.6 (0xf7eba000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7eaf000)
	libc.so.6 => /lib32/libc.so.6 (0xf7d60000)
	/lib/ld-linux.so.2 (0xf7fd6000)

```

In synaptic it tells me libuuid1 is installed - I suspect I need a 32bit version. What should I do?

---

### Post by chrisccoulson on 2008-04-28
You can download the 32-bit libuuid package, extract it using 'dpkg -x', and copy the .so files in to /lib32.

Assuming you're using Hardy:
```
wget http://fr.archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libuuid1_1.40.8-2ubuntu2_i386.deb
dpkg -x libuuid1_1.40.8-2ubuntu2_i386.deb
sudo cp lib/* /lib32/.
```

Just re-read my instructions, and I feel I should emphasise that **there is NO '/'** in front of 'lib/*' on the last line. If you put one there, you'll end up copying the contents of /lib in to /lib32, which is bad

---

