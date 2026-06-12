---
title: "Rhythmbox / Totem and gvfsd segfaults?"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by gaijinak on 2008-06-22
Hello, and thanks in advance for your time!

I recently upgraded to Hardy over a working Gutsy install.  The install was effectively painless, however, the system crashed during the night after I locked the screen and went to bed.  Since the crash any time I attempt to use Rhythmbox or Totem to view media the program hangs and drives the one of my CPUs to 100% utilization.  (Rhythmbox worked prior to the crash, Totem was untested.)

I've attempted to verify the integrity of the system using 'debsums -a' and less those small number of packages that don't contain md5sums, things seem to check out.  I've also attempted to reinstall gvfsd, Rhythmbox, and Totem as well as the dependencies that seemed pertinient, and there has been no change.

Other media players work, such Exaile, VLC and hovering over an audio file in Nautilus, so I'm reasonably certain it's not an audio issue.

The logs show are filled with messages similar to the following:

```
Jun 22 10:36:37 obsidian kernel: [96248.641815] gnome-vfs-daemo[2381]: segfault at 0 rip 7fb3eeea9ae2 rsp 7ffff87e8938 error 4

```
With the 'rip' and 'rsp' addresses varying.

An strace of totem shows a repeated loop of attempts to poll a resource (gvfsd I think) that continue until the program is stopped:
```

poll([{fd=15, events=POLLIN, revents=POLLIN}], 1, 25000) = 1
read(15, "l\4\1\0013\0\0\0U\1\0\0\211\0\0\0\1\1o\0\25\0\0\0/org/"..., 2048) = 295
read(15, 0x89de20, 2048)                = -1 EAGAIN (Resource temporarily unavailable)
writev(15, [{"l\1\0\1\0\0\0\0\225\0\0\0\212\0\0\0\1\1o\0\32\0\0\0/or"..., 160}, {"", 0}], 2) = 160
poll([{fd=15, events=POLLIN, revents=POLLIN}], 1, 25000) = 1
read(15, "l\4\1\0011\0\0\0W\1\0\0\211\0\0\0\1\1o\0\25\0\0\0/org/"..., 2048) = 209
read(15, 0x89de20, 2048)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=15, events=POLLIN, revents=POLLIN}], 1, 24976) = 1
read(15, "l\3\1\1=\0\0\0X\1\0\0o\0\0\0\5\1u\0\225\0\0\0\4\1s\0\""..., 2048) = 189
read(15, 0x89de20, 2048)                = -1 EAGAIN (Resource temporarily unavailable)
writev(15, [{"l\1\0\1\0\0\0\0\226\0\0\0\213\0\0\0\1\1o\0\32\0\0\0/or"..., 160}, {"", 0}], 2) = 160
poll([{fd=15, events=POLLIN, revents=POLLIN}], 1, 25000) = 1
read(15, "l\4\1\0013\0\0\0Y\1\0\0\211\0\0\0\1\1o\0\25\0\0\0/org/"..., 2048) = 211
read(15, 0x89de20, 2048)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=15, events=POLLIN, revents=POLLIN}], 1, 24990) = 1
read(15, "l\4\1\0011\0\0\0Z\1\0\0\211\0\0\0\1\1o\0\25\0\0\0/org/"..., 2048) = 398
read(15, 0x89de20, 2048)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, "\26\0\336\2\3\0\340\3\3\0\340\3 \0\300\3{\2^\1\212\2\364"..., 4096) = 160
read(3, 0x686244, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=15, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}], 9, 0) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=15, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}], 9, 0) = 0
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"(\0\4\0\3\0\340\3\246\1\0\0\0\0\0\0", 16}], 1) = 16
select(4, [3], [], NULL, NULL)          = 1 (in [3])
read(3, "\241 \336\2\3\0\340\3\372\0\0\0\370\0\0\0[\251\257\5\0"..., 4096) = 64
read(3, 0x686244, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=15, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}], 9, 0) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=15, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}], 9, 0) = 0
writev(15, [{"l\1\0\1$\0\0\0\227\0\0\0\210\0\0\0\1\1o\0\25\0\0\0/org"..., 152}, {"\31\0\0\0org.gnome.GnomeVFS.Daemon\0\0\0"..., 36}], 2) = 188

```
Any thoughts?

Thanks again!

---

### Post by pixel :-) on 2008-06-26
gnome-vfs-daemo

that thing is in user space.I think that something in you home got corrupted.Try a new user with clean home.

---

### Post by gaijinak on 2008-07-03
Pixel -

Actually I did do that - same result.  But, in the period since I've installed a fair number of updates, and had to fsck the filesystem again (reached maximum boot count) and the problem has cleared.  No idea why, but everything is functional again.

Thanks for the reply!

R.

---

