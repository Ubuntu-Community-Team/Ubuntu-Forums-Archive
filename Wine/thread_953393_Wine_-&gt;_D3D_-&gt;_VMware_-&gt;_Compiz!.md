---
title: "Wine -&gt; D3D -&gt; VMware -&gt; Compiz!"
date: 2008-10-20
forum: Wine
---

### Post by Fzang on 2008-10-20
Seems pretty advanced but you never know what might be possible...

Recently, VMware workstation for windows/linux just got updated to 6.5 and now supports 3D graphics by D3D! Linux however doesn't use D3D and renders compiz and other desktop effects in openGL

So... I was wondering if you could install D3D through wine and then have compiz use that instead? Probably not possible... I just want compiz in a VM! T_T

---

### Post by Mistrblank on 2008-10-20
The problem is that Compiz is not built on D3D so you've bought nothing.

---

### Post by Thelasko on 2008-10-20
> **Fzang said:**
> So... I was wondering if you could install D3D through wine and then have compiz use that instead? Probably not possible... I just want compiz in a VM! T_T
On the host or the guest?

FYI Wine doesn't interact with the video card directly.  It has libraries that convert video output into OpenGL.

For example, Wine has it's own version of DirectX that outputs 3D graphics in OpenGL.  That's why installing DirectX in Wine breaks 3D graphics support.

---

