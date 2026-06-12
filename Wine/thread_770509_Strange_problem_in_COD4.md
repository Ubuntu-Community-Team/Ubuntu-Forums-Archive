---
title: "Strange problem in COD4"
date: 2008-04-27
forum: Wine
---

### Post by andrebrait on 2008-04-27
I'm getting this, in the parte when you have to to choose the difficulty level.

> err:seh:setup_exception_record stack overflow 816 bytes in thread 001c eip f7ca9be8 esp 7cad5000 stack 0x7cad4000-0x7cad5000-0x7cbd5000

err:ntdll:RtlpWaitForCriticalSection section 0x7eba1e7c "d3d9_main.c: d3d9_cs" wait timed out in thread 0009, blocked by 001c, retrying (60 sec)


I followed 2 tutorial, in one of them I had to install DirectX and set some libraries as native, others as builtin. In the other I just had to copy the d3dx9_24~35 dlls to the system32 folder. Both of them freeze here.

Any idea?:confused:

---

### Post by schtufbox on 2008-04-27
Which version of wine and linux kernel do you have?

---

### Post by andrebrait on 2008-04-27
0.9.60

8.04 x86-64

---

### Post by andrebrait on 2008-04-27
0.9.60

8.04 x86-64

---

