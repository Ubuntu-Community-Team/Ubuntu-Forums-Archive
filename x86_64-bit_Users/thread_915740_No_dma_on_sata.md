---
title: "No dma on sata?"
date: 2008-09-10
forum: x86 64-bit Users
---

### Post by jernejk on 2008-09-10
Hi,

I've got a server with Intel S5000Psl motherboard and 6 SATA drives (not sure about brand, they are Seagates or WDs).

However, disk access is quite slow. Hdparm returns:
/dev/sda:
 IO_support = 0 (default)
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly = 0 (off)
 readahead = 256 (on)
 geometry = 25665/255/63, sectors = 1465149168, start = 0

Setting DMA also fails:
/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

Any ideas?

---

### Post by chadeldridge on 2008-09-11
Also having the exact same issue.  It looks like many other are as well.

---

### Post by insane_alien on 2008-09-11
hdparm doesn't fully support SATA yet IIRC.

---

