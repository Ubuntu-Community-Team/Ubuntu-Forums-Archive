---
title: "[SOLVED] Pan will not launch"
date: 2008-08-21
forum: x86 64-bit Users
---

### Post by David D. on 2008-08-21
Today Pan will not launch.  It was working yesterday.  I tried an uninstall and reinstall, but no luck.  If I try to launch in terminal I get "pan: parts.cc:244: void pan::Parts::set_parts(const pan::PartBatch&): Assertion `pch == part_mid_buf + part_mid_buf_len' failed.
Aborted"

I am using an HP dv6000 laptop.

---

### Post by Ehtetur on 2008-08-22
David - Try removing your .pan2 configuration folder and then starting pan...

Rather than delete .pan2 you may want to rename it:
> mv ~/.pan2 ~/_pan2

---

