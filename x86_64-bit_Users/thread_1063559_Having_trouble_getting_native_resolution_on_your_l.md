---
title: "Having trouble getting native resolution on your laptop?"
date: 2009-02-08
forum: x86 64-bit Users
---

### Post by pelle on 2009-02-08
Here is an ugly patch to get an 1920x1200 framebuffer
using kernel parameters "video=vesafb:ypan vga=0x376"
on the nice 17"-screen of the Fujitsu Siemens Xi2550

--------------------------------------------------------
1a2,5
>  * vesafb.c from Linux kernel 2.6.28.3
>  * patched for Fujitsu Siemens Xi 2550 (Radeon HD2700)
>  * by Per Andersson 090208 / [email]Professor.Frink@telia.com[/email]
>  *
59a64
> static void  *mmioptr = 0;
129a135,140
>         if (mmioptr) {
>            * (short unsigned int *) (mmioptr + 0x6120) = 1920;
>            * (short unsigned int *) (mmioptr + 0x6134) = 1920;
>            * (short unsigned int *) (mmioptr + 0x6586) = 1920;
>            * (unsigned char *) (mmioptr + 0x6590) = 0;
>            }
205a217,222
> static int vesafb_remove(struct platform_device *dev)
> {
> if (mmioptr) iounmap(mmioptr);
> return 0;
> }
>
220,222c237,239
<       vesafb_defined.xres = screen_info.lfb_width;
<       vesafb_defined.yres = screen_info.lfb_height;
<       vesafb_fix.line_length = screen_info.lfb_linelength;
---
>       vesafb_defined.xres = screen_info.lfb_width = 1920;
>       vesafb_defined.yres = screen_info.lfb_height = 1200;
>       vesafb_fix.line_length = screen_info.lfb_linelength = screen_info.lfb_width * vesafb_defined.bits_per_pixel / 8;
275a293,306
>         if (!request_mem_region(0xcfef0000, 0x10000, "vesaio")) { // Pelle Andersson
>            printk(KERN_ERR "vesafb: cannot reserve io memory at 0x%x\n", 0xcfef0000);
>            }
>         mmioptr = ioremap(0xcfef0000, 0x10000);
>         if (!mmioptr) {
>            printk(KERN_ERR  "vesafb: abort, cannot ioremap video memory 0x%x @ 0x%x\n", 0x10000, 0xcfef0000);
>            err = -EIO;
>            goto err;
>            }
>         * (short unsigned int *) (mmioptr + 0x6120) = 1920;
>         * (short unsigned int *) (mmioptr + 0x6134) = 1920;
>         * (short unsigned int *) (mmioptr + 0x6586) = 1920;
>         * (unsigned char *) (mmioptr + 0x6590) = 0;
>         printk(KERN_INFO  "vesafb: ioremap ioports 0x%x @ 0x%x to %p\n", 0x10000, 0xcfef0000, mmioptr);
441a473
>         .remove = vesafb_remove,
--------------------------------------------------------

---

