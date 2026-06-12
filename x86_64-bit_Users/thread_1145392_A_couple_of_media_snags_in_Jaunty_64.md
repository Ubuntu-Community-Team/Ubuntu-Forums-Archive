---
title: "A couple of media snags in Jaunty 64"
date: 2009-05-01
forum: x86 64-bit Users
---

### Post by FokkerCharlie on 2009-05-01
Hello!

This morning, I took the plunge and moved over to 64-bit Jaunty on my Core2Duo laptop.  Actually, it's working very well so far with just a couple of exceptions:

1) I can't play DVDs!

VLC returns:
```

Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///media/cdrom0/VIDEO_TS/'. Check the log for details.
```

Which is probably related to:

```
~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
```

Any ideas on that one?

2) Has anyone got BBC iplayer desktop (via Adobe AIR) working on the 64-bit OS?  It was working fine with 32-bit, but stubbornly refuses to behave now.  When I run the menu command in a terminal I see:

```
$ '/opt'/'BBC iPlayer Desktop'/bin/'BBC iPlayer Desktop'
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
```

And then the prompt returns.  Interstingly, I see the same message when I run 'acroread', but that runs fine, so I'm not sure that this is the problem.  I have tried the YouTube app on AIR, and that works OK.

Any ideas?

Cheers!
Charlie

---

### Post by edm1 on 2009-05-01
Just
> sudo /usr/share/doc/libdvdread4/./install-css.sh


---

### Post by FokkerCharlie on 2009-05-01
Cool!

That worked a treat.

Please will someone come up with a fix for iPlayer desktop that's just as easy?!:popcorn:

Thanks very much for your response
Charlie

---

