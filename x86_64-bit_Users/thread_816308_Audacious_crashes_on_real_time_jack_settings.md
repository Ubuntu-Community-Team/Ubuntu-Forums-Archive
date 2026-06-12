---
title: "Audacious crashes on real time jack settings"
date: 2008-06-02
forum: x86 64-bit Users
---

### Post by Kapitan on 2008-06-02
Hi all!!

I think i have a bug in audacious.
When i turn on the jack real time options
(and audacious has the jack plugin),
it crashes...

Is this the right place (i've ubuntu studio
64 bit).

I report the error:
```

jack_get_output_time:returning 13679 milliseconds
jack_free:free space of 4616 bytes
jack_write:starting length of 512
jack_write:writing 512 bytes
jack_write:finished
jack_get_written_time:returning 13848 milliseconds
jack_get_output_time:returning 13690 milliseconds

(process:6561): GLib-ERROR (recursed) **: /build/buildd/glib2.0-2.16.3/glib/gmem.c:175: failed to allocate 4 bytes
aborting...
Aborted

```

---

